# Language-world — Technical Architecture

**Status:** Working architecture specification v0.1 — engine/backend neutral; not approved for implementation  
**Date:** 26 November 2026  
**Depends on:** Master Blueprint, Blueprint Reconciliation, Architecture Decisions, Engine Evaluation, domain specifications  
**Purpose:** Define how the product's systems fit together without selecting an engine, backend, database, or service prematurely.

---

## 1. Architecture intent

Language-world is a persistent, multi-world experience with authored narrative, learning, characters, simulation, cinematic presentation, travel, creative work, and optional future connected services. Its architecture must make these systems coherent without turning them into one large runtime or a collection of disconnected features.

The architecture must support:
- A living universe whose state and content are not owned by the renderer.
- Independent domains with one authoritative owner for each kind of durable state.
- Replaceable presentation and media assets.
- A complete offline/online lifecycle appropriate to the eventual product promise.
- Durable, recoverable cross-domain experiences.
- Honest separation of authored facts, learner data, character knowledge, generated output, and presentation.
- Measured Android performance and graceful degradation.
- A maintainable content-production system for many worlds and experiences.
- An engine/runtime boundary that permits evidence-led engine selection.

**Non-goals:** This document does not select Godot, Unity, Unreal, a database, a backend, an AI provider, a speech service, or a content delivery vendor. It does not authorize implementation or a prototype.

## 2. Non-negotiable architecture principles

1. **Domain truth is renderer-independent.** Engine scene objects, animation graphs, UI components, and cinematic timelines are not authoritative product state.
2. **One owner per durable fact.** Each domain owns the state it is responsible for; consumers use explicit commands, queries, and events.
3. **No implicit cross-domain state access.** A system must not reach into another domain's internal store or mutate its state directly.
4. **Authored content is separate from learner state.** World canon, stories, learning content, and asset manifests are versioned content; personal progress is separately scoped.
5. **Presentation is replaceable.** 2D, 2.5D, and 3D representations may change without changing story or domain identity.
6. **Events are not automatically durable.** Consequential operations need durable records and recovery; a transient event bus is only a delivery mechanism.
7. **Offline behaviour is explicit.** Every feature declares what works offline, what queues, what is unavailable, and how it recovers.
8. **Privacy is designed into boundaries.** Personal data, voice, AI prompts, analytics, and diagnostics have explicit scope and permissions.
9. **Simulation is bounded.** Only relevant entities and state are updated at high fidelity.
10. **Content quality is a system requirement.** Authoring, localization, cultural review, versioning, validation, and rollback are part of the architecture.
11. **No legacy dependency.** No GoPAL-AI code, assets, media, tools, 3D pipeline, or implementation contracts are used as a foundation.
12. **Evidence before commitment.** Engine and service choices require representative tests and decision records.

## 3. Logical architecture

The system is described in logical layers. They may be packaged differently depending on the selected engine and backend; the boundaries are the requirement.

### 3.1 Client experience shell

Responsibilities:
- Application lifecycle and platform integration.
- Onboarding, settings, account, help, privacy and accessibility surfaces.
- Navigation and transition between world, activity, archive and study experiences.
- Input abstraction and focus management.
- Session orchestration and error/recovery presentation.
- User-controlled audio, captions, motion and display preferences.

The shell must not own world, story, learning, character or travel truth. It coordinates domain entry and presentation.

### 3.2 Presentation and world runtime

Responsibilities:
- Rendering, cameras, lighting, materials, scene composition and visual effects.
- Character and creature embodiment: movement, gaze, expression, gesture and animation evaluation.
- Physics, collision, navigation and spatial interaction.
- Audio playback, mixing and spatial audio.
- Asset loading, streaming, LOD and resource lifecycle.
- Engine-specific input, platform and accessibility adapters.

This layer consumes semantic domain state and presentation intents. It may report user actions and completed presentation beats, but it cannot independently commit canonical world or learner state.

### 3.3 Experience orchestration

Responsibilities:
- Resolve a learner's chosen intention (explore, learn, story, create, relax, travel, or another approved mode).
- Select eligible experiences from an authored catalogue.
- Coordinate entry, session sizing, pause, exit, re-entry and optional recommendations.
- Explain recommendations and respect user controls.
- Route requests to the domain that owns the selected experience.

