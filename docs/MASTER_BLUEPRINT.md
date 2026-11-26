# Language-world — Master Blueprint

**Document status:** Working draft v0.3 — expanded after further reference review; research and design in progress; not approved for implementation  
**Project:** Language-world  
**Reference archive:** `jamlove1318-lab/GoPAL-AI` (read-only)  
**Destination:** `jamlove1318-lab/Language-world`  
**Purpose:** Define the complete product we intend to create before implementation begins.

---

## 0. How to use this blueprint

This is the central product and system-design document for Language-world. It is not a claim that every design decision has been made. It consolidates the established vision, recovered ideas, explicit constraints, and the questions that must be resolved before development.

Detailed specifications will live in supporting documents and be linked from here. This document owns the overall coherence: every supporting specification must agree with the product principles and with the other systems.

### Evidence labels

- **Established:** Explicitly stated by the product owner or already accepted in the project.
- **Recovered concept:** A useful idea found in the GoPAL-AI reference archive; it must be independently redesigned.
- **Proposed:** A design direction worth evaluating, not yet a final commitment.
- **Open decision:** Requires research, comparison, testing, or product-owner approval.
- **Unverified:** Suggested by source material but not proven to work end-to-end.

### Non-negotiable project boundary

GoPAL-AI is a read-only reference archive. It may be inspected for ideas, specifications, character canon, creative material, implementation lessons, and evidence of limitations. It must never be modified as part of this project. Language-world is independently designed and implemented. Do not copy the old application wholesale, port its code, or reuse its rejected 3D pipeline, tools, exporters, scripts, models, rigs, animations, or pipeline-specific contracts.

No application implementation begins until the Master Blueprint and its required supporting specifications have been reviewed and explicitly approved.

---

# Part I — Product identity

## 1. Product definition

**Established:** Language-world is a living, explorable universe in which language learning is woven into meaningful participation in different places and experiences.

It is not a conventional course, dashboard, chatbot, collection of lesson cards, or 3D environment used merely as decoration. The world itself is the primary experience. People should be able to explore, discover, play, create, listen, speak, investigate, meet characters, follow stories, and learn through what they do.

The product must remain worthwhile even when the learner is not completing a lesson, speaking to Cassidy, or interacting with a resident. It should feel like a place with its own identity, atmosphere, activities, history, and continuity.

### 1.1 Intended emotional experience

The product should encourage:
- Curiosity: there is always something worth noticing or discovering.
- Belonging: familiar places and characters create a sense of return.
- Agency: learners choose what to explore and how to participate.
- Wonder: the universe contains surprises, secrets, stories, and unexpected events.
- Progress through capability: learners notice that they can understand and express more.
- Continuity: places, objects, stories, and relationships can remember meaningful events.
- Calm enjoyment: the experience does not punish absence or manufacture urgency.

Avoid guilt-driven streaks, manipulative emotional dependency, artificial scarcity, relentless reward loops, and progression systems that replace meaningful experiences.

## 2. Product principles

1. **World first, interface second.** Menus support the experience; they are not the experience.
2. **Learning through meaningful activity.** Language is used to understand, decide, communicate, create, and participate.
3. **A universe larger than any one character.** Cassidy is central, but the world has independent stories, places, systems, and inhabitants.
4. **Distinct worlds, not reskins.** Each language world needs its own coherent identity.
5. **Continuity with boundaries.** Remember useful events and preferences transparently, with user control and privacy.
6. **Player agency.** Offer invitations and possibilities without coercion.
7. **Authored meaning plus systemic life.** Handcrafted stories and cinematic moments coexist with believable world behaviour.
8. **Temporary assets, durable architecture.** Placeholder art is acceptable; disposable technical foundations are not.
9. **Accessibility from the design stage.** Motion, audio, text, input, and cognitive accessibility are first-class requirements.
10. **Evidence before commitment.** Engine, backend, and performance decisions require representative tests.

## 3. Audience, use context, and product boundaries

**Open decisions:** Define primary learner groups, age policy, supported proficiency ranges, accessibility needs, expected session lengths, online/offline expectations, supported platforms beyond the initial Android target, and whether the product is single-player, connected, or selectively social.

These decisions affect safety, privacy, content, architecture, moderation, account design, and production scope. They must be resolved before implementation.

---

# Part II — The universe

## 4. Universe structure and canon

**Established:** Emerald Valley is the home world, not the entire universe. Different languages correspond to distinct worlds with their own geographies and identities. The Spanish world, for example, is not simply a Spanish-themed district inside Emerald Valley.

The universe specification must define:
- The overall cosmology and world-to-world relationship.
- How travel between worlds works and what makes it possible.
- The history, geography, major locations, and defining mysteries of each world.
- Shared universe rules versus world-specific rules.
- Cultural representation principles and research standards.
- How new worlds can be added without flattening their differences.
- Canon ownership, naming, continuity, and change control.

**Proposed:** Maintain a canonical world registry and an individual World Bible for every world. The registry defines identity and cross-world metadata; each World Bible defines the authored place in depth.

## 5. Emerald Valley — the home world

Emerald Valley is the learner's first home and the introduction to the wider universe. It should feel like a real, memorable place rather than a tutorial hub.

Recovered location concepts include Mount Emerald, forest and treeline regions, streams, paths, a café, market, library, station, sanctuary, garden, and hidden routes or spaces. These are starting references, not a final map or a restriction on new ideas.

