# Language-world Blueprint Work Register

**Status:** Active design phase — no implementation authorized  
**Last updated:** 26 November 2026  
**Purpose:** Track blueprint research, decisions, documents, dependencies, and approval gates so the project does not drift into premature development.

## Project boundary

- GoPAL-AI is a read-only reference archive.
- All new product design, specifications, assets, architecture, and implementation belong in Language-world.
- No Expo.
- No reuse of the legacy GoPAL 3D pipeline or its models, rigs, animations, scripts, tools, exporters, validators, or pipeline-specific contracts.
- Engine selection remains open pending representative Android evaluation.
- Temporary assets are acceptable; the asset architecture must support reliable replacement.
- No application implementation until the Master Blueprint and required supporting specifications are reviewed and explicitly approved.

## Current authoritative documents

| Document | Role | Current state |
|---|---|---|
| [Master Blueprint](MASTER_BLUEPRINT.md) | Central product vision and system index | Working draft v0.3+; Cassidy canon added |
| [Product Systems Audit](PRODUCT_SYSTEMS_AUDIT.md) | Evidence and limitations from selected reference files | Sections 1–50; ongoing |
| [Archive Gap Audit](GOPAL_ARCHIVE_TO_LANGUAGE_WORLD_GAP_AUDIT.md) | Recovered product concepts and new-product gaps | Working research document |
| [Cassidy Character Bible](CASSIDY_CHARACTER_BIBLE.md) | Independent Language-world character canon and production direction | Working draft v0.1; review required |
| [World & Universe Bible](WORLD_UNIVERSE_BIBLE.md) | Universe hierarchy, Emerald Valley, distinct world standards and registry | Working draft v0.1; world canon incomplete |
| [Experience Catalogue](EXPERIENCE_CATALOGUE.md) | Experience taxonomy, 60 research seeds, learning integration, authoring and quality gates | Working draft v0.1; portfolio and scope require review |
| [Learning Design](LEARNING_DESIGN.md) | Capability/evidence model, adaptive support, evaluation, speech honesty, privacy and accessibility | Working draft v0.1; language scope and validation remain open |
| [World Simulation Specification](WORLD_SIMULATION_SPEC.md) | Canonical time, climate/weather, residents, ecology, plants, events, offline and performance | Working draft v0.1; clock model and world profiles remain open |
| [World Objects and Spaces](WORLD_OBJECTS_AND_SPACES.md) | Spatial hierarchy, buildings/interiors, objects, interactions, navigation, inventory and personal spaces | Working draft v0.1; launch scope and technical contracts remain open |
| [Travel Experience Specification](TRAVEL_EXPERIENCE_SPEC.md) | Route graph, transport, journey state, cinematic staging, arrival and recovery | Working draft v0.1; first route remains to be authored |
| [Audio, Voice, and Soundscape](AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md) | World sound identity, cue/mix contracts, character voice, learning audio, captions and accessibility | Working draft v0.1; engine, voice scope and production plan remain open |
| [Narrative and Story Continuity](NARRATIVE_AND_STORY_CONTINUITY_SPEC.md) | Story canon, mysteries, clues, choices, resident autonomy, quests, journal and re-entry | Working draft v0.1; initial story portfolio and canon remain open |
| [Persistence, Privacy, and Synchronization](PERSISTENCE_PRIVACY_AND_SYNC.md) | Learner identity, local-first data, sync, conflicts, memory, privacy, security, export, deletion, recovery | Working draft v0.1; identity, backend, offline promise, and policies remain open |
| [Creative Experiences and Personal Archive](CREATIVE_EXPERIENCES_AND_PERSONAL_ARCHIVE.md) | Journal, phrasebook, postcards, comics, boards, museum, capsules, conversation archive, editable source and media lifecycle | Working draft v0.1; launch scope, sharing, and creative workflow decisions remain open |
| [Source Audit](SOURCE_AUDIT.md) | Reference repository inventory and audit scope | Ongoing |
| [Foundation](FOUNDATION.md) | Initial product principles | Established foundation |
| [Architecture Decisions](ARCHITECTURE_DECISIONS.md) | Accepted constraints and unresolved choices | Maintained |
| [Engine Evaluation](ENGINE_EVALUATION.md) | Engine comparison and Android proof plan | Preliminary; no engine selected |
| [Cinematic Experience Blueprint](CINEMATIC_EXPERIENCE_BLUEPRINT.md) | First-open, travel, character reveals, sequence lifecycle and cinematic quality gates | Working draft strengthened; runtime and content authoring still require review |
| [Asset Handoff Standard](ASSET_HANDOFF_STANDARD.md) | Designer delivery, semantic IDs, animation and replacement rules | Working draft strengthened with validation and authoritative boundaries |
| [Asset and Cinematic Pipeline](ASSET_AND_CINEMATIC_PIPELINE.md) | Replaceable asset contracts and engine-neutral cinematic pipeline | Working draft strengthened with ownership, versioning and independent-pipeline rules |
| [Roadmap](ROADMAP.md) | High-level phases and exit gates | Pre-implementation |