The Experience Director is a bounded coordinator, not an AI god-object. It cannot invent unreviewed content, grant progression, mutate learning mastery, or own story/world state.

### 3.4 Domain services

The domain layer contains product rules and authoritative state ownership. See Section 4.

### 3.5 Content and delivery

Responsibilities:
- Versioned world and narrative content.
- Learning objectives, exercises, assessment rubrics and localization.
- Experience definitions and configuration.
- Asset/audio manifests and compatibility metadata.
- Downloadable content packs, dependency resolution and rollback.
- Validation and publishing workflow.

Content must be usable independently of any one renderer. Engine-specific import products are build outputs, not canonical content identity.

### 3.6 Persistence and synchronization

Responsibilities:
- Local durable storage.
- Remote persistence where required.
- Identity and learner scoping.
- Transaction boundaries, outbox/inbox, retries and idempotency.
- Sync, conflict resolution, migrations, export, deletion and backup.
- Content cache and offline pack management.

The storage technology is open. The contracts and privacy invariants are not.

### 3.7 External services and platform adapters

Potential integrations include authentication, AI generation/retrieval, speech recognition, voice synthesis, analytics, crash reporting, notifications, payment, and content delivery. Each integration requires a dedicated adapter, data contract, permission boundary, retention policy, timeout/retry strategy, and fallback. None is assumed to be required at launch.

## 4. Domain boundaries and ownership

| Domain | Owns canonical state | Does not own |
|---|---|---|
| Universe & World Registry | World/region/place identities, authored geography, world metadata, content versions | Learner visit history, renderer scenes |
| World State & Simulation | Persistent world facts, schedules/outcomes, weather/calendar state where canonical, environmental event outcomes | Frame animation, camera, audio playback |
| Places, Objects & Interaction | Object identity/capabilities, durable object state, interaction rules, learner-owned placements where applicable | Meshes, filenames, renderer nodes |
| Characters & Residents | Character canon, resident schedules/commitments, bounded character state, character knowledge boundaries | UI widgets, animation clip filenames |
| Cassidy | Cassidy-specific canon, motives/plans/commitments, permitted memory references, character actions/knowledge | Global learner identity, canonical memory store, renderer state |
| Creatures & Ecology | Species definitions, habitats, ecological state and authored behaviours | Generic collectible economy, animation assets |
| Narrative & Quest | Story canon, clue definitions, learner story knowledge/choices, quest objectives and resolution | Learning mastery, cinematic playback |
| Travel | Route graph, journey session, transport state, departure/arrival/handoff status | Vehicle model, cinematic camera sequence |
| Cinematics | Authored sequence definitions, beat progression/presentation checkpoint metadata | Durable journey/world/story outcomes |
| Learning | Learning objectives, attempts, responses, evidence, skill estimates, review schedule | General world state, character memory |
| Experience Catalogue/Director | Approved experience metadata, eligibility and recommendation decision | Authoritative state of experiences' domains |
| Creative Archive | Learner-created source objects, revisions, media references, privacy/sharing settings | World canon, raw chat logs by default |
| Audio & Voice | Semantic cue definitions, playback requests and audio-learning session metadata within scope | Character canon, unconsented recordings |
| Identity & Privacy | Learner identity, consent, data permissions, account lifecycle | Learning or story content |
| Persistence & Sync | Durable storage mechanics, event/outbox processing, migration and synchronization | Product meaning of domain records |
| Analytics & Operations | Minimsed operational events, diagnostics and service health | Hidden learner profiling or canonical progression |

The exact module boundaries and deployment topology are open. The ownership rules are mandatory.

### 4.1 Cross-domain command pattern

A domain exposes explicit commands and queries. A command:
- Names the intended domain action.
- Includes a stable operation ID.
- Includes the learner/account scope when personal state is involved.
- Includes expected version or concurrency token where required.
- Validates permission, eligibility and current state.
- Returns a durable outcome or a clear failure.

A consumer never calls another domain's private storage API or mutates its internal object.

### 4.2 Cross-domain event pattern

Events communicate facts that have already been committed by the owning domain. They include:
- Stable event ID.
- Event type and schema version.
- Aggregate/domain owner and aggregate ID.
- Learner/account scope where applicable.
- UTC occurrence/recording time and relevant authored/simulation time.
- Causation ID and correlation ID.
- Payload with minimal required data.
- Privacy classification and retention category.