Its specification must cover:
- A readable geographical layout and navigational landmarks.
- Districts, routes, interiors, secret places, and points of interest.
- Daily life, resident routines, wildlife, and local events.
- Activities available without requiring Cassidy or a resident.
- Local stories, mysteries, games, learning opportunities, and discoveries.
- The transport station and the first journey to another world.
- Day/night, weather, seasonal, and audio identity.
- A guided first-visit route that teaches through experience rather than a long menu tutorial.

## 6. Other language worlds

Every world requires a complete identity brief before production. At minimum:
- Language and cultural scope, with clear distinction between language and nationality.
- Geography, climate, ecology, architecture, materials, settlements, and landmarks.
- History, local stories, mysteries, festivals, everyday rhythms, and social life.
- Resident communities, character roles, wildlife, and creatures.
- Food, music, soundscape, transport, objects, and environmental details.
- Language-learning contexts grounded in the world.
- Unique activities and experiences that could not be copied unchanged into another world.
- Travel links and arrival experience.
- Cultural consultation, accuracy review, and sensitivity process.

No world should be approved as a mere palette, asset, or vocabulary reskin.

---

# Part III — People and life

## 7. Cassidy — the central human character

**Established:** Cassidy is a human female character. She is not a fox, animal, mascot, or anthropomorphic creature. Her existing canonical design and character details in the reference archive are creative reference material; the new implementation must be independent.

Cassidy is the emotional heart and a distinctive companion within a much larger universe. She has her own interests, routines, stories, discoveries, friendships, commitments, and moments when she is not present with the learner.

The new design must define:
- Canonical identity, appearance, voice, history, values, humour, boundaries, and characterization.
- Motivations, needs, interests, goals, plans, and commitments.
- Perception of the environment and relevant learner context.
- Physical embodiment: movement, navigation, gaze, gestures, expressions, posture, and interaction.
- Dialogue, language adaptation, voice, and conversational limits.
- Memory: what can be remembered, why, for how long, with what provenance and user controls.
- Relationship development through meaningful shared experiences, not a simple affection score.
- Independent life simulation, including appropriate absence, quiet time, and offline boundaries.
- Narrative continuity and how authored scenes connect to her ongoing life.

Her autonomy must never imply surveillance, emotional pressure, or punishment for a learner's absence.

## 8. Residents, communities, and creatures

Residents are not interchangeable quest-givers or decorative NPCs. The design should establish believable communities with roles, routines, interests, relationships, local knowledge, and changing circumstances.

Creature and wildlife design must be world-specific. Define species, habitats, ecological roles, needs, rhythms, behaviours, communication, signs of presence, and how learners may observe or interact with them. Not every creature should be collectible, hostile, or a generic enemy.

The specification must distinguish:
- Authored named characters from systemic background population.
- Resident schedules from moment-to-moment animation.
- Friendly, neutral, helpful, guardian, dangerous, and other behaviours where appropriate.
- Creature ecology from combat or collection mechanics.
- Persistent narrative characters from temporary scene actors.

---

# Part IV — What people can experience

## 9. Experience catalogue

Language-world must support a broad catalogue of independent and connected experiences. The recovered GoPAL-AI catalogue includes concepts across discovery, search, puzzles, building, reflex and arcade games, social communication, listening, stories, adventures, and creative construction. These are idea sources, not a commitment to ship every concept.

The new catalogue should evaluate:
- Exploration and environmental discovery.
- Stories at micro, local, character, seasonal, and world-arc scales.
- Mysteries, clues, rumours, evidence, investigations, and satisfying resolutions.
- Mini-games, puzzles, strategy, reflex, building, and cooperative activities if approved.
- Cultural experiences, everyday activities, celebrations, and festivals.
- Creative tools such as postcards, phrase cards, memory boards, comics, collections, museums, and personal journals.
- Photography or capture-like experiences where supported and privacy-safe.
- Collection, inventory, crafting, personal spaces, and object histories if they add meaningful play.
- Activities that are available independently of Cassidy and residents.

Every experience must specify its purpose, core loop, entry points, player choices, language role, accessibility, state changes, persistence, replayability, failure/recovery behaviour, and content production cost.

## 10. Learning design

Learning should be contextual and purposeful rather than hidden behind a world-themed worksheet. Learners should encounter language because it helps them understand a situation, communicate, make a choice, solve a problem, or create something.

The learning specification must separately define:
- Listening comprehension.
- Reading comprehension.
- Vocabulary and phrase acquisition.
- Grammar and patterns in context.
- Speaking and conversational interaction.
- Writing and composition.
- Pronunciation and phonological awareness.
- Recall, review, spaced practice, and long-term retention.
- Adaptive assistance, hints, scaffolding, and difficulty.
- Assessment, confidence, uncertainty, and evidence of capability.

Do not claim a capability that the implementation cannot measure. Distinguish audio playback, shadowing, microphone capture, transcription, speech recognition, and measured pronunciation feedback. Define how attempts, responses, hints, confidence, skill dimensions, and recall evidence are recorded independently.

Learning should complement exploration and stories, not turn every activity into a test.

## 11. Stories, quests, mysteries, and continuity

Define a coherent narrative model for authored scenes and systemic stories. Include:
- Story scales, arcs, chapters, scenes, and optional side stories.
- Quest objectives, dependencies, choices, consequences, and completion rules.
- Clue/evidence provenance and investigation state.
- Rumours, partial information, misleading clues, and fair resolution.
- Character-specific stories and world-wide events.
- Re-entry after interruption and the ability to understand what happened.
- Replay, branching, and canon consequences.
- A durable story journal or equivalent where it helps rather than overwhelms.

