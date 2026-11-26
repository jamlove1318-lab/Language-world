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
| [Product Systems Audit](PRODUCT_SYSTEMS_AUDIT.md) | Evidence and limitations from selected reference files | Sections 1–44; ongoing |
| [Archive Gap Audit](GOPAL_ARCHIVE_TO_LANGUAGE_WORLD_GAP_AUDIT.md) | Recovered product concepts and new-product gaps | Working research document |
| [Cassidy Character Bible](CASSIDY_CHARACTER_BIBLE.md) | Independent Language-world character canon and production direction | Working draft v0.1; review required |
| [World & Universe Bible](WORLD_UNIVERSE_BIBLE.md) | Universe hierarchy, Emerald Valley, distinct world standards and registry | Working draft v0.1; world canon incomplete |
| [Experience Catalogue](EXPERIENCE_CATALOGUE.md) | Experience taxonomy, 60 research seeds, learning integration, authoring and quality gates | Working draft v0.1; portfolio and scope require review |
| [Source Audit](SOURCE_AUDIT.md) | Reference repository inventory and audit scope | Ongoing |
| [Foundation](FOUNDATION.md) | Initial product principles | Established foundation |
| [Architecture Decisions](ARCHITECTURE_DECISIONS.md) | Accepted constraints and unresolved choices | Maintained |
| [Engine Evaluation](ENGINE_EVALUATION.md) | Engine comparison and Android proof plan | Preliminary; no engine selected |
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
- [x] Record local persistence, account scoping, fallback, and cross-domain reliability findings.
- [x] Record creation studio, Memory Museum, Journey Book, time capsules, discovery progression, and transport infrastructure findings.

### Blueprint

- [x] Create central Master Blueprint structure.
- [x] Expand it with recovered requirements and supporting specification plan.
- [x] Add Cassidy Character Bible as the first detailed character specification.
- [x] Add World & Universe Bible as the universe/world authoring foundation.
- [x] Create Experience Catalogue working specification with all 60 ideas clearly marked as research seeds, not completed games.
- [x] Define experience families, learning relationship types, Cassidy participation boundaries, authoring contract, persistence classes, accessibility/safety, and quality gates.
- [x] Link the Master Blueprint from README.
- [ ] Complete product-owner review and approval.

## Current reference-audit status

The Product Systems Audit currently contains 45 numbered sections. It is substantial but not complete. The current review is based on selected files from a complete repository tree inventory; it must not be described as a line-by-line audit of all source files or as proof that features work end-to-end.

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
4. [ ] `LEARNING_DESIGN.md` — skills, evidence, practice, adaptive support, assessment, speech capability claims.
5. [ ] `WORLD_SIMULATION_SPEC.md` — canonical clock, weather, seasons, ecology, schedules, events, offline tiers.
6. [ ] `WORLD_OBJECTS_AND_SPACES.md` — object contracts, buildings, interiors, navigation, interaction, inventory and lifecycle.
7. [ ] `CINEMATIC_EXPERIENCE_SYSTEM.md` — timelines, camera, actor direction, voice, sound, accessibility, preload and recovery.
8. [ ] `TRAVEL_EXPERIENCE_SPEC.md` — routes, transport modes, staging, boarding, journeys, arrival, handoff and interruption.
9. [ ] `ASSET_AND_CREATIVE_PIPELINE.md` — semantic IDs, manifests, versioning, replacement, rigs, animation, provenance and designer handoff.
10. [ ] `AUDIO_EXPERIENCE_SPEC.md` — acoustic identity, mixing, spatial behaviour, playback boundary and accessibility.
11. [ ] `PERSISTENCE_PRIVACY_AND_SYNC.md` — identity, local-first behaviour, sync, security, privacy, export, deletion and recovery.
12. [ ] `TECHNICAL_ARCHITECTURE.md` — domain boundaries, runtime, data, engine evaluation and integration contracts.
13. [ ] `PRODUCTION_AND_QUALITY_PLAN.md` — production roles, content workflows, acceptance criteria, testing and release gates.

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
- [ ] World simulation, objects/spaces, narrative, travel, and cinematics.
- [ ] Asset/creative pipeline and audio.
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