An event is not a command disguised as a fact. A subscriber may react, but only the owner can commit changes to its domain.

## 5. State classes and storage authority

Every record must be classified before implementation.

| State class | Examples | Authority and lifecycle |
|---|---|---|
| Authored canon/content | World bible, story, dialogue, learning item, asset manifest | Versioned content source; published immutable version with controlled replacement |
| Learner durable state | Discovery, learning evidence, story choice, journey, personal creation | Learner-scoped durable record; correction/export/deletion rules |
| Shared durable state | Shared event or community state, only if approved | Server-authoritative with explicit participation and moderation policy |
| Session state | Current camera, temporary dialogue choice, in-progress unsaved interaction | Memory/session storage; recovery policy depends on experience |
| Presentation state | Animation blend, camera interpolation, particle state | Runtime only; reconstructible and disposable |
| Derived/read model | Map overlay, dashboard summary, recommendation features | Rebuildable from canonical state; never sole authority |
| Cache/content pack | Downloaded models, audio, world packs | Versioned, integrity checked, evictable within offline promise |
| Operational telemetry | Crash report, performance sample, service trace | Minimized, purpose-limited, consent/legal policy, retention bound |

Every domain must state its schema owner, storage adapter, migration policy, deletion semantics, offline availability, and recovery behaviour.

## 6. Durable operation and event processing

A multi-domain experience may produce several consequences. Example: completing a language activity during a festival may create a learning attempt, update a clue, record a journey moment, and change a world object.

These effects must not rely on a chain of unprotected in-memory callbacks.

### 6.1 Required operation lifecycle

1. Create a stable operation ID and capture the learner/session scope.
2. Validate the initiating action and all required preconditions.
3. Commit the owning domain's primary state change and an outbox record within one local transaction boundary where supported.
4. Dispatch the outbox event to interested domains.
5. Each consumer records an inbox/idempotency key and applies its own domain transaction.
6. Retry transient failures with bounded backoff.
7. Surface permanent/partial failure in diagnostics and provide repair/replay where safe.
8. Mark completion only when required effects have reached the defined consistency level.

### 6.2 Consistency policy

Use strong atomicity inside one domain transaction. Across domains, use an explicit durable workflow/saga or equivalent recoverable process. Do not promise global database transactions across independent services unless the chosen architecture proves that capability.

Define which side effects are:
- Required for the initiating action to count as complete.
- Eventually consistent and safe to retry.
- Optional presentation effects.
- Compensatable or reversible.
- Irreversible and therefore require pre-validation.

### 6.3 Idempotency and ordering

Stable IDs must be generated before retry. Consumers must tolerate duplicate delivery. Ordering must be explicit per aggregate/stream where order matters; wall-clock timestamps alone are not an ordering guarantee.

## 7. Runtime lifecycle and clocks

Keep the frame loop separate from product simulation and durable time.

### 7.1 Runtime phases

- **Cold start:** load platform configuration, validate local identity/session, load critical content and restore durable state.
- **World entry:** resolve world/region version, restore relevant state, preload presentation dependencies, establish input/audio/focus.
- **Active session:** process input, domain commands, bounded simulation, presentation and durable writes.
- **Backgrounding:** stop or reduce rendering/audio, persist required checkpoints, release platform resources, suspend nonessential work.
- **Resume:** validate session/content versions, recover incomplete operations, restore scene/presentation, resume permitted audio and input.
- **Termination/relaunch:** reconstruct from durable domain state and resumable session checkpoints, never from assumed in-memory continuity.
- **Sign-out/account switch:** isolate learner scope, flush/secure permitted writes, clear private caches and active session references, prevent cross-account leakage.

### 7.2 Time domains

- UTC event time for durable cross-device records.
- Learner-local time for local schedules and presentation, with timezone-change policy.
- Authored world calendar/time for fictional chronology and festivals.
- Simulation time for bounded offline advancement.
- Cinematic time for authored sequence pacing.
- Frame/render time for visual update only.

No domain may silently substitute device wall time for a trusted unlock, durable ordering, or canonical chronology.

## 8. Offline and synchronization architecture

The final offline promise is open, but every feature must declare one class:

1. **Offline-complete:** works without network and syncs later.
2. **Offline-with-limits:** core experience works, but selected media/AI/social capabilities are unavailable.
3. **Online-required:** clearly explains why network is required and fails gracefully.