The story system must not depend on volatile in-memory state or random IDs that make continuity unreliable.

## 12. Creative work and personal archive

Learners may create or keep meaningful artefacts: postcards, phrase collections, journals, memory boards, comics, discoveries, and other formats chosen after product design.

Define ownership, edit/reopen, delete, export, media lifecycle, storage limits, account scope, sync, privacy, backup, and accessibility. Personal records must be scoped to the correct learner/account. Time-locked experiences must have explicit rules for device clock changes, offline use, and early unlock policy.

---

# Part V — The living world

## 13. World simulation

Specify the simulation clock, local time zones, day/night, weather, seasons, festivals, resident schedules, ecology, world events, and ambient changes.

For every simulated system define:
- Authoritative time source and offline behaviour.
- Whether it is deterministic, seeded, scheduled, or server-authoritative.
- What is simulated continuously versus derived when the learner returns.
- Pause, background, sleep, and resume rules.
- Device-clock manipulation handling.
- Bounded offline simulation and performance budgets.
- Accessibility and user settings, including reduced stimulation where appropriate.

Avoid simulating every entity every frame. Use bounded, purposeful simulation with clear state ownership.

## 14. Objects, spaces, inventory, and interaction

Define a common interaction model for doors, furniture, tools, signs, plants, collectibles, clues, vehicles, and other objects. Specify object identity, state, ownership, provenance, persistence, interaction affordances, and reset rules.

Buildings and interiors should be designed as navigable spaces with meaningful functions, not just visual shells. Personal spaces and collections need privacy and durable ownership rules.

---

# Part VI — Travel and cinematic direction

## 15. Cinematic Experience System

Cinematics are a core presentation capability, not one-off animations buried in individual screens.

The system must support:
- Authored timelines and beats.
- Camera choreography and transitions.
- Actor blocking, movement, gestures, gaze, expressions, and animation.
- Dialogue, subtitles, voice, music, ambience, and sound effects.
- Environment, weather, lighting, and world-state cues.
- Preloading, streaming, checkpoints, and asset readiness.
- Skip, replay, pause, interruption, resume, and recovery.
- Reduced-motion and accessible alternatives.
- Localization and timing changes.
- Consistent handoff into playable control.

Cinematic presentation must not own the persistent game or world state. It presents a transition or event whose durable state is managed by the appropriate domain system.

## 16. First-open introduction

The first app experience should introduce Cassidy and the universe through a thoughtfully staged sequence. Cassidy introduces herself, guides the learner through Emerald Valley, establishes it as the home world, reveals what can be experienced there, and explains how journeys to other worlds work.

This should feel like an invitation into a place, not a conventional feature tour. The complete script, staging, camera, dialogue, audio, pacing, interaction points, skip/replay policy, and return path remain to be authored.

## 17. Travel Director and world-to-world journeys

World travel is a durable multi-stage experience:
1. Decide to travel and select/earn access according to the designed world rules.
2. Reach the correct station, terminal, port, or departure location.
3. Prepare and board the chosen transport.
4. Stage departure and transition into the journey.
5. Present the journey itself, with optional meaningful interactions.
6. Cross the world boundary and prepare the destination.
7. Arrive, disembark, and reveal the new world.
8. Hand control to the destination world in a consistent state.

The first example to design is a train journey from Emerald Valley to the Spanish world, including station, boarding, departure, travel, arrival, and destination reveal. Planes and other transport may serve longer journeys; cars, buses, boats, and other local transport should have appropriate world-specific roles and experiences.

Travel state must survive interruption, app closure, and relaunch. A cinematic cannot be the only record that a journey happened.

## 18. Character and resident reveals

Important character introductions should use anticipation, environmental hints, sound, staging, point of view, and a meaningful reveal before direct interaction. Not every encounter needs a long cinematic; the system must support short, medium, and major presentation scales.

---

# Part VII — Interface, technology, and production

## 19. User experience and accessibility

Design the complete user journey: first launch, onboarding, world entry, navigation, discovery, activity entry/exit, travel, settings, help, account, privacy, and returning after absence.

Specify interaction patterns for touch, controller/keyboard if relevant, text size, captions, transcripts, audio controls, colour and contrast, motion sensitivity, cognitive load, localization, and low-connectivity use. The interface must support the world without constantly pulling the learner out of it.

## 20. Technical architecture

**Established constraints:** No Expo. No reuse of the legacy GoPAL 3D pipeline. No engine has been selected.

The architecture must be designed around clear ownership and boundaries for:
- World and scene lifecycle.
- Characters and embodied runtime.
- World simulation and ecology.
- Narrative, quests, clues, and event continuity.
- Learning and capability evidence.
- Memory, relationships, and personal archive.
- Interaction, objects, inventory, and spaces.
- Cinematics and travel.
- Audio, accessibility, localization, and UI.
- Save data, accounts, synchronization, offline operation, privacy, and security.
- Asset registry, streaming, loading, and performance.

Persistent records require explicit learner/account scope. Cross-system effects need durable event handling, stable identifiers, idempotency, retry and recovery rules, and clear transaction boundaries. Avoid hidden cross-store mutation and fragmented sources of truth.

### 20.1 Engine decision

Godot, Unity, Unreal, and any relevant alternatives remain candidates until representative Android prototypes are measured. The comparison must cover character animation, cinematics, world streaming, tooling, asset workflows, developer productivity, licensing, package size, device compatibility, performance, and long-term maintenance.

No selection based only on reputation, screenshots, or a simple demo.

