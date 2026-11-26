# Language-world — Master Blueprint

**Document status:** Working draft v0.1 — research and design in progress; not approved for implementation  
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

1. Complete the remaining read-only reference review, especially objects/interiors/inventory, environment and festivals, audio/animation/cinematics/accessibility, and persistence/account/sync/privacy/offline behaviour.
2. Expand every chapter into specific requirements, flows, examples, acceptance criteria, and supporting specifications.
3. Resolve product questions that materially affect scope, safety, privacy, and architecture.
4. Create individual World Bibles and the Cassidy Character Bible.
5. Create detailed specifications for experiences, learning, world simulation, narrative, cinematics, travel, asset contracts, persistence, and technical architecture.
6. Cross-check all specifications for contradictions, missing dependencies, feasibility, and scope.
7. Review the complete blueprint with the product owner and record explicit approval.

**Current approval state: NOT APPROVED FOR IMPLEMENTATION.** This is the foundation draft. Its purpose is to make the next design work structured and traceable, not to pretend the universe is already fully specified.