## Work completed

### Product boundary and foundational direction

- [x] Confirm Language-world as the independent product.
- [x] Record GoPAL-AI as read-only reference material.
- [x] Record no-Expo constraint.
- [x] Reject reuse of the legacy 3D pipeline and its artifacts/tooling.
- [x] Establish Emerald Valley as home world, with genuinely distinct language worlds.
- [x] Establish Cassidy as a canonical human female character and emotional anchor, not the whole universe.
- [x] Record broad experiences beyond residents and dialogue: exploration, stories, mysteries, games, culture, creativity, and learning.
- [x] Record first-open introduction, cinematic travel, resident reveals, and replaceable placeholder assets.
- [x] Recover Cassidy's written visual canon, record conflicts, and create an independent character bible draft.
- [x] Recover Emerald Valley geography and Japanese/French world seeds; create an independent universe bible draft.
- [x] Inspect the 60-game research catalogue, game selection/session foundation, story threads, quest seed, event director, and activity primitives; record evidence limits.

### Reference recovery

- [x] Inspect major world, Cassidy, learning, narrative, memory, and language-world systems (selected files; not every source path).
- [x] Record object archetypes, placed objects, buildings, interiors, inventory, and crafting findings.
- [x] Record environment, time, weather, festivals, events, and offline simulation findings.
- [x] Record audio contracts, animation semantics, first-meeting cinematic, and no-Expo implications.
- [x] Inspect audio cue/mix contracts, profiles, playback adapter, semantic animation vocabulary, departure and first-meeting cinematic sources; record Expo and ownership limitations.
- [x] Record local persistence, account scoping, fallback, and cross-domain reliability findings.
- [x] Record creation studio, Memory Museum, Journey Book, time capsules, discovery progression, and transport infrastructure findings.
- [x] Inspect creation templates, archive screens, time capsule unlock flow, transcript archive truthfulness, and LocalStore object methods.

### Blueprint

- [x] Create central Master Blueprint structure.
- [x] Expand it with recovered requirements and supporting specification plan.
- [x] Add Cassidy Character Bible as the first detailed character specification.
- [x] Add World & Universe Bible as the universe/world authoring foundation.
- [x] Create Experience Catalogue working specification with all 60 ideas clearly marked as research seeds, not completed games.
- [x] Define experience families, learning relationship types, Cassidy participation boundaries, authoring contract, persistence classes, accessibility/safety, and quality gates.
- [x] Inspect contextual learning, capability tracking, adaptive conversation, response evaluation, scenario content, and multi-domain learning flow.
- [x] Create Learning Design working specification with separate evidence dimensions and explicit limits on speech/pronunciation claims.
- [x] Inspect legacy time, weather, resident routine, ambient event, NPC runtime, and actor simulation sources.
- [x] Create World Simulation working specification covering clock policy, climate, residents, ecology, plants, events, offline recovery, and performance tiers.
- [x] Inspect object schemas/catalogues/factories, entrances, interactions, personal-object storage, inventory helpers, and location contracts.
- [x] Create World Objects and Spaces working specification with explicit object lifecycle, state ownership, interior, and asset-replacement requirements.
- [x] Inspect local transport networks, vehicle loops, destination arrival scenes, and arrival timeline sources.
- [x] Create Travel Experience working specification with durable journey states, cinematic staging, arrival handoff, and recovery requirements.
- [x] Create Audio, Voice, and Soundscape working specification with world sound bibles, voice/audio integrity, captions, interruption, and delivery requirements.
- [x] Strengthen cinematic sequence lifecycle, track ownership, interruption/version migration, and quality gates.
- [x] Strengthen artist handoff and asset/cinematic pipeline documents with validation, authoritative boundaries, versioning, and independent-production constraints.
- [x] Inspect quest, resident story, clue investigation, story choice, event direction, and narrative trace sources.
- [x] Create Narrative and Story Continuity working specification with canon/knowledge ownership, fair mystery, resident autonomy, durable re-entry, and ethical quest requirements.
- [x] Create Creative Experiences and Personal Archive working specification with editable source, object lifecycle, privacy, media, AI boundaries, cultural integrity, and acceptance tests.
- [x] Link the Master Blueprint from README.
- [ ] Complete product-owner review and approval.

## Current reference-audit status

The Product Systems Audit currently contains 53 numbered sections. It is substantial but not complete. The current review is based on selected files from a complete repository tree inventory; it must not be described as a line-by-line audit of all source files or as proof that features work end-to-end.