### 20.2 Android proof

The eventual representative prototype should include an outdoor environment and an interior, a new human placeholder character, animation and expression, interactive objects with persisted changes, a short story choice, a small game, layered audio, quiet mode, interruption recovery, and replacement of placeholder assets without changing gameplay.

Measure average, p95, and worst frame time; dropped frames; CPU/GPU; thermal behaviour over 20–30 minutes; memory; package and update size; startup and transition times; battery impact; audio interruption; crashes/driver issues; and save recovery on the agreed target devices.

## 21. Asset and creative production system

Temporary assets are allowed and expected during early validation. High-quality final art is not a prerequisite for proving architecture. The asset system must make later replacement predictable and safe.

Define:
- Stable semantic asset IDs independent of filenames and engine object paths.
- Asset manifests, versions, checksums, provenance, and licensing.
- Character rig/skeleton compatibility and animation/action semantics.
- Scale, units, orientation, pivots, collision, interaction targets, and material rules.
- LOD and performance tiers, variants, fallback assets, and loading behaviour.
- Validation and designer handoff requirements.
- Replacement tests on Android before content is scaled up.

Gameplay and story systems reference semantic identities and events, not artist export folders, filenames, renderer nodes, or prefab paths.

The new workflow must be independent. Do not reuse the GoPAL 3D renderer/runtime, models, meshes, rigs, animations, Blender scripts, asset factories, validators, converters, exporters, or pipeline-specific manifests and registries.

## 22. Audio, voice, and presentation

Define a coherent audio system for dialogue, narration, music, ambience, environmental effects, UI, and cinematic cues. Include mixing priorities, spatial audio decisions, dynamic transitions, subtitles/transcripts, volume controls, quiet mode, device interruption, localization, voice production, and licensing.

The final audio backend is an engine-dependent decision and must be tested on Android.

## 23. Data, privacy, safety, and reliability

Specify account identity, local-first behaviour, sync, conflict resolution, backup, deletion, export, retention, consent, analytics, telemetry, and recovery. Define what is stored, why it is stored, who can access it, and how the learner can inspect or control it.

Memory and personalization must be transparent, scoped, useful, and proportionate. Establish age and safety requirements before selecting social features, voice features, or user-generated content policies.

---

# Part VIII — Production and approval

## 24. Content production and world-authoring standards

Define repeatable pipelines for writing, world design, character design, cultural review, modelling, rigging, animation, audio, localization, testing, and release. Every content package must have clear owners, acceptance criteria, dependencies, and compatibility requirements.

Worlds and experiences should be authorable without requiring changes to core runtime code for every new location or story. The correct balance between data-driven content and bespoke authored behaviour must be tested.

## 25. Development roadmap and release gates

The implementation roadmap will be produced only after the product and technical specifications are coherent. It will identify dependencies, vertical slices, milestones, risk, team roles, test strategy, and measurable exit criteria.

Expected gates:
1. Product vision and universe approved.
2. World, character, experience, and learning specifications approved.
3. Cinematic, travel, asset, and production specifications approved.
4. Architecture, privacy, persistence, and engine decision supported by evidence.
5. Representative Android prototype passes agreed acceptance criteria.
6. First complete experience is validated end-to-end.
7. Content expansion and release readiness are approved.

A phase is not complete because code exists; it is complete when its acceptance criteria pass.

## 26. Blueprint governance

Maintain:
- A decision log with rationale and alternatives.
- An open-question and risk register.
- A traceability map from product goals to systems, requirements, and tests.
- A glossary and canonical naming registry.
- A source-evidence register separating reference findings from new design decisions.
- Version history and explicit approval status.

Changes that affect canon, user experience, architecture, privacy, or scope must be recorded and checked against dependent chapters.

---

# Current established decisions

- Language-world is a new, independent product.
- GoPAL-AI remains read-only reference material.
- No Expo.
- No reuse of the legacy GoPAL 3D pipeline or its artifacts/tooling.
- Emerald Valley is the home world, not the whole universe.
- Other language worlds must have genuinely distinct identities.
- Cassidy is a human female character and the emotional heart, not the entire product.
- The product includes experiences beyond residents and conversation: exploration, stories, mysteries, games, creativity, culture, and learning.
- First-open introduction and cinematic world travel are important experiences.
- Temporary assets are acceptable if final assets can replace them through stable contracts.
- Engine selection remains open and must be evidence-led.
- No application implementation before blueprint approval.

# Work still required before this blueprint can be approved

1. Reconcile the existing Master Blueprint and supporting specifications; see BLUEPRINT_RECONCILIATION.md.
2. Complete the engine-neutral Technical Architecture, UX/accessibility/navigation, AI/voice governance, product scope, and production/quality specifications.
3. Resolve or explicitly defer audience/age policy, first-release scope, language/world scope, account/offline promise, engine/backend/service choices, progression/monetization, and operational model.
4. Complete and approve the Emerald Valley and first destination world bibles; approve Cassidy canon and performance boundaries.
5. Author a small, coherent first-release experience portfolio with complete user journeys and acceptance criteria.
6. Cross-check domain ownership, persistence, events, time, content, accessibility, privacy, security, performance, and failure recovery across all documents.
7. Present the complete blueprint package for product-owner review and explicit approval.

GoPAL-AI idea recovery is now sufficiently broad for product-idea transfer. Further source checks should answer specific unresolved questions; no legacy assets or production pipeline need to be inspected.

