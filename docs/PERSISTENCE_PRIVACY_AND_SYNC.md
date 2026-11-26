# Persistence, Privacy, and Synchronization Specification

**Status:** Working draft v0.1 — research-informed, not approved for implementation  
**Project:** Language-world  
**Reference boundary:** GoPAL-AI is read-only research. No GoPAL implementation, storage adapter, schema, or pipeline is to be copied into this project.

## 1. Purpose

Language-world is a persistent place, not a disposable session. Learner progress, discoveries, story choices, travel, personal creations, preferences, and meaningful character/world continuity must survive app closure, device changes, network loss, upgrades, and recoverable failures.

Persistence is a product-quality and trust system. It must protect personal information, avoid cross-account leakage, explain what is stored, and let people retrieve, export, correct, and delete their own data.

This document defines requirements and decision boundaries. It does not select a backend, database, identity provider, sync protocol, or storage library.

## 2. Foundational invariants

1. Every learner-owned record belongs to one explicit, stable learner identity.
2. Anonymous/local-first use is a first-class identity state, not a shared demo account.
3. No personal data may be read from or written to a global unscoped key.
4. No fallback user ID may silently merge unrelated people or devices.
5. Public authored content and private learner state have different ownership, storage, cache, and deletion rules.
6. A network failure must not silently convert one learner's data into another learner's data or overwrite newer state.
7. A successful user action must have a defined durable outcome or an honest pending/failed state.
8. Cross-domain side effects must be recoverable and idempotent.
9. Personal memory must have provenance, confidence, purpose, retention, visibility, and deletion semantics.
10. Data export and account deletion must cover local, remote, cached, derived, and media data, subject to clearly disclosed legal/security retention exceptions.
11. Sensitive data collection must be minimized; microphone, camera, location, and third-party AI/voice processing require explicit purpose and consent.
12. Time-dependent state must use explicit clock semantics and must not trust arbitrary device-clock jumps.

## 3. Data ownership classes

Every persisted entity must declare one of these ownership classes.

| Class | Examples | Owner and lifecycle |
|---|---|---|
| Authored world content | World bible, places, resident canon, stories, language content, asset manifests | Product/content team; versioned releases; not deleted with learner account |
| Learner-private state | Progress, preferences, discoveries, personal memory, story choices, creations | One learner; exportable and deletable |
| Shared service state | Public events, service configuration, globally published content | Service/product; access-controlled and versioned |
| Session/transient state | Current camera, temporary dialogue UI, active animation, uncommitted draft | Short-lived; never sole authority for durable progress |
| Derived/cache state | Search indexes, rendered thumbnails, computed recommendations, downloaded bundles | Rebuildable; must preserve source ownership and deletion propagation |
| Operational/security records | Abuse prevention, diagnostics, audit/security logs | Restricted purpose, short documented retention, not character memory |

A record may reference several classes but must never blur their ownership. A learner's discovery of a public story is learner-private state; the story itself remains authored content.

## 4. Identity and learner scope

### 4.1 Identity lifecycle

Support these explicit states:

- **Uninitialized:** no learner profile exists.
- **Local anonymous learner:** a cryptographically random, persistent local learner ID is created on-device.
- **Authenticated learner:** a verified account identity is bound to the learner profile.
- **Account recovery / migration:** a controlled process reconciles local and remote records.
- **Signed out:** account credentials are removed from active session; private local data is either retained in a clearly isolated local profile or removed according to the user's choice and policy.
- **Deletion pending / deleted:** access is restricted immediately while deletion workflows complete and are auditable.

The local anonymous ID must be generated securely, persisted in protected app storage where available, and never be a hard-coded constant, email-derived ID, device-wide shared ID, or placeholder fallback.

### 4.2 Scope every personal record

All learner-owned rows, documents, blobs, local keys, event envelopes, caches, and queued mutations must carry or be cryptographically/structurally bound to a learner ID. Enforce ownership in both application logic and backend authorization. A child record must inherit and validate the owner's scope through its parent relationship.

Local key namespaces must include the learner identity and schema namespace, for example:

    lw:v1:learner:<opaque-learner-id>:<domain>:<record-key>