A local-first write must have an explicit durable queue and status. "Saved locally", "sync pending", "synced", and "sync failed" are distinct states.

Conflict policy is domain-specific:
- Append-only evidence may merge by stable operation ID.
- Personal editable documents need revision/conflict handling.
- Authored content is versioned and not merged with learner data.
- World/shared state requires an explicit authority model.
- Deletion and consent revocation must propagate and must not be undone by stale clients.

Account migration, anonymous identity, sign-out, multi-device conflict, backup, export and deletion must be specified before choosing a storage provider.

## 9. Content, world packs, and asset architecture

### 9.1 Canonical content identity

Use stable semantic IDs for worlds, regions, places, objects, characters, stories, learning objectives, experiences, audio cues, animation intents, cinematic sequences and assets. IDs must not encode:
- Display language or localized names.
- Asset filenames or artist folder structure.
- Engine scene/node paths.
- Clip names or renderer implementation.
- Mutable coordinates or presentation details.

### 9.2 Content pack manifest

Each published pack should declare:
- Pack ID, semantic scope and version.
- Minimum compatible application/content schema version.
- Dependencies and required/optional status.
- Localization and cultural review status.
- Asset/audio manifest references and checksums.
- Quality tier and device requirements.
- Provenance, licence/rights and attribution metadata for Language-world-owned content.
- Migration/deprecation and rollback rules.
- Integrity/signature metadata as required by delivery security.

### 9.3 Replacement and presentation adapter

A domain object references a semantic asset role. The selected engine adapter resolves that role to a compatible presentation asset. Gameplay/story logic does not know the filename, importer, renderer node or animation clip.

Placeholder-to-final replacement must preserve:
- Semantic identity.
- Scale/origin/orientation conventions.
- Interaction/collision affordances.
- Rig/animation semantic compatibility where applicable.
- LOD/performance requirements.
- Accessibility and fallback behaviour.

No GoPAL-AI asset or production artifact is part of this pipeline.

## 10. Cinematics, travel, and character performance integration

Cinematics are a presentation runtime that consumes a sequence definition and emits presentation-completion/checkpoint signals. Travel, story, and character domains remain authoritative for the event being presented.

A cinematic sequence definition references:
- Stable sequence and beat IDs.
- Trigger/eligibility conditions.
- Actor and semantic performance intents.
- Camera and environment presentation intents.
- Dialogue/subtitle/localization tracks.
- Audio cue intents.
- Checkpoint, skip, replay, pause and recovery policy.
- Required asset/content versions.
- Handoff contract and fallback.

Travel commits its durable state transition before or at a defined transaction boundary; the cinematic presents the transition. If presentation is skipped or fails, travel state remains correct and the user can reach the destination safely.

Cassidy's intelligence and canonical state are separate from her visual embodiment. The character domain decides intent/action; the engine adapter realizes movement, gaze, gesture and expression. If a model or animation is unavailable, a safe fallback must not corrupt character or story state.

## 11. Learning and AI service boundaries

Learning owns the objective, attempt, response, evidence, feedback decision and skill estimate. External AI/speech services provide bounded observations or suggestions; they do not silently write mastery or character memory.

Every service call must define:
- Data sent and purpose.
- User consent and eligibility.
- Provider retention/training-use policy.
- Timeout, retry, cancellation and offline behaviour.
- Confidence/uncertainty and evaluation limits.
- Human-authored fallback and user-visible capability statement.
- Logging minimization and deletion path.

AI-generated dialogue must be distinguishable from canon. It cannot invent persistent shared events, character memories, or world facts without an approved domain action and provenance.

No assumption is made that Cassidy, every resident, or every activity requires generative AI.

## 12. Security, privacy, and trust boundaries

Threat modelling must include:
- Learner/account scope leakage across local stores, caches, files, logs and sync.
- Unauthorized access to personal archive and voice data.
- Prompt injection or untrusted content in retrieved/user-generated material.
- Tampered local state, clocks, unlocks and content packs.
- Replayed or duplicated events/commands.
- Insecure secrets, tokens, deep links and service configuration.
- Content update rollback or malicious package substitution.
- Data deletion that fails to propagate to backups, vendors or offline devices.

Apply least privilege, secure token storage appropriate to the platform, encrypted transport, protected local data where warranted, server-side authorization, signed/validated content delivery, retention limits, and auditable deletion. Exact controls depend on selected providers and a formal threat model.