**Current approval state: NOT APPROVED FOR IMPLEMENTATION.** This is the foundation draft. Its purpose is to make the next design work structured and traceable, not to pretend the universe is already fully specified.

---

# Part IX — Newly recovered design requirements

## 27. Objects, buildings, interiors, and the physical world

The reference review identifies a useful distinction between an object archetype and a placed object instance. Language-world must make this distinction explicit.

### 27.1 Object identity and lifecycle

Every authored object should be defined through:
- A stable semantic identity and object family.
- An archetype describing capabilities and constraints.
- A world instance with placement, transform, and contextual overrides.
- Optional visual, audio, collision, navigation, and interaction bindings.
- State, ownership, provenance, and lifecycle rules.
- Version compatibility and migration behaviour.

A visual asset is not the object identity. A door remains the same semantic door even if its model, material, animation, or engine implementation changes.

### 27.2 Buildings and interiors

Buildings must be treated as functional places. Their design needs to cover entrances, exits, interior topology, room-to-room navigation, occlusion, lighting, acoustic identity, interaction anchors, accessibility, loading/streaming, and save/re-entry behaviour.

The design should distinguish:
- A building's exterior identity and world placement.
- Its interior layout and room identities.
- Portals and transitions between exterior and interior spaces.
- Persistent state of doors, furniture, objects, and activities.
- Instanced or private spaces versus shared world spaces, if both are required.

### 27.3 Inventory, collections, and crafting

These are optional product systems, not automatic requirements. Each must have a clear experience purpose. Where included, define unique item identity, stackability, quantity, ownership, provenance, discovery context, durability, transfer rules, recipe requirements, consumption, output, rollback, and persistence.

Avoid adding inventory friction to experiences that are better served by direct interaction or a personal archive.

## 28. Canonical world simulation and event continuity

### 28.1 Separate kinds of time

The design must not treat all clocks as interchangeable. Specify:
- Real-world UTC time for durable timestamps and cross-device ordering.
- Learner-local time for local routines and presentation, with explicit timezone-change policy.
- Authored world time for fictional calendars, festivals, and story chronology.
- Simulation time for bounded world advancement.
- Cinematic/presentation time for authored pacing and playback.

The authoritative clock for each domain must be named. Device wall-clock changes must not corrupt durable ordering or unlock rules.

### 28.2 Simulation tiers

Use bounded simulation rather than continuously simulating every entity:
- **Active scene:** detailed interaction, movement, animation, and local events.
- **Nearby region:** simplified movement, schedules, and local state changes.
- **Distant world:** coarse schedules, event outcomes, and authored state transitions.
- **Offline/hibernating:** bounded, deterministic or reproducible advancement only where required.

Every tier needs a defined update budget, transition rule, persistence policy, and resume behaviour.

### 28.3 Durable world events

Events that affect persistent state require stable identity, source/causal references, timestamps, schema version, idempotency, deduplication, and replay/recovery rules. In-memory event delivery may support immediate presentation, but cannot be the sole record of a consequential event.

An orchestration director may select and coordinate opportunities; authoritative ownership remains with the domain that owns the quest, festival, learning evidence, inventory, relationship, or world object.

## 29. Audio, animation, and cinematic production requirements

### 29.1 Audio

The product requires semantic audio categories, location/world acoustic profiles, adaptive mixing, priority and ducking, concurrency limits, cooldowns, spatial attenuation, transitions, quiet mode, user controls, and an engine-specific playback adapter. Exact mix values are tuning data, not product canon.

Every audio asset requires provenance, licensing, technical metadata, optimization, device validation, and human listening approval.

### 29.2 Animation and character performance

Character behaviour should issue semantic performance intent—such as locomotion, posture, gaze, expression, gesture, listening, speaking, and interaction. Art assets and animation clips implement those intents through replaceable bindings.

Define rig/skeleton compatibility, retargeting, blend rules, layered performance, locomotion integration, fallback actions, and performance tiers. Gameplay must not depend on clip filenames or a specific authoring tool.

### 29.3 Cinematic system requirements

The Cinematic Experience System must be reusable across first introductions, resident reveals, stories, discoveries, festivals, and travel. A cinematic specification includes timeline beats, camera direction, actor blocking, semantic animation, dialogue, localization, voice, subtitles, music, ambience, lighting, asset preloading, checkpoints, skip/replay, interruption, recovery, and handoff to interactive control.

Cinematic playback is presentation. Persistent world, story, and travel state belongs to their respective domains.

## 30. Persistence, identity, privacy, and reliable side effects

### 30.1 Learner-scoped data

Every personal record, cache, offline queue, creation, learning result, relationship record, and world-state record must be scoped to a stable learner/account identity. Anonymous mode and later account linking require an explicit migration policy.

### 30.2 Local-first and synchronization policy

Specify which domains can operate offline, which actions require a server, how writes are queued, how conflicts are resolved, how retries are performed, and how duplicate operations are prevented. Account switching must never expose one learner's local records to another.

### 30.3 Cross-domain consistency

When one experience affects several domains—for example, a festival creating a memory, a personal artefact, a learning outcome, and a world-state change—define the durable operation and recovery behaviour. Partial failure must be visible and recoverable, not silently treated as full success.

### 30.4 Trust and privacy

Define data minimization, purpose, consent, retention, export, deletion, backup, security boundaries, and auditability. Row-level security is one layer, not proof of end-to-end security. Local storage, offline fallback, sync, logs, analytics, and deletion paths require the same scrutiny.

---

# Part X — Supporting specification set