This is an illustrative naming convention, not a required storage technology. Never put email, display name, access token, or other direct identifier in a key.

Switching accounts must switch the entire data context atomically. No screen, cache, search result, memory retrieval, notification, or queued write may continue using the previous learner's scope.

### 4.3 Anonymous-to-account migration

Before linking an account:

1. Explain what local progress and creations will be associated with the account.
2. Authenticate and verify the destination account.
3. Inventory local records and media by type, owner, schema version, and mutation status.
4. Detect collisions and duplicate semantic events using stable IDs and provenance.
5. Present meaningful conflicts in understandable language; do not silently choose a winner for irreversible story choices or user creations.
6. Transfer records in resumable batches with idempotency keys.
7. Verify counts, hashes, relationships, and media availability.
8. Commit the identity binding only after validation succeeds.
9. Retain a recoverable migration journal until the operation is confirmed.
10. Provide a safe rollback/retry path.

Do not merge two anonymous learners just because they use the same device. Do not merge two accounts automatically based only on matching email text.

## 5. Local-first operation and offline contract

The app should remain useful offline for downloaded worlds, authored content, local learning activities, personal journal/creations, and supported story/world actions.

### 5.1 Offline capability classes

Every feature must declare one of:

- **Offline-complete:** all required content and state transitions are available locally.
- **Offline-with-queued-sync:** action is committed locally and queued for remote synchronization.
- **Read-only offline:** cached content can be viewed but no durable mutation is offered.
- **Online-required:** the feature genuinely requires a remote service; explain this before the user invests effort.

Do not display a false success for an online-required action while disconnected. For queued actions, distinguish “saved on this device” from “synced to account.”

### 5.2 Local transaction boundary

A user action that changes several local records must be atomic where the storage engine permits. If true transactions are unavailable, use a journaled operation with:
- stable operation ID;
- learner ID;
- domain and schema version;
- expected precondition/version;
- intended mutations;
- creation time from trusted local monotonic ordering where available;
- state (pending, applied, syncing, synced, conflict, failed);
- retry count and last error category.

On startup, recover incomplete operations before presenting dependent state.

### 5.3 Offline queue

The outbox must support ordering where causality matters, bounded retries with backoff, idempotent replay, dead-letter inspection, cancellation where safe, and explicit conflict handling. Do not retry permanent authorization or validation failures indefinitely.

Critical content and personal state must not depend on an in-memory event listener being alive when an event occurs.

## 6. Synchronization and conflict policy

### 6.1 General protocol

- Use stable globally unique record and operation IDs.
- Include learner scope, entity type, schema version, mutation version, and causal references.
- Prefer append-only event records for historical facts and carefully versioned current-state projections for mutable entities.
- Use server acknowledgements and explicit sync cursors; do not infer success from a request being sent.
- Make retries safe through idempotency constraints.
- Preserve enough operation history to diagnose and recover partial synchronization.
- Never let client-provided ownership fields override authenticated server identity.

### 6.2 Conflict classes

| Data type | Default conflict approach |
|---|---|
| Preferences | Field-level merge where safe; user choice for incompatible settings |
| Learning attempts | Append-only; deduplicate by stable attempt ID |
| Mastery/proficiency | Recompute from validated attempt history or domain-defined merge; never blindly take max |
| Story choices | Preserve causal history; resolve branch conflicts explicitly, not last-write-wins |
| Discoveries/unlocks | Set union only where discovery semantics are monotonic and verified |
| Inventory/economy | Server-authoritative transaction or validated ledger; no client-side balance merge |
| World state | Domain-specific merge with version and event ordering |
| Personal creations | Preserve versions; conflict copy rather than overwrite |
| Memory facts | Merge only when provenance and ownership match; retain conflicting evidence |
| Time-based simulation | Reconcile using canonical world clock and bounded offline policy |

“Last write wins” is acceptable only for low-risk fields where the product explicitly accepts lost updates. It is not a universal synchronization strategy.

### 6.3 Cross-domain operations

Examples such as completing a story beat, recording a learning outcome, updating a world object, and adding a journal entry must not be implemented as unrelated best-effort writes.