Remaining high-value review areas include:
- Full source trace of transport and travel state, including interruption and re-entry.
- Full source trace of object memories, plant/personal-space lifecycle, and collection ownership.
- Detailed account lifecycle, anonymous mode, sign-out/account switching, sync and deletion behaviour.
- RLS policy completeness and security boundaries (schema declarations alone are not a security audit).
- Accessibility implementation evidence and reduced-motion/audio/subtitle behaviour.
- Content authoring and asset validation workflows, while explicitly excluding the legacy 3D pipeline from reuse.

## Supporting specification queue

Create and review in dependency order:

1. [x] `WORLD_UNIVERSE_BIBLE.md` — first working draft created; Emerald Valley/world canon still needs product-owner review and completion.
2. [x] `CASSIDY_CHARACTER_BIBLE.md` — first working draft created; canonical artwork and open questions require review.
3. [x] `EXPERIENCE_CATALOGUE.md` — working draft created; taxonomy and quality gates are defined, launch portfolio remains unapproved.
4. [x] `LEARNING_DESIGN.md` — working draft created; capability/evidence, adaptive support, assessment limits, speech honesty, privacy and accessibility defined.
5. [x] `WORLD_SIMULATION_SPEC.md` — working draft created; simulation domains and clock/offline decisions documented, world-specific profiles remain open.
6. [x] `WORLD_OBJECTS_AND_SPACES.md` — working draft created; spatial hierarchy, object lifecycle, interaction, interiors, inventory, and replaceable assets defined.
7. [~] `CINEMATIC_EXPERIENCE_BLUEPRINT.md` and `ASSET_AND_CINEMATIC_PIPELINE.md` were strengthened with sequence lifecycle, track ownership, recovery, version migration, and approval gates; full content/engine review remains.
8. [x] `TRAVEL_EXPERIENCE_SPEC.md` — working draft created; route graph, transport modes, durable journey states, arrival handoff, and interruption recovery defined.
9. [~] `ASSET_HANDOFF_STANDARD.md` and `ASSET_AND_CINEMATIC_PIPELINE.md` were reconciled at the boundary level; final importer/schema/engine-specific validation contract remains open.
10. [x] `AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md` — working draft created; world sound identity, mix, voice, learning audio integrity, captions, accessibility, interruption, and delivery defined.
11. [x] `NARRATIVE_AND_STORY_CONTINUITY_SPEC.md` — working draft created; canon, mysteries, choices, resident autonomy, quests, journal/re-entry and durable events defined.
12. [x] `PERSISTENCE_PRIVACY_AND_SYNC.md` — working draft created; identity, local-first behaviour, sync, security, privacy, export, deletion and recovery defined.
13. [x] `CREATIVE_EXPERIENCES_AND_PERSONAL_ARCHIVE.md` — working draft created; archive families, editable source, media lifecycle, ownership, privacy, cultural review and acceptance tests defined.
14. [ ] `TECHNICAL_ARCHITECTURE.md` — domain boundaries, runtime, data, engine evaluation and integration contracts.
15. [ ] `PRODUCTION_AND_QUALITY_PLAN.md` — production roles, content workflows, acceptance criteria, testing and release gates.

## Open decisions register

These are intentionally unresolved; do not invent answers.

- [ ] Primary audience, age range, age policy, and supported proficiency levels.
- [ ] First target Android device(s) and minimum supported device class.
- [ ] Online/offline product promise and account model.
- [ ] Single-player versus optional connected/social experiences.
- [ ] First language worlds and launch scope.
- [ ] First release experience scope and content volume.
- [ ] Engine choice after representative device testing.
- [ ] Backend, sync, voice, speech recognition, and privacy architecture.
- [ ] Cultural review model and language-quality assurance process.
- [ ] Accessibility requirements and test methodology.
- [ ] Production capacity, team roles, content budget, and release expectations.

## Approval gates

### Gate A — Product definition
- [ ] Complete product vision and audience.
- [ ] Universe structure and world identity rules.
- [ ] Cassidy and character canon.
- [ ] Experience catalogue and learning philosophy.
- [ ] Scope and safety boundaries.

### Gate B — System specifications
- [ ] World simulation, objects/spaces, narrative, travel, and cinematics (working specifications exist; full review and approval remain).
- [ ] Asset/creative pipeline and audio (working drafts exist; require final review and scope approval).
- [ ] Persistence, privacy, accounts, sync, and offline.
- [ ] UX and accessibility.
- [ ] Acceptance criteria and traceability.

### Gate C — Technical evidence
- [ ] Engine comparison updated with current evidence.
- [ ] Representative Android prototype plan agreed.
- [ ] Target device(s) agreed.
- [ ] Performance and reliability budgets defined.
- [ ] No legacy pipeline dependency.

### Gate D — Product-owner approval
- [ ] Full document set reviewed.
- [ ] Open decisions resolved or explicitly deferred.
- [ ] Contradictions and dependencies checked.
- [ ] Product owner explicitly approves the blueprint for implementation.

**Current state: Gate A is being designed. Gates B–D are not complete. No implementation work should begin.**