The Master Blueprint remains the central index. These supporting documents will carry the detail needed for implementation and production. They should be created and reviewed in dependency order, not all at once.

| Supporting specification | Primary blueprint chapters | Required outcome |
|---|---|---|
| `WORLD_UNIVERSE_BIBLE.md` | 4–6 | Canon, world registry, Emerald Valley, distinct world bibles and travel geography |
| `CASSIDY_CHARACTER_BIBLE.md` | 7 | Canonical identity, personality, boundaries, voice, life, memory and relationship |
| `EXPERIENCE_CATALOGUE.md` | 9–12 | Complete experience inventory, loops, dependencies, accessibility and content costs |
| `LEARNING_DESIGN.md` | 10 | Capability model, skill evidence, practice, feedback, assessment and honest speech claims |
| `WORLD_SIMULATION_SPEC.md` | 13–14, 28 | Clock, weather, ecology, schedules, events, offline tiers and durable continuity |
| `WORLD_OBJECTS_AND_SPACES.md` | 14, 27 | Object contracts, buildings, interiors, navigation, interaction, inventory and lifecycle |
| [`CINEMATIC_EXPERIENCE_BLUEPRINT.md`](CINEMATIC_EXPERIENCE_BLUEPRINT.md) | 15–18, 29 | Timeline, camera, actors, staging, audio, accessibility, preloading and recovery |
| `TRAVEL_EXPERIENCE_SPEC.md` | 17 | Transport modes, routes, staging, journey state, arrival and handoff |
| [`ASSET_AND_CINEMATIC_PIPELINE.md`](ASSET_AND_CINEMATIC_PIPELINE.md) | 21, 29 | Semantic asset IDs, manifests, replacement, rigs, animation, provenance and designer handoff |
| [`AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md`](AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md) | 22, 29 | Audio identity, mixing, spatial behaviour, playback boundary and accessibility |
| `PERSISTENCE_PRIVACY_AND_SYNC.md` | 23, 30 | Identity, storage, offline, sync, security, privacy, export, deletion and recovery |
| [`TECHNICAL_ARCHITECTURE.md`](TECHNICAL_ARCHITECTURE.md) | 20 | Domain boundaries, engine evaluation, runtime, data and integration contracts |
| `PRODUCTION_AND_QUALITY_PLAN.md` | 24–26 | Roles, pipelines, acceptance criteria, test strategy, milestones and release gates |

Supporting specifications must link back to the relevant blueprint chapters, use the evidence labels defined in Section 0, and record open decisions. They must not silently turn a proposal into an accepted product decision.

---

# Part XI — Current research status

## 31. Reference review coverage

The GoPAL-AI product-idea recovery is consolidated in [GOPAL_IDEA_RECOVERY_AUDIT.md](GOPAL_IDEA_RECOVERY_AUDIT.md). The repository tree inventory was complete for the inspected main-branch snapshot; selected source review is broad but not line-by-line or runtime verification. The user's transfer rule is ideas only: no GoPAL-AI code, assets, media, or production pipeline are to be transferred or inspected for reuse.

Additional selected-file review has expanded the product systems audit through:
- World object archetypes, instances, buildings, interiors, object state, inventory, and crafting.
- Environment/time models, simulation snapshots, events, festivals, and offline behaviour.
- Semantic audio, location profiles, animation intent, resident performance sequences, and a first-meeting cinematic.
- Supabase schema/RLS declarations, local storage, memory fallback, account scoping, and multi-domain side effects.
- Personal creations, Memory Museum, Journey Book, time capsules, unlock policy, and archive ownership.
- Discovery progression, canonical place IDs, transport infrastructure, and the distinction between map routes and durable travel journeys.

The findings and source limitations are recorded in `PRODUCT_SYSTEMS_AUDIT.md`. The audit is still ongoing: selected source inspection does not prove full integration, correctness, security, or end-to-end behaviour.

## 32. Immediate blueprint work order

1. Complete the document reconciliation and technical architecture.
2. Specify end-to-end user journeys, navigation, accessibility, and re-entry.
3. Define audience, age policy, first-release scope, AI/voice governance, and progression/monetization boundaries.
4. Complete actual world canon and approve Cassidy's character canon.
5. Define production, quality, security, privacy, operations, and release gates.
6. Run a full contradiction/dependency/acceptance-criteria pass across the document set.
7. Present the complete package for product-owner review and explicit approval.

Further GoPAL-AI research is now question-led rather than an open-ended audit. The user has explicitly limited transfer to ideas only; old assets and pipeline are out of scope.

**Implementation remains blocked until the Master Blueprint and its required supporting specifications are approved.**
 
## 33. Additional personal-history and travel design implications

The additional archive review makes four requirements explicit:

1. **Personal archive as an owned product capability.** Postcards, phrase cards, comics, memory boards, cultural artefacts, discoveries, and reflective records need a shared ownership/lifecycle policy. The archive must support appropriate edit, reopen, delete, export, and media handling rather than being a read-only aggregation of demo records.
2. **Time capsules require trustworthy unlock rules.** Define trusted time, timezone changes, offline operation, clock manipulation, privacy, and deletion. Demo/developer unlock affordances must never silently become production rules.
3. **Discovery requires canonical identity.** World, region, place, landmark, and hidden-location IDs must be centrally defined and migrated deliberately. Learner discovery progress is separate from authored discovery content.
4. **Travel is not map geometry.** Infrastructure and route data describe where transport can move; a travel experience additionally needs itinerary/session state, staging, boarding, departure, journey, arrival, reveal, handoff, and interruption recovery.