Use a transaction when all affected records share one transactional store. Across services/stores, use a durable outbox/saga:
1. validate the initiating action;
2. commit the domain's authoritative state and an outbox event together;
3. process downstream effects idempotently;
4. record completion/failure and retry safely;
5. expose a coherent pending state until the operation is settled.

Define compensating actions for reversible effects. Do not pretend an irreversible choice can be rolled back without preserving the original history.

## 7. Time, ordering, and offline catch-up

Store absolute instants as UTC timestamps with explicit timezone context where local interpretation matters. Distinguish:
- server/UTC time for audit and cross-device ordering;
- world-local calendar and timezone for authored events;
- monotonic elapsed time for in-session durations and cooldowns;
- device wall time as an untrusted hint, not authoritative progression.

World time and seasonal calendars are authored simulation rules, not direct aliases for the learner's device date. The canonical world clock and timezone model remain product decisions.

For offline simulation:
- cap catch-up duration by domain;
- use deterministic, versioned simulation inputs;
- avoid granting unbounded growth, rewards, relationship changes, or story advancement from a large clock jump;
- detect implausible clock movement and defer to trusted server time when online;
- do not punish a learner for being offline or absent;
- make time-locked personal creations honest and understandable;
- retain the ability to replay a simulation calculation from its inputs and version.

## 8. Schema and content versioning

Every persisted record or aggregate must declare a schema version. Every authored content bundle must declare content version, compatibility range, stable semantic IDs, and dependency references.

Migration requirements:
- migrations are ordered, deterministic, resumable, and tested against realistic prior data;
- preserve unknown fields where forward compatibility is required;
- validate before and after migration;
- keep a backup or rollback snapshot for destructive transformations;
- never silently discard a learner's data on parse failure;
- quarantine corrupt records with recoverable diagnostics and a user-safe explanation;
- support content references whose authored content has been revised or retired;
- preserve historical meaning when a story or world asset changes.

Cache and download invalidation must be version-aware. Asset filenames are not durable identity; use semantic asset IDs and content manifests.

## 9. Memory, provenance, and character access

Memory is not a generic text bucket. Each stored memory item must include:
- owner learner ID;
- memory category and purpose;
- source event or source record;
- occurred-at and recorded-at timestamps;
- provenance and confidence/evidence level;
- scope and visibility;
- retention class and expiry/review policy where applicable;
- correction/deletion status;
- content/schema version.

Distinguish learner-confirmed facts, directly observed actions, inferred preferences, temporary context, and authored fictional canon. Inferences must not be represented as facts. Learners must be able to inspect and correct personal memories that materially affect experiences.

Character memory access must be purpose-limited and policy-controlled. Cassidy and residents must not access private learner data merely because it exists. The learner must have understandable controls for what can be remembered and used. Never fabricate a shared memory, imply certainty where evidence is weak, or use personal memories to create guilt or emotional dependency.

## 10. Privacy and data minimization

### 10.1 Data inventory

Before implementation, create a data inventory for each feature: data fields, purpose, owner, sensitivity, collection point, local/remote location, processors, retention, access, export, deletion, and security controls.

Collect only what is necessary for a stated feature. Avoid collecting precise location, contacts, identifiers, raw voice, camera data, or behavioral telemetry by default.

### 10.2 Voice, camera, and AI services

For any external speech/AI/voice provider:
- identify the provider and processing purpose;
- explain whether audio/text leaves the device;
- obtain clear consent before capture or transmission;
- show recording state and provide a cancel path;
- specify whether raw audio, transcripts, prompts, and outputs are retained by the app or provider;
- disclose training/use policies based on verified provider terms;
- offer deletion and retention controls where available;
- do not send unrelated memory or profile context;
- avoid sending children's data to third parties until audience/age policy and legal review are settled.

Playback, shadowing, microphone capture, speech-to-text, pronunciation assessment, and conversational AI are separate capabilities with separate data flows and consent requirements.

### 10.3 Analytics and diagnostics

Analytics must be purpose-limited, documented, configurable where appropriate, and minimized. Do not put message text, raw voice, private memories, personal creations, access tokens, or precise location into routine telemetry. Crash reports should scrub personal content and secrets. Product analytics must not become a covert emotional or behavioral profile.