## 13. Observability and operations

Operational telemetry should answer product reliability questions without collecting unnecessary personal content.

Define:
- Crash/error categories and redaction rules.
- Startup, loading, frame-time, memory, thermal and audio interruption measurements.
- Content pack failure and version compatibility.
- Save/sync queue health and retry outcomes.
- AI/speech service latency, availability, cost and failure categories.
- Release health, rollback and incident procedures.
- Retention and access controls for diagnostics.

Analytics must not become hidden emotional profiling or a measure of user worth. Product metrics should focus on reliability, learning evidence, experience quality, accessibility and user-chosen outcomes.

## 14. Testing strategy

### 14.1 Domain tests
- State transition and invariant tests.
- Time and deterministic simulation tests.
- Learning evidence and scoring validity tests.
- Story/clue fairness and continuity tests.
- Character knowledge and memory permission tests.
- Travel state machine and skip/recovery tests.

### 14.2 Contract and integration tests
- Domain command/event schema compatibility.
- Idempotency and duplicate delivery.
- Outbox/inbox retries and partial failure.
- Content pack version/dependency compatibility.
- Asset replacement with unchanged domain behaviour.
- Account switching and learner-scope isolation.
- Local/remote sync and conflict resolution.

### 14.3 Failure-injection tests
- App killed during save, cinematic, travel, sync and download.
- Network lost before/after commit.
- Storage full, corrupt, unavailable or migrated.
- Duplicate/reordered events.
- Provider timeout, refusal, invalid output or outage.
- Audio focus interruption and permission revocation.
- Asset missing, incompatible or failed to load.
- Device clock/timezone changed while offline.

### 14.4 Device and experience tests
- Representative low/mid/high Android tiers.
- Cold/warm start, scene transition, thermal soak, memory and battery.
- Touch readability, reduced motion, captions, screen reader and audio controls.
- 20–30 minute sustained world session and repeated travel transitions.
- Real learner walkthroughs for first-open, exploration, learning, travel, return and archive.

No benchmark is accepted from editor preview alone. Target devices and thresholds must be selected before engine choice.

## 15. Engine and backend adapter policy

Engine candidates remain those in ENGINE_EVALUATION.md until updated evidence supports another option. The selected engine must implement the presentation/platform adapters without leaking engine types into domain contracts.

Backend and database candidates must be compared against:
- Learner identity and account lifecycle.
- Local-first operation and conflict semantics.
- Transaction/outbox requirements.
- Data residency, privacy, deletion and export.
- Content delivery and versioning.
- Operational cost, availability and maintainability.
- AI/voice integration boundaries.

A managed backend may simplify operations but cannot replace product-level data ownership, privacy policy, offline queue, or domain invariants.

## 16. Architecture decisions still open

- Engine and rendering mode.
- Target Android device tiers and minimum hardware.
- Application shell/runtime packaging around the engine.
- Local database and protected storage technology.
- Backend, authentication and sync provider.
- Content delivery/packaging and patch strategy.
- AI, speech recognition and voice synthesis providers—or whether to use them at all in the first release.
- Shared/social architecture, if approved.
- Analytics/crash tooling and retention.
- Exact domain deployment boundaries (modular monolith/client domains vs separate services).

These are not blockers to completing product design, but they are blockers to implementation decisions that depend on them.

## 17. Architecture acceptance checklist

- [ ] Every durable state type has one named owner.
- [ ] Domain boundaries and command/query/event contracts are reviewed.
- [ ] State classes and storage authorities are mapped.
- [ ] Cross-domain operations have idempotency, recovery and partial-failure semantics.
- [ ] Runtime lifecycle and all clock domains are specified.
- [ ] Offline capability classes and account isolation are agreed.
- [ ] Content pack and semantic asset contracts are compatible with designer handoff.
- [ ] Cinematic/travel/story ownership boundaries are tested on paper.
- [ ] AI/voice data and capability boundaries are explicit.
- [ ] Threat model, privacy and deletion paths are reviewed.
- [ ] Android performance and failure-injection test plans are measurable.
- [ ] Engine/backend decisions remain open until evidence and approvals exist.
- [ ] Product owner reviews this architecture before implementation.

**Current decision:** architecture design only. This document is a working specification, not an engine selection or authorization to create a project, prototype, or production asset.