Detailed source observations and limitations are recorded in Sections 40–42 of `PRODUCT_SYSTEMS_AUDIT.md`. These findings remain evidence from selected reference files, not proof of complete legacy behaviour.

## 34. Cassidy canon and character bible

The independent [Cassidy Character Bible](CASSIDY_CHARACTER_BIBLE.md) is the working character specification for Language-world. It preserves the established human character identity while separating immutable visual canon, permitted world adaptation, personality, agency, memory, dialogue, physical performance, cinematics, and asset production.

The actual canonical artwork remains authoritative over conflicting written outfit descriptions. The age presentation, voice identity, backstory, world outfit variants, and detailed autonomy/memory rules remain open until reviewed. The new project must independently produce its character model, rig, animation, and runtime; no legacy Cassidy production artifact or pipeline is reusable.

The Cassidy Character Bible is a supporting draft and does not become final canon until reviewed and approved by the product owner.

## 35. Universe and world bible

The independent [World & Universe Bible](WORLD_UNIVERSE_BIBLE.md) defines the universe hierarchy, Emerald Valley as the home world, requirements for distinct language worlds, world identity standards, canonical registry requirements, and travel connections. It records recovered Emerald Valley landmarks and Japanese/French location seeds while clearly identifying the Spanish-world gap and other open decisions.

No language world is approved as complete merely because it has a list of places or a visual theme. Each launch world requires a researched world bible covering geography, culture, society, ecology, stories, language experiences, sensory identity, transport, and production requirements.


## 36. Experience catalogue and quality standard

The independent [Experience Catalogue](EXPERIENCE_CATALOGUE.md) defines the universe-wide experience taxonomy: exploration, mysteries, stories, games, language-in-the-world, culture, creativity, optional social play, world-life, travel, events, and personal archive. It recovers the 60 mini-game ideas from the GoPAL-AI research archive while explicitly distinguishing design seeds from playable, validated content.

The catalogue establishes learning-integration categories, Cassidy's non-compulsory role, experience authoring requirements, recommendation and variety principles, persistence boundaries, accessibility and safety requirements, quality gates, and a candidate first-release portfolio. It is a working specification, not an approved content commitment. No implementation is authorized until the complete blueprint is reviewed and approved.

## 37. Learning design and evidence model

The independent [Learning Design](LEARNING_DESIGN.md) specification defines contextual learning across the universe, a multidimensional capability/evidence model, adaptive support, feedback and evaluation limits, listening/speaking/reading/writing requirements, vocabulary and grammar practice, cultural/pragmatic competence, progress, learner control, privacy, persistence, and accessibility.

It explicitly separates microphone capture, shadowing, transcription, semantic response evaluation, and measured pronunciation. The product must not claim to assess a capability without appropriate evidence. Learning remains integrated into the world rather than forcing every experience into a lesson. This is a working specification; language scope, assessment validation, and implementation remain open.

## 38. Living-world simulation

The independent [World Simulation Specification](WORLD_SIMULATION_SPEC.md) defines canonical time, day/night, authored climate and weather, seasons/calendars, resident schedules and autonomy, creature ecology, plant/garden lifecycles, festivals and world events, environmental storytelling, offline catch-up, performance tiers, and durable event/recovery requirements.

The specification explicitly leaves the canonical time model, world timezone/calendar policy, offline catch-up limits, and first-release ecology open for product decisions. It rejects treating device wall time, random ambient effects, or presentation state as the source of persistent world truth. This is a working specification; no implementation is authorized.

## 39. World objects, spaces, and interaction contracts

The independent [World Objects and Spaces](WORLD_OBJECTS_AND_SPACES.md) specification defines the spatial hierarchy from universe/world through regions, places, spaces, objects, and interactions. It establishes building/interior contracts, object identity and lifecycle, contextual interactions, navigation, inventory/collections, personal spaces, semantic world events, placeholder-to-final asset replacement, accessibility, and performance requirements.

It distinguishes world-authored facts, learner-owned state, shared state, and temporary session state. It also records legacy global-state and in-memory inventory risks that must not be inherited. This is a working specification; launch scope and technical contracts remain open.

## 40. Travel Director and inter-world journey lifecycle

The independent [Travel Experience Specification](TRAVEL_EXPERIENCE_SPEC.md) defines travel as a persistent, authored experience: route graphs, transport selection, boarding/departure/journey/transfer/arrival stages, optional in-transit activities, Cassidy's role, cinematic staging, destination handoff, accessibility, interruption recovery, and privacy.

It develops the first Emerald Valley-to-Spanish-world train journey as the reference experience while distinguishing existing local vehicle loops from a complete inter-world journey. The cinematic director owns presentation; the travel domain owns durable journey state and arrival. The first route remains to be authored and approved.

## 41. Audio, voice, and world sound identity

The independent [Audio, Voice, and Soundscape Specification](AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md) defines authored sound bibles per world, semantic cue contracts, runtime mix ownership, adaptive ambience, original music, character voice, language-learning audio integrity, captions, accessibility, interruption handling, content delivery, and production review.

The specification distinguishes playback, shadowing, microphone capture, speech recognition, pronunciation assessment, and conversation. It explicitly rejects claiming pronunciation assessment from playback or recording alone, and excludes the legacy Expo Audio playback adapter. Runtime technology, voice services, and launch language scope remain open.

## 42. Narrative, story, mystery, and continuity systems