## 11. Security requirements

- Encrypt network traffic using current secure transport.
- Use platform-protected storage for refresh tokens and other secrets; do not store credentials in plain preferences.
- Keep privileged backend keys out of client builds.
- Enforce authorization server-side for every private record and blob.
- Apply least privilege to service roles and third-party processors.
- Validate input and file types; scan or safely process uploaded media.
- Protect local databases and backups according to platform capabilities and documented threat model.
- Avoid logging personal payloads, credentials, tokens, or voice content.
- Define session expiry, token rotation, sign-out, device loss, and compromised-account response.
- Test account switching and authorization boundaries, not only happy-path reads.
- Do not rely on obscurity of local keys or UI hiding as access control.

## 12. Personal creations and media lifecycle

Postcards, phrase cards, comics, journals, memory boards, saved scenes, and user-authored media are learner-owned content.

Each creation needs stable identity, owner, title/type, version history, created/updated timestamps, editable source representation, media references, provenance, and deletion state.

Media storage must define:
- local draft and upload states;
- resumable uploads and checksum verification;
- thumbnail/derivative generation;
- content type and size limits;
- access controls and signed delivery;
- offline availability and cache eviction;
- replacement/versioning;
- orphan cleanup;
- deletion propagation to derivatives and backups under retention policy;
- export format and portability.

A creation must not be trapped as an uneditable rendered image if its source can reasonably be preserved. Export should preserve content and referenced media or clearly report omissions.

## 13. Export, correction, deletion, backup, and recovery

### 13.1 Export

Provide a user-initiated export of personal data in documented, portable formats. Include profile/preferences, learning records, story choices, discoveries, memories, creations, media or media references, and relevant metadata. Explain exclusions, format, processing time, and how to protect the export.

### 13.2 Correction and deletion

Provide controls to:
- inspect and correct personal profile/memory information;
- delete individual memories, conversations, recordings, and creations where supported;
- clear downloaded/cache data without deleting account progress;
- reset a local anonymous profile with clear consequences;
- request account deletion and understand its scope.

Deletion must cascade through derived indexes, caches, media derivatives, queued jobs, and third-party processors where applicable. Pending offline deletion requests must be retained securely and applied before stale data can reappear after sync. Explain any legally required retention exceptions and their duration.

### 13.3 Backup and recovery

Define backup frequency, encryption, retention, restore testing, recovery-point objective, and recovery-time objective before launch. Backups must be isolated from ordinary client access. Test full account restoration and partial corruption recovery. A backup is not a substitute for export or deletion.

## 14. Failure and recovery behavior

The product must explicitly handle:
- app termination during a local write;
- device restart during upload or account migration;
- network loss after server commit but before acknowledgement;
- duplicate event delivery;
- out-of-order events;
- expired credentials;
- account switching with queued writes;
- schema/content upgrade during offline use;
- corrupted local data;
- full device storage;
- deleted/retired content references;
- remote deletion while a device is offline;
- failed media upload and orphaned media;
- restore from backup.

User-facing language must distinguish saved locally, syncing, synced, conflict requiring attention, and failed. Never claim a record is safely backed up merely because it exists in local storage.

## 15. GoPAL-AI reference research: findings and cautions

Selected read-only source files inspected:
- src/lib/localStore.ts
- src/lib/storage.ts
- src/lib/supabaseClient.ts
- src/services/auth.ts
- src/engines/memory/memoryEngine.ts
- supabase/schema.sql

### Useful concepts recovered

- Local persistence and a remote Supabase path were both attempted.
- The schema models learner preferences, world state, relationships, memories, learning attempts, stories, creations/postcards, progression, discoveries, inventory, and journey events.
- Some remote tables use owner-scoped row-level policies.
- Memory categories and source-event references provide a useful starting vocabulary.
- Local cache and durable store were conceptually separated.

### Concrete limitations observed in selected code

- Local storage keys use a shared gopal:store: namespace without a learner ID.
- Local world state, memories, journey events, Cassidy relationship, and demo seeds use the hard-coded local-explorer-user.
- When Supabase is not configured, auth returns one shared local demo identity rather than creating an isolated anonymous learner.
- The memory engine's local fallback calls LocalStore.addMemory(layer, fact) and getMemories() without forwarding the supplied userId; a failed remote insert can therefore fall back to shared local state.
- The memory engine can fall back to local memories when a remote query returns no rows, conflating “no remote records” with a local fallback.
- Several LocalStore getters seed demo progress, memories, creations, bookmarks, artifacts, and revisit counts, so a clean first-run experience is not guaranteed by these getters.
- Local writes catch and log errors rather than returning a durable operation status to the caller.
- Local mutations use read-then-write patterns without a transaction or operation journal.
- IDs for local memories and journey events are based on Date.now(), which is not a robust globally unique or idempotent event identity.
- The inspected memory record stores a canonical fact and timestamp but lacks confidence, provenance detail, retention, correction, and visibility metadata.
- The schema enables RLS on many tables and defines owner policies for selected personal tables; RLS enablement alone is not proof that every table has a complete, correct policy set.
- The inspected schema includes user-owned creations/progress-like tables, but this alone does not prove account migration, offline sync, conflict resolution, export, deletion, backup, or crash recovery.
- The Supabase client persists auth through AsyncStorage; a production design must evaluate platform-protected secret storage and threat model rather than inheriting that choice.

These observations are limited to the selected files and do not constitute a complete security review of GoPAL-AI. No source code or schema is being copied.

## 16. Required acceptance tests

1. Two anonymous learners on one device cannot read, overwrite, or infer each other's records.
2. Signing out and switching accounts clears all in-memory and cached private context before the next account renders.
3. An anonymous learner can link an account without losing creations or duplicating learning attempts.
4. Interrupted account migration can resume or roll back without partial ownership.
5. Offline actions show accurate local-save and sync status.
6. Duplicate and out-of-order event delivery does not duplicate rewards, story choices, memories, or progress.
7. A crash between domain commit and downstream processing is recovered by the outbox.
8. Conflicting story choices are preserved and resolved without silent branch loss.
9. Device clock changes cannot generate unlimited offline growth or unlocks.
10. Corrupt data is recoverable or quarantined; it is never silently replaced with demo progress.
11. Export contains the documented personal data and media or a clear manifest of unavailable items.
12. Deletion prevents stale offline devices from restoring deleted personal data after reconnect.
13. Character memory retrieval respects learner scope, consent, purpose, and visibility.
14. Raw audio and transcripts follow declared consent, retention, and deletion policies.
15. Authorization tests reject cross-learner reads and writes at the backend boundary.
16. Backup restore is tested against documented recovery objectives.
17. Schema migration is tested with representative old, partial, and interrupted datasets.
18. Full storage, expired tokens, revoked sessions, and provider outages produce safe, understandable behavior.

## 17. Decisions still open

- Anonymous-first, account-first, or optional account model.
- Backend and database choice; local database technology.
- Authentication provider and protected token-storage implementation.
- Whether sync is multi-device at first release.
- Which features are offline-complete and which require connectivity.
- Conflict UX and canonical world-clock/timezone policy.
- Voice/AI vendors, retention terms, and supported age range.
- Export format and account-deletion service-level target.
- Backup retention, recovery objectives, and operational ownership.
- Data residency and jurisdictional compliance requirements.

These decisions require product-owner input, technical evaluation, and where relevant legal/privacy review. No backend or implementation is selected by this draft.

## 18. Approval checklist

- [ ] Data inventory and classification reviewed.
- [ ] Learner identity and anonymous migration model approved.
- [ ] Offline capability matrix approved.
- [ ] Sync/conflict semantics approved per domain.
- [ ] Memory provenance and access policy approved.
- [ ] Voice/AI consent and retention model approved.
- [ ] Export/deletion/backup policy approved.
- [ ] Threat model and authorization design reviewed.
- [ ] Acceptance tests and operational ownership agreed.
- [ ] Product owner approves this specification.

**Implementation remains blocked until the complete Language-world blueprint is reviewed and explicitly approved.**