The independent [Narrative, Stories, Mysteries, and Continuity Specification](NARRATIVE_AND_STORY_CONTINUITY_SPEC.md) defines story scales, canon and knowledge ownership, story authoring, fair mysteries and clue provenance, meaningful choices and consequences, resident autonomy, Cassidy's independent narrative role, ethical quest use, journals and re-entry, durable narrative events, learning integration, and cultural/quality review.

It distinguishes world canon, learner knowledge, learner choices, character knowledge, and presentation. The specification explicitly rejects local UI state as authoritative story progress, pre-completed seed quests, and inactivity-driven story urgency. The first story portfolio and long-running universe mystery remain to be authored and approved.

## 43. Persistence, privacy, identity, and synchronization

The independent [Persistence, Privacy, and Synchronization Specification](PERSISTENCE_PRIVACY_AND_SYNC.md) defines learner identity and local-anonymous scope, account migration, offline capability classes, durable local operations, synchronization and conflict semantics, cross-domain outbox recovery, clock trust, schema/content migration, memory provenance and access, privacy, security, personal-creation media lifecycle, export, deletion, backup, and recovery.

The specification records concrete GoPAL-AI reference limitations: shared unscoped local keys, a hard-coded local demo identity, user ID loss in local memory fallbacks, seeded personal demo data, non-transactional read/write mutations, weak timestamp-derived IDs, and incomplete memory provenance. It explicitly requires isolated learner scope and honest local-versus-synced status. Backend, identity model, offline promise, voice/AI processors, and retention policy remain open. This is a working specification; no implementation is authorized.

## 44. Creative experiences and the personal archive

The independent [Creative Experiences and Personal Archive Specification](CREATIVE_EXPERIENCES_AND_PERSONAL_ARCHIVE.md) defines the learner's creative ecosystem: Journey Book and journal, postcards, phrasebook, comics/storyboards, memory boards, cultural discoveries and museum exhibits, time capsules, and selected conversation archives.

It establishes editable structured source as authoritative, with rendering and media as versioned derivatives; learner ownership and privacy; explicit sharing; AI-assistance provenance; cultural/rights review; accessibility; durable object identity and lifecycle; and export/deletion integration. It proposes a staged first-release sequence without approving scope. The GoPAL-AI research found useful seeds but also sample-only transcripts, demo unlock bypass, timestamp IDs, limited text-only creation records, and no demonstrated full edit/media/export lifecycle. No legacy implementation is reused.


## 45. GoPAL-AI idea recovery and transfer audit

The new [GoPAL-AI Idea Recovery and Transfer Audit](GOPAL_IDEA_RECOVERY_AUDIT.md) consolidates the transferable product ideas, experience patterns, design lessons, and failure lessons recovered from GoPAL-AI. Its boundary is explicit: ideas only. No source code, media, 3D models, images, animation, audio, assets, production pipeline, scripts, or implementation contracts are to be transferred.

The audit covers the place-worth-returning-to philosophy; distinct living worlds; contextual learning; a 60-seed mini-game catalogue; Cassidy and resident autonomy; narrative scales and mysteries; world simulation and ecology; objects and personal spaces; travel; audio; personal journey and creative experiences; experience direction; healthy return; and future optional social possibilities. It distinguishes documented ideas from implemented foundations and unverified claims, and records weaknesses that Language-world must not repeat.

Language-world should adopt the underlying human value, not the old feature implementation. The transfer matrix identifies ideas to adopt, redesign, expand, defer, or reject. The audit now also consolidates the early product-specification concepts (first-open and return rituals, persistent home, ambient learning, review stories, explanation modes, real-life preparation, event scale, progression dimensions, accessibility, and progressive fidelity) and records the player-facing surface/reachability lesson. This document is a research consolidation, not approval of launch scope or implementation. Product-owner review remains required.


## 46. Master Blueprint reconciliation and remaining product decisions

The [Master Blueprint Reconciliation](BLUEPRINT_RECONCILIATION.md) compares the recovered GoPAL-AI ideas with the current Language-world specification set, identifies what is already captured, and records missing product-level definitions and cross-document inconsistencies.

The central finding is that the project has broad system coverage but still needs decision closure and a coherent end-to-end product definition. Critical remaining work includes audience/age policy, first-release promise and scope, navigation and session journeys, Experience Director boundaries, actual world canon, Cassidy canon approval, AI/voice governance, and a unified technical architecture. Progression/monetization and operational/live-content policy also require explicit decisions or deferral.

The reconciliation also identifies stale work-order language, supporting-document filename mismatches, ambiguity about GoPAL-AI asset inspection, and duplicate architecture-decision numbering. The supporting-document table and work order have been corrected to reflect the current document set and the user's ideas-only boundary.

This reconciliation does not approve features, select an engine/backend, or authorize implementation. The product owner must review the open decisions and approve the complete blueprint explicitly.


## 47. Engine-neutral Technical Architecture

The working [Technical Architecture](TECHNICAL_ARCHITECTURE.md) consolidates domain ownership, logical layers, state classes, commands/events, durable cross-domain operations, runtime lifecycle, time domains, offline/sync boundaries, content packs, semantic asset resolution, cinematic/travel integration, AI/voice boundaries, privacy/security, operations, and testing.

It intentionally does not select an engine, backend, database, AI provider, or speech service. It translates the product requirements into architecture constraints while preserving the existing decisions: no Expo, no GoPAL-AI implementation or assets, renderer-independent domain truth, and Android evidence before engine selection.

This is a working architecture draft. It must be reconciled with UX/accessibility, product scope, AI/voice governance, and production/quality specifications before the blueprint can be approved.
