# Product Systems Audit — Cassidy, Living World, Relationships, Learning

**Status:** Working findings from direct source inspection  
**Source repository:** `jamlove1318-lab/GoPAL-AI`  
**Destination repository:** `jamlove1318-lab/Language-world`  
**Boundary:** GoPAL-AI is reference-only and remains untouched. This document extracts product ideas and records weaknesses; it does not authorize reuse of source code. The legacy GoPAL-AI 3D pipeline is explicitly rejected and excluded under ADR-010.

## 1. Cassidy: product ideas worth carrying forward

The inspected source includes separate concepts for perception, autonomy, personality, life activities, meaningful experiences, narrative moments, world presence, runtime sessions, and experience coordination.

Product ideas worth preserving and redesigning:

- **Perception before response:** Cassidy should notice the learner's current activity, location, nearby people, opportunities, recent success or difficulty, atmosphere, and conversational context.
- **Autonomy with restraint:** she should sometimes observe, continue her own activity, invite the learner, help, celebrate, or choose not to interrupt. Quiet presence is a valid behaviour.
- **A life beyond the learner:** activities represented in the old concept include wandering, reading, visiting a café, watching rain, stargazing, resting, storytelling, dreaming, discovering, and going on adventures.
- **Shared continuity:** meaningful discoveries, adventures, stories, help, and celebrations can become persistent experiences rather than disposable dialogue.
- **World-aware presence:** Cassidy's behaviour and words should make sense in Emerald Valley and in each distinct language world, with world/location context and scene anchors.
- **Return and travel continuity:** Cassidy can accompany the learner across worlds and return home, while retaining a coherent identity and relationship.
- **Narrative agency:** stories and adventures can begin from things Cassidy notices, remembers, or finds interesting—not only from explicit lesson menus.

These are design directions, not a commitment to reproduce the existing implementation.

## 2. Cassidy: limitations observed in the old implementation

The inspected files show useful architectural separation, but the behaviour is still largely rule-driven:

- Personality traits such as curiosity, warmth, playfulness, patience, adventurousness, and confidence are stored as bounded numbers. Many changes are fixed increments attached to broad event flags. This risks turning personality into a hidden score system rather than a coherent, contextual human character.
- The autonomy decision tree has a small number of high-priority conditions (success, help, nearby resident, discovery) followed by a weighted activity choice. It is a useful prototype, but not sufficient for nuanced motives, competing intentions, emotional continuity, or believable initiative.
- Perception produces short, fixed-priority cues from a compact snapshot. It does not by itself establish deep understanding of the scene or the learner.
- Life activities and narrative prompts rely on fixed templates and deterministic/pseudo-random selection. They provide variety but can become repetitive and do not amount to a fully authored personal life.
- Some generated life moments are written into memory and personality state together. The new design should separate event facts, interpretation, emotional significance, relationship impact, and later recall.
- The old world-presence layer chooses from predefined dialogue lines. New dialogue must be grounded in current scene facts and relevant memories, while retaining a stable voice and avoiding repetitive canned responses.
- Multiple runtime, presentation, personality, life-state, and interaction modules create a risk of fragmented state ownership. The new design needs one authoritative Cassidy state model and explicit domain boundaries.

**Conclusion:** Preserve the aspiration that Cassidy is an autonomous human character with continuity. Do not copy the numerical personality model, fixed decision tree, prompt templates, or split runtime architecture as-is.

## 3. Memory and relationships

The old project contains a generic memory engine with layers including profile, learning, conversation, character, world, story, progress, preference, achievement, and session. It attempts local storage with optional Supabase persistence.

There are also resident relationship concepts that track familiarity, trust, warmth, shared moments, help, choices, and short summaries of meaningful encounters. Story threads can move through stages such as seeded, waiting, ready, and resolved. Environmental observations can trigger later acknowledgement by a resident rather than forcing an immediate quest.

### Product direction for the new project

Build a deliberate memory model with separate categories:

1. **Event memory:** what actually happened, when, where, and who was present.
2. **Personal memory:** what Cassidy experienced, noticed, preferred, promised, or chose.
3. **Learner memory:** explicitly useful learning context and preferences, with privacy controls.
4. **Relationship history:** shared experiences and meaningful changes in trust, familiarity, comfort, and understanding.
5. **World memory:** discoveries, changes, visits, unresolved threads, and consequences.
6. **Narrative threads:** open questions, promises, clues, and events that may return later.

Memory must support provenance, importance, confidence, retention/expiry rules, user control, and correction. Avoid storing every utterance as equally important. Relationship should emerge through accumulated experiences and behaviour; do not expose it as a visible numeric affection meter or make it a grindable reward.

The old code's generic memory fallback and world-state storage patterns should not be adopted. The new project needs a versioned, user-scoped, local-first persistence design with explicit sync and conflict behaviour.

## 4. Living-world simulation and residents

The old project contains concepts for world snapshots, time-of-day, weather, atmosphere, ambient activity, resident routines, resident motion, encounters, relationships, stories, persistent place visits, discoveries, and consequence follow-ups.

Useful product ideas:

- A place should remember visits and discoveries.
- Residents should have routines and activities independent of the learner.
- A resident's attention can shift when the learner approaches, then return to their own task.
- Choices and shared moments can influence later greetings and encounters.
- Environmental clues can be noticed first and acknowledged later.
- Story threads can remain unresolved and become available again when context makes sense.
- The world should change with local time, weather, season, and meaningful events.

Limitations observed:

- Some world snapshots are generated from the current clock with default clear weather and fixed baseline temperatures/activity values. This is a data shape, not yet a convincing simulation.
- The inspected resident routine prototype uses coarse hour bands and short fixed transitions. It does not establish robust schedules, navigation, social needs, or long-term state.
- Relationship values are sometimes simple counters and thresholds, which can make interactions mechanically transactional.
- Some world-state systems store serialized state in generic memory/local key-value layers. The new project should not reproduce this persistence coupling.
- Simulation must not depend on frequent UI/render updates. Separate authoritative simulation state from presentation and update only what materially changes.

## 5. Contextual learning and activities

The inspected learning surface includes world hotspots, resident encounters, scenario activities, investigation boards, story choices, crafting, rhythm, audio navigation, drag-and-drop, phrase building, and timed/memory activities.

Preserve the principle that language is used to do something meaningful in a place: ask a resident for help, follow a clue, make a choice, craft an object, navigate, understand an announcement, solve a local problem, or participate in a cultural activity.

Do not turn the living world into a grid of generic quiz doors or a sequence of modal mini-games. Activities should arise naturally from world context, have clear learning intent, and leave a trace in the world or the learner's memory. Ensure accessibility and non-timed alternatives.

## 6. New project design requirements

- Cassidy is a **human female character**, not an animal, mascot, or anthropomorphic companion. Her approved design and identity information are canonical creative references.
- Her new in-world representation and all visual-production tooling must be created from scratch. No GoPAL-AI 3D model, rig, renderer, asset factory, export workflow, manifest, or pipeline code may be reused.
- Design one authoritative Cassidy domain model, with explicit modules for identity, perception, intention, action, emotion, memory, relationship, dialogue, world participation, and learning collaboration.
- Treat autonomy as context-sensitive intention selection with cooldowns, safety boundaries, interruption policies, and explainable reasons—not as a simple random activity picker.
- Let Cassidy have preferences and recurring interests, but ensure they evolve from credible experiences and never override the user's agency.
- Design world simulation around meaningful state changes, deterministic testability, offline progression rules, and mobile performance budgets.
- Give each language world its own distinct geography, culture, residents, soundscape, and learning opportunities. Emerald Valley remains the home world, not a template for every world.

## 7. Next audit targets

- Trace the complete Cassidy event path from world observation through decision, action, dialogue, memory write, relationship change, and later recall.
- Inspect the full world simulation and resident systems for ownership, persistence, schedules, event causality, and offline behaviour.
- Inventory every learning activity and map each to its world context, language objective, accessibility needs, and persistence outcome.
- Audit the language-world registry and content model to ensure world identity is not merely a reskin.
- Inspect the current navigation and reachable app surfaces to distinguish implemented product behaviour from disconnected prototypes.

## 8. Classification

| Classification | Meaning |
|---|---|
| Preserve as product intent | A valuable experience principle worth redesigning |
| Rework | Useful idea, but current implementation is too simplistic or coupled |
| Replace | Existing implementation should not be carried into the new architecture |
| Exclude | Explicitly prohibited from reuse |
| Verify | Evidence is incomplete; inspect before deciding |

This is a working audit, not a claim that the entire GoPAL-AI repository has been reviewed.

## 9. Language-world registry and identity audit

The inspected GoPAL-AI language-world registry currently defines Japanese, Spanish, French, and Korean worlds. Its metadata includes language identity, world naming, a visual-identity description, cultural categories, and place records. The Spanish and Korean entries contain explicit city/region examples; Japanese and French places are materialized from a separate location catalogue. This is a useful start for content organization, but not yet a full world-design system.

Risks and design implications:

- A language label is not a world identity. Spanish-speaking regions, for example, contain distinct countries, climates, accents, architecture, food, social customs, and everyday rhythms. A single generic Spanish environment would flatten those differences.
- The registry mixes broad world metadata with place records and learning purposes. The new project should separate world identity, regions, settlements, locations, resident populations, cultural references, language variants, and activity content.
- World content should be authored as a coherent place: geography and climate first, then settlements and routes, daily life and inhabitants, stories and landmarks, and finally language activities that naturally belong there.
- Emerald Valley should remain the home world and emotional point of return. It must not become the universal template reskinned for each language.

The old Emerald Valley specification contains valuable creative direction about emotional atmosphere, geographic hierarchy, continuous settlement composition, visual readability, weather, and the feeling of returning home. These may be reconsidered as product/world-design principles. Its old coordinate anchors, asset transforms, runtime assumptions, renderer choices, and 3D implementation instructions are not a technical foundation for the new project.

## 10. Cassidy runtime event-path audit

The inspected runtime bridge currently runs an autonomous decision on a fixed 90-second interval. It restores the user session, reads current world presence, life state, and personality, makes a decision, executes an action, and may create a narrative or record a meaningful experience. It also listens for world-location changes, returns home, and completed conversations.

This is a useful end-to-end prototype, but several limitations matter for the new design:

- The autonomous tick currently supplies a narrow snapshot: the learner is marked as not exploring, not needing help, and not recently successful. The decision therefore cannot reliably respond to the full live scene unless other pathways update it.
- A fixed 90-second interval is not a substitute for event-driven awareness. Some events need immediate response; other periods should remain quiet for much longer.
- The action executor writes life state asynchronously and emits an event, while meaningful experiences may be persisted through a separate coordinator. These responsibilities need one explicit transaction/event policy to avoid partial or duplicate outcomes.
- The interaction lifecycle deduplicates some events in process memory and local storage, but it coordinates character relationship changes, memory writes, and personality evolution across separate operations. The new design must define idempotency and recovery across the whole experience, not just one step.
- The character runtime snapshot currently stores presentation-oriented state such as world/location, expression, animation, outfit, visibility, and transition ID. It should remain separate from Cassidy's authoritative identity, motives, memory, and relationship state.
- Fixed action text and fixed visual-action mappings are useful fallbacks, but they should not become the character's full behaviour or dialogue system.

**New architecture implication:** separate (a) perception/event ingestion, (b) intent and priority selection, (c) action planning, (d) world interaction execution, (e) dialogue generation, (f) memory/relationship transaction, and (g) visual animation requests. Give every meaningful event a stable ID, causal links, timestamps, and a clear retry/deduplication policy. The presentation layer must never be the source of truth for Cassidy's internal state.

## 11. World runtime and simulation audit

The inspected world runtime loads persisted location state, calculates elapsed time since the last visit, advances a simulation snapshot, writes the resulting time/season/weather back into world state, and produces a revisit recap. Location changes are validated against the active world's location catalogue and emit a world-location event.

This suggests a valuable continuity loop: leave a place, allow time to pass, return, and notice what changed. However, the inspected simulation snapshot is currently quite shallow:

- Day phase is derived from the device clock.
- The inspected snapshot constructor initializes weather to clear with a fixed baseline temperature and derives broad ambient activity from time-of-day.
- Resident routine prototypes use coarse hour bands and fixed short transitions rather than a complete schedule/needs model.
- Some runtime surfaces describe simulation/weather/environment as running, but that flag alone does not prove a persistent, evolving simulation.
- Revisit recaps currently derive mainly from date/season and stored visit differences, not a rich causal history of world events.

**New architecture implication:** define simulation time explicitly (including offline elapsed time, time-zone changes, clock tampering, and pause rules); represent weather and world events as deterministic, testable state; use schedules and event-driven state transitions for residents; and persist only meaningful state changes. Render frames must not drive simulation truth. The world should be able to advance while the app is closed according to bounded, battery-conscious rules.

## 12. Audit confidence

The findings above are based on direct inspection of the named source modules and registry/specification files, not on a complete execution or device test of the old app. They describe code structure and apparent behaviour, not proof that every path is currently reachable or functioning in production. The complete audit still needs call-site tracing, data-flow verification, and feature-level tests.

## 13. Contextual learning and mini-game audit

The inspected learning engine supports six broad skills (vocabulary, listening, speaking, reading, grammar, writing) and builds a learning moment from the active language world, place, scenario, and skill. Scenario records can include a scene, goal, target phrase, translation, vocabulary, response options, cultural note, follow-up, and a described world change.

A completion flow attempts to connect a learning turn to several consequences: capability tracking, learning integration, resident relationship changes, Cassidy's reaction and interaction memory, and a world consequence. Successful outcomes can update a location story layer and create a world echo. This is the right product ambition: learning should change what happens and what the place remembers.

The mini-game catalogue spans discovery, puzzle, arcade, social, listening, adventure, and creative families. Examples include sign reading, word hunts, phrase building, listening navigation, market/café interactions, investigation, story choices, crafting, and creative world-building.

### Risks and limitations observed

- The catalogue is broad, but a large number of named mini-games can become content volume without meaningful differences in learning mechanics. The new project should prefer a smaller set of deeply contextual interaction patterns that can be recombined intelligently.
- Some scenario flows are fixed multiple-choice experiences. They can support beginners, but cannot be the only route to genuine comprehension, listening, speaking, free response, and transfer to new situations.
- The inspected mini-game component contains generic fallback vocabulary and generated rounds when scenario content is missing. This is a development convenience, not acceptable authored learning content.
- A completion flow performs multiple side effects across capability, integration, relationship, Cassidy, and world systems. Its idempotency marker is stored separately from those effects; interruption between writes could leave a partially applied outcome. The new project needs a transactional event/outbox or recoverable workflow.
- A failed or incomplete attempt should be treated as useful learning evidence, not as a negative relationship event or punishment. The learner should be able to pause and return.
- Learning consequences should be specific and observable. Avoid a generic message that a location changed when nothing visible or meaningful actually changed.

### New learning design

- Start with the situation and the learner's intention, not with a mini-game category.
- Give the learner a reason to listen, read, speak, choose, write, negotiate, ask, repair a misunderstanding, or help someone.
- Use scaffolded hints and optional translations; fade support as competence grows.
- Accept multiple valid responses where appropriate, and distinguish communicative success from exact-string matching.
- Include accessible, untimed alternatives and input modes that work for different abilities and environments.
- Record evidence of what the learner understood and could do, with uncertainty and context—not just XP, streaks, or a binary correct/incorrect value.
- Make consequences concrete: a resident understands, a route becomes familiar, a clue is interpreted, a craft is completed, a local story advances, or a new conversation becomes possible.
- Design content per world and region. Cultural material must be researched, reviewed, respectful, and not reduced to stereotypes.

## 14. World activities, discovery, quests, and exploration

The repository contains several distinct progression and interaction concepts:

- **Place discovery:** a world discovery graph links places to learning scenarios, landmarks, and hidden-gem flags. The inspected builder currently assigns each place a prerequisite based on the immediately previous place, producing a mostly linear unlock chain.
- **Quests:** quest categories include daily, cultural, conversation, exploration, story, and personal goals. The sample seed data includes already-completed quests, suggesting demonstration state rather than a clean first-run learner experience.
- **Inventory and crafting:** small domain helpers represent items/materials, recipes, quantities, and crafted outputs. These are useful mechanics for world activities, but the new project should decide which objects have lasting meaning rather than adding inventory management for its own sake.
- **World opportunities:** a catalogue can surface resident, weather, discovery, and Cassidy-led moments. Examples include noticing an unusual café guest, investigating a misplaced book page, helping with a market lantern, or following Cassidy to a night-time viewpoint. Some follow-ups depend on previously stored world flags.
- **Memory Museum:** the archive combines postcards, learner creations, cultural artifacts, and memory exhibits. This is a strong emotional idea: the learner should be able to revisit tangible traces of their own journey.

### Limitations and design implications

- A sequential place prerequisite can make exploration feel like a locked checklist. The new world should support multiple routes, optional discoveries, revisits, and curiosity-driven access, with gates used only when they make narrative or learning sense.
- A quest/reward layer can accidentally turn every meaningful moment into a task. Many opportunities should remain invitations, observations, or stories that can be declined without penalty.
- Seeded completed quest state is not a valid first-run experience. New profiles need intentional onboarding and clean state.
- The inspected audio waypoint helper contains a no-op selection function; the actual route check is in a separate function. This is a reminder that exported helpers and named features need behaviour-level tests, not just presence checks.
- The inspected opportunity catalogue uses a small fixed set of authored scenarios and time/weather filters. It is a promising narrative seed system, not yet a dynamic world director.
- Inventory and crafting helpers are intentionally simple and do not by themselves provide durable world consequences, provenance, or recovery after interrupted writes.
- The Memory Museum's current screen is a tabbed archive surface. The new product can retain the idea of a personal living archive, but it should feel connected to places and experiences rather than becoming another detached dashboard.

### New project direction

Make exploration intrinsically rewarding. Let discoveries emerge from observation, conversation, revisiting, environmental change, resident routines, and personal curiosity. Use quests sparingly as optional narrative framing. Allow the learner to keep meaningful objects, postcards, notes, photographs, recordings, sketches, and shared memories, but only when each has a clear story or personal purpose.

## 15. Atmosphere, sound, and time

The old project includes a world audio mixer with categories for music, ambience, location, activity, interaction, transport, voice, and events. It models location profiles, priority, gain, distance attenuation, quiet mode, and cooldowns. This is a useful design inventory for a layered soundscape.

The environment engine derives time-of-day and season from the device date and selects weather deterministically from the day/hour and season. This avoids random render-state changes, but it is not a meteorological simulation and can repeat in visibly patterned ways. The new project should distinguish ambient presentation from authoritative world climate and authored weather events.

Design implications:

- Build a soundscape from layers that respond to location, distance, weather, time, activity, and narrative importance.
- Respect user volume controls, quiet mode, audio focus, headphone/speaker context, data use, and accessibility captions.
- Use authored seasonal and weather patterns appropriate to each world's geography and climate; avoid arbitrary weather chosen only for visual variety.
- Time and weather should create opportunities and atmosphere, but should not make essential learning or progression inaccessible.
- Establish bounded offline time advancement and deterministic simulation rules, rather than relying on device clock values throughout unrelated systems.

## 16. World content and persistence quality risks

The inspected world systems show several separate stores and key-value persistence paths, including AsyncStorage and a generic local store. There are canonical ID aliases in discovery progression, and different modules maintain their own flags or snapshots.

This creates a migration and consistency risk: a single place or event can be represented by more than one ID or written through more than one persistence path. The new project should establish stable domain IDs, schema versions, explicit ownership, event provenance, and migration tests before significant content is authored.

A world consequence should be applied once, recover safely after interruption, and be observable on the next visit. The system should distinguish:
- transient presentation state (camera, animation, temporary sound cue);
- session state (current interaction and temporary choices);
- durable personal state (memories, preferences, creations);
- durable world state (discovered places, resident story changes, repaired objects);
- derived state (what can be recomputed from authoritative records).

Avoid persisting every animation or frame-level detail. Persist meaningful facts and reconstruct presentation.

## 17. Feature disposition snapshot

| Area | Product disposition | Implementation disposition |
|---|---|---|
| Cassidy autonomous presence | Preserve ambition | Replace old decision/runtime implementation |
| Cassidy memory and relationship | Preserve and deepen | Rebuild with event provenance and explicit privacy |
| Resident routines and continuity | Preserve ambition | Rework schedules, needs, simulation and persistence |
| Place discovery | Preserve curiosity | Replace linear checklist-first progression |
| Quests | Optional supporting tool | Rework; do not make every experience a task |
| Inventory and crafting | Use where meaningful | Rebuild only around meaningful world objects |
| World opportunities | Preserve authored surprise | Rework into contextual, non-coercive event director |
| Memory Museum | Preserve personal archive idea | Reimagine as integrated living archive |
| Audio and atmosphere | Preserve layered soundscape | Design fresh per-world systems |
| Old GoPAL-AI 3D pipeline | Exclude | No reuse, port, adaptation, or dependency |

This disposition is provisional and will be refined as the remaining call sites, screens, stores, and feature flows are traced.

## 18. Persistence, identity, and event architecture audit

The inspected GoPAL-AI persistence layer combines a large AsyncStorage-backed local store, a learner-memory store with user-scoped keys, a separate memory engine with optional Supabase persistence, world-state snapshots serialized into a generic memory record, and additional world flags/opportunities stored through other key-value paths.

Useful product requirements visible in this work:

- Keep the experience usable locally and across sessions.
- Scope personal memories to the correct learner.
- Preserve world visits, discoveries, creations, relationships, and meaningful events.
- Migrate older local data rather than silently losing it.
- Allow optional cloud persistence.

However, the current patterns reveal important risks:

- There are multiple memory write/read paths with different fallback behaviour. One path can fall back to a generic local memory list that is not obviously scoped to the requested user.
- The generic local store contains a very broad collection of unrelated seed data and domain types. This makes it easy for unrelated systems to share keys or become coupled to one storage module.
- The seed data initializes a returning learner with high Cassidy trust/friendship/familiarity, pre-existing memories, unlocked locations, and completed activities. This may be useful for a demo, but it is not a neutral new-player state.
- Persistent world state is serialized as a large JSON string inside a world-layer memory fact. That is difficult to query, migrate, validate, partially update, or reconcile.
- The event bus keeps a short in-memory history and synchronously notifies handlers. That is useful for runtime coordination, but it is not a durable event log and does not guarantee that asynchronous side effects complete.
- Some reactors use an in-memory deduplication set. A process restart clears it, while the bounded set eventually evicts old IDs. It cannot provide durable exactly-once processing on its own.
- Local and cloud writes may fall back independently. The project needs explicit offline-first semantics, sync cursors, retry queues, conflict resolution, account switching, export, and deletion behaviour.

### New project persistence design requirements

Use domain-owned repositories rather than one giant generic store. Define stable IDs and versioned schemas for learner profile, Cassidy identity/state, relationship history, world locations, residents, discoveries, learning evidence, creations, and narrative threads. Use a durable event/outbox pattern for cross-domain consequences, with idempotency keys and recoverable processing. Separate event facts from derived summaries. Define user consent and retention for conversation/memory data. Support local-first operation and explicit cloud sync without making cloud availability a prerequisite for entering the world.

No persistence architecture should be selected solely because it is familiar from the old React Native implementation. Choose storage based on the new engine/runtime, offline requirements, Android constraints, and testable recovery behaviour.

## 19. World catalogue maturity and expansion limits

The inspected world catalogue currently exposes Emerald Valley as the home world and Japanese and French as language worlds. The canonical language-location data includes real and fictional places in Japan and France, with descriptions, tags, experience categories, unlock order, and illustrative 2D coordinates.

This is a content registry, not proof of complete distinct worlds. It currently lacks the full authored depth required for each world: coherent geography, regional climate, ecology, architecture, settlement layout, resident population, daily routines, transport, local soundscape, cultural calendar, story arcs, and region-specific learning progression.

The new project must not copy the old location list as its world design. Use it only as evidence of the kinds of place and learning contexts previously considered. Build each world from researched, internally consistent world bibles and modular content packs. Real-world cultural material should be reviewed for accuracy and nuance; fictional locations should belong plausibly to their region rather than act as generic quiz rooms.

## 20. Reachable app experience and product-surface audit

The inspected root `App.tsx` mounts four primary tabs: Explore (Emerald Valley), Travel, Cassidy, and Study Room. A secondary menu opens Memory Museum, People/Characters, and Settings. The root also starts a living-world reactor, hydrates world presence, restores a Cassidy snapshot, handles travel/return events, and opens learning scenario overlays.

This confirms that the existing project has a connected experience path beyond isolated source modules. It also shows where the new project should improve the product structure:

- The current experience is still organized around a bottom tab bar and separate screen surfaces. The new project's primary experience should be the explorable world itself, with contextual interactions and discreet world-native navigation.
- Study, Travel, Cassidy, archive, and people should feel like activities, places, conversations, or in-world tools where appropriate—not separate app destinations that repeatedly pull the learner out of the world.
- Utility surfaces such as account, accessibility, settings, privacy, and data controls may remain conventional UI.
- A scenario overlay can be useful for focused learning, but the new project should avoid making every interaction a modal mini-game detached from the scene.
- Root-level runtime startup and hydration show that persistent systems need clear lifecycle ownership. Avoid starting duplicate reactors or timers when screens mount/unmount or the app resumes.
- The current app seeds local identity and sample history. New onboarding must create a clean learner state and explicitly distinguish demo data from personal data.

The product blueprint's strongest north-star principles remain valuable: continuity over resets, curiosity over obligation, relationship over score, context over disconnected drills, small meaningful surprises, agency over rigid paths, and honest memory over simulated intimacy. These principles are carried forward as design intent, not as an instruction to copy the old UI or code.

## 21. Feature audit status and evidence boundary

This audit now covers representative source modules for Cassidy autonomy/personality/memory/runtime, world simulation and residents, contextual learning, discovery and quests, crafting/inventory, audio/environment, world catalogues, persistence, and the root navigation experience.

It is still not a complete repository-wide verification. Remaining work includes:
- Trace every root-mounted screen and each user-visible route to its data and event handlers.
- Inventory all features documented in the master blueprint and compare them with actual reachable implementation.
- Verify which systems are imported and invoked, which are prototypes, and which are disconnected or superseded.
- Inspect all data migrations, account switching, Supabase policies, privacy/export/deletion flows, and offline recovery.
- Inspect asset licences and source provenance separately from the rejected 3D production pipeline. No old pipeline artifact becomes eligible for reuse through this audit.
- Run no claim of runtime correctness without a successful build and device-level test.

The audit should continue to classify findings as product intent, implemented/reachable, implemented but unverified, prototype, disconnected/legacy, duplicated, broken/incomplete, or explicitly excluded. A source file's presence alone is never enough to assign the "working" classification.

## 22. Remaining product-surface inventory from the master blueprint

The master blueprint describes these additional surfaces and capabilities. They are included in the audit scope so that important ideas are not lost simply because they are not part of the first vertical slice.

| Product area | Ideas to evaluate for the new project | New-project stance |
|---|---|---|
| Arrival and re-entry | Time-aware welcome, meaningful away recap, gentle invitations, unfinished activity recovery | Preserve; no guilt or streak pressure |
| Home / sanctuary | A place to return to, festivals, world DJ, continuity and calm choices | Reimagine as the living world, not a dashboard |
| Adaptive conversation | Level-aware roleplay, intent, recent difficulty, confidence, adjustable correction | Preserve and deepen |
| Socratic learning | Questions and hints before revealing answers; optional model answer/translation | Preserve with learner-controlled scaffolding |
| Residents | Distinct roles, preferences, routines, conversations and continuity | Preserve; residents must be people, not quiz terminals |
| Pronunciation/listening | Pitch and prosody, shadowing, replay, slower audio, syllable highlighting | Evaluate feasibility and accuracy on Android |
| Writing/calligraphy | Guided writing, stroke order, saved creations and retries | Preserve as contextual creative activities |
| Vocabulary recall | Context capture, spaced revisits, retention rather than tap counts | Preserve with evidence-based scheduling |
| Learning evaluation | Comprehension, productive use, recall, fluency and confidence | Rework into transparent evidence, not opaque scoring |
| Journey/transcripts | Milestones, chapter reviews, transcripts, replay, learner-controlled progress comparison | Preserve with privacy and export controls |
| Living objects | Plant care, radio, wish plaques, meaningful physical-world traces | Preserve selectively; never punish missed care |
| Cultural discovery | Artifacts, wonder prompts, stories, researched cultural context | Preserve with expert/cultural review |
| Creative studio | Postcards, phrase cards, memory boards, comic strips and other learner creations | Preserve if creation can be saved, reopened and exported |
| Time capsules and wishes | Private intentions, delayed revisits, personal notes | Optional, private by default |
| Soundscape | World radio, layered ambience, per-category volume and quiet mode | Preserve with accessibility and audio-focus handling |
| Quests and rewards | Optional narrative goals, souvenirs and artifacts | Rework; avoid grinding and coercive reward loops |
| Museum/archive | Postcards, creations, artifacts, exhibits and shared memories | Integrate into world places and personal history |
| People/characters | Resident profiles, introductions and relationships | Make accessible through in-world encounters |
| Settings and diagnostics | Privacy, accessibility, account, audio, data and diagnostics | Conventional utility UI is appropriate |

The master blueprint also describes privacy, accessibility, and trust as foundational requirements: learner control over memory, honest claims about what Cassidy remembers, adjustable hints/corrections, reduced-motion support, readable typography, audio controls, and no guilt for absence. These are acceptance requirements, not optional polish.

## 23. First-vertical-slice candidates from the audit

Do not implement the entire feature catalogue at once. The first vertical slice should prove the core emotional and technical loop with a very small, coherent area:

1. Enter Emerald Valley and understand where the learner is.
2. Move through a small, authored place with meaningful environmental depth and interaction.
3. Meet Cassidy as a human character with the approved identity, presence, movement, expressions, and a short natural conversation.
4. Meet one resident whose own activity continues independently.
5. Complete one contextual language interaction using at least two response modes (for example, typed response and guided support).
6. Have the interaction create a concrete, visible world consequence.
7. Have Cassidy and the resident remember the meaningful event in a later encounter.
8. Leave the app, return, and verify continuity and safe recovery.
9. Provide quiet mode, readable UI, reduced motion, and an accessible alternative to any time-sensitive interaction.

This is a product and architecture proof, not a commitment to a specific engine or final art style. All visual assets and production tooling must come from the new pipeline; the old GoPAL-AI 3D pipeline remains explicitly excluded.



## 24. Product identity correction: a whole universe, not a Cassidy-and-residents simulator

The new product must be understood as a broad, living language-learning universe. Cassidy is its heart and emotional anchor, but she is not the entire experience. Residents are one important part of the world, not the sole source of activity, story, learning, or discovery. The universe must remain interesting and meaningful when Cassidy is elsewhere, when the learner is alone, and when no resident encounter is taking place.

This distinction is a core product constraint. Do not let the first vertical slice, the easiest systems to prototype, or the character architecture accidentally narrow the product into a companion simulator.

### Experience pillars to develop as first-class systems

1. **World exploration and discovery** — landscapes, settlements, interiors, hidden places, landmarks, routes, natural wonders, objects, collections, secrets, and discoveries that reward curiosity.
2. **Stories and narrative** — authored story arcs, local tales, mysteries, character-led stories, environmental storytelling, optional side stories, episodic events, branching choices where meaningful, and long-running narrative threads. Stories should exist beyond resident dialogue and should not all revolve around Cassidy.
3. **Games and playful challenges** — substantial game experiences across listening, speaking, reading, writing, observation, memory, puzzles, rhythm, movement, creativity, cooperation, and adventure. Games should be varied in format and purpose, not a large pile of shallow quiz reskins. They can be discovered in the world, arise from stories, or be played as standalone in-world activities.
4. **Learning through many forms** — conversations, exploration, stories, games, making, collecting, performance, problem-solving, cultural discovery, reading, listening, writing, pronunciation, and everyday world interactions. No single activity format should dominate.
5. **Characters and residents** — residents have their own lives, relationships, work, interests, stories, and knowledge. They contribute to the universe, but are not merely quest dispensers or language exercise interfaces.
6. **Cassidy and the learner's relationship** — Cassidy is the heart of the experience: a fully realized human character, trusted companion, guide, participant, and continuing presence. Her importance comes from authentic personality, agency, shared history, care, humour, growth, and meaningful participation—not from appearing in every activity or monopolizing every story.
7. **Culture, creativity, and personal expression** — festivals, music, crafts, food, art, performances, local customs, learner-made creations, journals, postcards, collections, and personal keepsakes.
8. **Living-world systems** — time, weather, seasons, ecology, sound, ambient events, routines, world changes, and consequences that make places feel coherent and worth revisiting.
9. **Personal journeys and memory** — the learner's own discoveries, stories experienced, games played, creations, skills demonstrated, meaningful choices, and relationships. Preserve this history honestly and privately.

### Story system requirements

Treat narrative as a dedicated product system, not merely a set of dialogue prompts attached to residents. It should support:
- World-level mysteries and long-form arcs that unfold over time.
- Local stories rooted in particular places, cultures, histories, and events.
- Main stories, optional side stories, spontaneous encounters, seasonal stories, and replayable story experiences.
- Story delivery through scenes, exploration, objects, letters, audio, environmental clues, performances, games, and character interactions.
- Clear separation between authored narrative canon, learner-specific choices, runtime state, and generated dialogue.
- Continuity checks so a story does not contradict established events, character knowledge, or the learner's prior choices.
- Language-learning goals integrated naturally into story participation without turning every narrative beat into a compulsory test.

### Games system requirements

Treat games as a broad, authored catalogue with reusable interaction patterns and clear learning intent. Each game should specify its purpose, language skills, input modes, feedback, difficulty adaptation, accessibility alternatives, replay value, save behaviour, and relationship to the world. Include both short spontaneous play and deeper multi-stage experiences. Avoid making XP, streaks, leaderboards, or unlock grinding the reason to play.

### Product balance and acceptance tests

The product should pass these qualitative checks as it grows:
- A learner can have a meaningful session exploring, discovering, creating, or playing without needing a resident conversation.
- A learner can follow a story whose central mystery or events are not simply about Cassidy.
- Cassidy remains emotionally central without being forced into every scene or every activity.
- Residents are not the only characters; the universe can also contain travelers, visitors, groups, creatures, historical figures in stories, and other forms of life appropriate to each world.
- A game is worthwhile because its play and learning experience are satisfying, not because it awards points.
- The world has things to discover and stories to tell even when the learner has already met its main residents.
- Different language worlds have distinct story traditions, game forms, places, cultures, and learning opportunities rather than sharing one template with translated labels.

The first vertical slice remains deliberately small, but its architecture must leave room for all these pillars. It must not hard-code the product around Cassidy conversations and resident routines.



## 25. Source audit: stories and games are present as separate product concerns, but maturity varies

A targeted read-only inspection of the GoPAL-AI source tree found a substantial game catalogue and several story-related modules. This supports carrying stories and games forward as first-class pillars, while also showing why source presence must not be mistaken for a finished, integrated experience.

### Games: broad catalogue, incomplete proof of depth

Inspected files include:
- `src/engines/world/worldMiniGameEngine.ts` — defines game kinds, families, skills, difficulty labels, and game definitions. Its families include discovery, puzzle, arcade, social, listening, adventure, and creative.
- `src/engines/world/worldMiniGameCatalog.ts` — provides a catalogue of named concepts such as word hunts, sign spotting, phrase puzzles, listening challenges, dialogue scenarios, mystery/adventure formats, and creative activities.
- `src/engines/world/worldMiniGameSelectionEngine.ts` — selects games using skills, preferred family/game, estimated time, recent play history, cooldowns, and novelty. It also currently restricts this mini-game selection path to fictional locations.
- `src/features/world/data/livingWorldGameplay.ts` and `livingWorldEvents.ts` — define gameplay objects and event types for triggers, puzzles, collectibles, portals, checkpoints, game starts/completions, and related interactions.

**Audit interpretation:** the old project contains more than a simple quiz list. It has the beginnings of a multi-family game system and a world-gameplay vocabulary. But catalogue entries and type definitions do not prove that every listed game has a complete playable loop, polished interaction, accessible alternatives, balanced difficulty, persistence, or meaningful learning evaluation. Those must be traced game by game before calling them implemented.

For Language-world, design a curated game portfolio with a smaller number of genuinely satisfying, reusable interaction systems first. The catalogue can grow over time. Each game should be independently valuable, contextually placed where appropriate, and capable of supporting different languages and input modes without becoming a reskinned multiple-choice quiz.

### Stories: more than resident dialogue, but not yet a complete narrative platform

Inspected files include:
- `src/engines/world/worldStoryChoiceEngine.ts` — a small branching-choice state model with node IDs, choice history, numeric flags, and completion state.
- `src/engines/world/residentStoryEngine.ts` — three fixed resident-linked story threads in the inspected source, with seeded/waiting/ready/resolved stages and a simple elapsed-time follow-up.
- `src/engines/world/worldEventDirectorEngine.ts` — coordinates ambient world events and opportunities; its own comment explicitly leaves quests, festivals, inventory, and rewards to separate systems.
- `src/engines/quest/questEngine.ts` — includes story as one quest category, alongside daily, cultural, conversation, exploration, and personal categories.
- `src/features/learning/components/WorldStoryChoiceBoard.tsx` and `src/features/world/components/WorldStoryTraceLayer.tsx` — indicate story-choice and environmental story presentation surfaces exist in the source tree.

**Audit interpretation:** there are story fragments, resident threads, branching-choice primitives, quest hooks, and world-story presentation components. The inspected story-choice engine is deliberately small; the resident-story engine is a fixed template set tied to particular residents. These are useful prototypes and evidence of intent, not proof of a robust world-scale narrative system with long arcs, canon management, branching continuity, independent stories, or reliable save/recovery.

For Language-world, narrative must be a dedicated system that can run through places, mysteries, objects, exploration, games, letters, performances, environmental clues, and characters. Cassidy may be involved in many important stories, but she must not be a mandatory gateway to all stories. Some stories should be about the world, its history, cultures, conflicts, creatures, and other characters; some should be personal; some can be playful or self-contained.

### Required next verification

Before adopting any old feature as a proven implementation, trace:
- Which game definitions have actual runtime implementations and reachable entry points.
- Which gameplay events are emitted, consumed, persisted, and restored.
- Whether story traces and choice boards connect to durable story state.
- Whether story progress survives app restart and is scoped to the learner.
- Whether world events, quests, games, and stories can create consistent consequences without duplicate rewards or contradictory state.
- Whether each interaction has accessibility, non-timed, and low-confidence learner paths.

All source inspection above was read-only. No GoPAL-AI files, assets, pipelines, or runtime code were changed or adopted.


## 26. Integration checks: visible components do not yet prove complete gameplay or narrative continuity

A second source pass inspected the root app, world presentation components, story UI, and mini-game runtime registry.

### Concrete findings

- `App.tsx` mounts the old app's Explore, Travel, Cassidy, and Study Room primary surfaces, with Museum, Characters, and Settings as secondary destinations. This reinforces that the old product was a multi-surface application, not a single resident-chat loop. The new product should make the universe itself the primary experience.
- `LivingGameWorld.tsx` composes a visual world layer with a gameplay layer, but the inspected component alone does not prove that every gameplay definition is reachable or interactive.
- `LivingGameplayLayer.tsx` explicitly sets `pointerEvents="none"`; it renders marker graphics rather than handling player interaction. It also returns no gameplay markers for `emerald-village`. These markers must not be mistaken for a functioning interaction system.
- `WorldStoryChoiceBoard.tsx` creates its story state with component-local React state. The inspected component does not itself persist choices or restore a story after restart. A caller may add other persistence, but that must be verified at the call site before continuity is claimed.
- `WorldStoryTraceLayer.tsx` is wired to the resident-story engine and has fixed screen positions for three named resident threads. This is a narrow resident-story presentation, not a general world narrative layer.
- `worldMiniGameRuntimeRegistry.ts` maps catalogue entries to named mechanic categories and currently sets the registry binding's `implemented` field to true when creating each binding. This is a declaration/registry assertion, not independent test evidence that each game has a complete, accessible, correctly persisted runtime. The registry's claim must be checked against actual mechanic dispatch, screen entry points, tests, and successful play paths.

### Revised implementation-confidence judgement

| Area | Evidence from inspected source | Confidence in complete end-to-end experience |
|---|---|---|
| Game catalogue | Broad catalogue with multiple families and skill tags | High that catalogue concepts exist; low that every entry is a finished game |
| Game selection | Skill/family/time/novelty/recent-history selection logic | Medium for selection logic; runtime integration still needs tracing |
| Game runtime registry | Many catalogue-to-mechanic bindings declared | Low until each mechanic and entry path is tested |
| World gameplay markers | Marker definitions and visual rendering | Low; inspected layer is non-interactive and hidden in Emerald Village |
| Branching story primitive | Local node/choice/flag state transition | High that a primitive exists; low for durable narrative continuity |
| Resident story threads | Three fixed templates and timed stages | High that this narrow prototype exists; low for a broad story universe |
| General narrative platform | Story components and traces exist | Not established by inspected evidence |

### Language-world consequence

Do not reproduce these limitations. The new project needs distinct, testable subsystems for:
- Authored story content and story-canon validation.
- Narrative runtime state, choice history, branching, and recovery.
- World events and story triggers.
- Game catalogue, actual playable mechanic implementations, and game progression.
- Shared learning evidence and accessibility services that games and stories can use without becoming dependent on one another.
- A world interaction layer that is genuinely interactive, not only decorative markers.

The systems should connect through explicit events and stable contracts, while remaining independently usable. For example, a learner might discover a mystery through exploration, solve part of it in a game, learn more from an old recording, and later discuss it with Cassidy or a resident. No single character or UI surface should own that entire experience.


## 27. Learning, creativity, festivals, and activity surfaces: second-pass evidence

The master blueprint's wider experience inventory is not limited to Cassidy and residents. A targeted source pass inspected the Study Room, creative studio, festival experience, world screens, and the blueprint's own acceptance gates.

### Study Room and focused practice

`src/features/study/screens/StudyScreen.tsx` is a real screen component with:
- Matcha Workshop, Calligraphy Studio, Pitch Trainer, and Soundscape Mixer entry controls.
- Cassidy's study-room presence and study objects.
- A short set of quick-practice prompts.

Important limitation: the inspected quick-practice completion state is component-local React state. Toggling an item changes its visual state, but this file does not persist that practice evidence. The four workshop controls open separate modals, which must be audited independently for complete learning, accessibility, and persistence. Therefore the Study Room is a connected surface, but not every item displayed there is a durable learning system.

### Creative Studio

`src/features/learning/components/CreativeStudioModal.tsx` supports choosing a creation template, visual theme, title, content, and tags, then calls `CreationStudio.createArtifact`. It is stronger evidence than a static mock-up: a save operation is wired to a creation domain service and returns a created artifact to its caller.

Still to verify: the creation service's storage guarantees, schema/versioning, reopen/edit/delete/export flows, asset handling, learner ownership, and the Memory Museum's ability to display the same artifact after restart. The inspected UI also writes a subtitle saying the work was created with Cassidy; Language-world should allow learner-led creation without making Cassidy a required co-author.

### Seasonal festivals

`src/features/world/components/SeasonalFestivalModal.tsx` presents a seasonal festival catalogue and a celebrate action. That action claims a reward through the economy service, then writes a postcard creation and a world memory when the claim is new.

This demonstrates a multi-system activity concept (festival → reward claim → creation → memory), but the component's `celebrated` display state is local. The durable claim key appears to be the duplicate-reward guard; the actual festival state, event history, and return-visit consequences need separate verification. The current memory text explicitly frames the festival as celebrated with Cassidy and residents. The new product should also support festivals and events that the learner can enjoy independently, with Cassidy present when it is natural—not forced into every activity.

### Emerald Valley screen and interaction boundary

`src/features/world/screens/LivingValleyScreen.tsx` mounts a world viewport, world runtime, environment resolution, continuity return, and opportunity panel. It builds a place-selection panel when a building is pressed. In the inspected component, however, the building panel only displays an ID and generic description, with a "Keep wandering" close action. This is not evidence that each building has a meaningful interior, activity, story, game, or object interaction.

The world screen is a useful structural starting point in the old implementation, but Language-world must define a genuine interaction contract: object identity, available actions, preconditions, feedback, consequences, persistence, and accessibility—not merely tappable scenery.

### Master blueprint acceptance gates

The old master blueprint explicitly states that every feature should have a reachable route, successful happy path, loading/error/empty states, persisted outcome, restart/re-entry behaviour, accessibility, offline policy, automated test, and documented owner. Its broader principles—privacy controls, data minimization, screen-reader support, scalable text, reduced motion, captions/transcripts, adjustable audio, and alternatives to timed gestures—remain valid acceptance requirements for Language-world.

### New-project product implications

- A feature inventory is not a release checklist. Each experience needs an end-to-end evidence record.
- Games, stories, workshops, creative tools, festivals, exploration, and conversations should all be able to produce meaningful learner-owned outcomes.
- Activities should be discoverable from the world and also accessible through appropriate focused spaces; neither a dashboard nor a single world scene should become the only interaction pattern.
- Cassidy can encourage, join, teach, react, or simply share the moment. The learner must retain agency to explore, play, create, and learn without requiring her presence in every loop.
- Each world should author its own festival calendar, story traditions, games, creative forms, and cultural material; Emerald Valley's Japanese-inspired motifs must not become the template for every language world.

No GoPAL-AI files were changed. This remains static source inspection; no runtime, persistence restart, device, or build test was performed.


## 28. Learning loop, evaluation, creation storage, and personal archive

A targeted read of the learning session UI, evaluation engine, world-learning completion flow, creation service, and Memory Museum reveals both a meaningful end-to-end ambition and important limitations.

### Contextual learning session

`src/features/learning/screens/LearningScenarioModal.tsx` uses a learning-session hook and tutor engine. The inspected UI starts a scenario when opened, accepts typed learner responses, supports hints and translation visibility, shows feedback and cultural insight, and allows the learner to continue through dialogue turns. This is a real interaction surface rather than only a design document.

The contextual moment builder in `src/engines/learning/contextualLanguageLearningEngine.ts` can create place- and skill-specific moments for vocabulary, listening, speaking, reading, grammar, and writing. It uses authored world scenarios when a matching skill exists and otherwise falls back to generated prompt templates.

### Evaluation limitations

`src/engines/learning/learningEvaluationEngine.ts` evaluates input using normalized strings, a finite hard-coded set of concept variants, expected-concept matching, and sample-response matching. It also derives partial-understanding, confidence, difficulty, and hint-dependency fields.

This is a useful deterministic prototype, but it is not proof of robust semantic understanding or speech/pronunciation assessment. The inspected variants include Japanese-specific terms and transliterations. Language-world needs language-specific evaluation strategies, explicit accepted-answer variants, morphology/orthography handling, context-sensitive alternatives, transparent confidence, and human-reviewed quality tests. Do not mark a valid learner response wrong merely because it differs from one memorized string.

### Completion flow and cross-domain effects

`src/engines/learning/worldLearningFlowEngine.ts` connects a completed scenario to capability evidence, learning integration, resident relationship effects, Cassidy interaction/reaction, and a world consequence. It uses a persisted completed-key list and an in-memory in-flight set to reduce duplicate processing.

This is strong evidence of the intended product loop: learning should affect more than a score. But the operations span several services and are not one atomic transaction. A process interruption after some side effects but before the completed key is saved can leave a partial outcome that may be retried. The in-memory in-flight set does not survive restart. Language-world should use a durable, idempotent workflow/outbox with per-step status and recovery, and separate learner skill evidence from relationship or world-event side effects.

### Creation service and Museum

`src/engines/creation/creationStudio.ts` saves an artifact through `LocalStore.addCreation` and then writes a Journey event. It exposes a method to retrieve creations. The Memory Museum reads postcards, creations, cultural artifacts, and memories on mount, then presents category tabs.

This demonstrates a connected creation-to-archive path at source level. It does not yet establish edit/reopen/export/delete workflows, asset-backed artwork, robust error handling, account scoping, or refresh when the Museum is revisited while still mounted. The new project should treat learner creations as owned personal works with versioning, attribution choices, privacy, export, and durable access—not just text records in a collection.

### Learning product requirements carried into Language-world

- Support typed, spoken, listened, read, written, visual, spatial, and creative responses as appropriate to each activity.
- Separate a learner's attempt, evidence of understanding, confidence, hint use, and final mastery estimate.
- Treat errors as useful evidence, never as a reason to punish Cassidy's relationship or remove world access.
- Accept multiple natural answers and dialect/register variation where appropriate.
- Make evaluation uncertainty visible; do not claim pronunciation precision unless validated against appropriate audio data and tests.
- Persist transcripts and learner-owned creations with consent, clear retention, account isolation, and recovery.
- Make world consequences and personal-history updates recoverable and idempotent.
- Build each language world's learning and evaluation content with language-specific expertise rather than translating a single Japanese-first template.

Static inspection only. These files were read from GoPAL-AI; no source code was copied or modified there.


## 29. Speech, audio, navigation games, object interaction, and world simulation

This pass inspected the old audio contracts/runtime, pitch-shadow trainer, audio-navigation activity, object interaction layer, event bus, quest runtime, discovery progression, and environment resolver.

### Speech and pronunciation: concept exists; assessment is not established

- `PitchShadowTrainerModal.tsx` contains three Japanese minimal-pair examples (雨/飴, 箸/橋, 今/居間) and pitch-pattern labels. Its practice action immediately displays a positive feedback sentence and increments a local counter. Every second tap awards Sparkles.
- The inspected practice handler does not record microphone input, analyse a waveform, compare learner speech, or calculate pitch accuracy. It is a guided concept demonstration, not a verified pronunciation assessment.
- The world experience interaction panel supports typed answers and guided choices. Its copy mentions speaking as an option, but the inspected component itself only implements text entry and choice buttons.

**Language-world requirement:** distinguish listening/repetition practice from actual speech recognition and validated pronunciation feedback. Start with reliable listen, replay, shadow, syllable/phoneme visualisation, and learner self-comparison where appropriate. Add microphone assessment only after a real audio capture/analysis pipeline is selected, tested across devices, accents, noise conditions, and accessibility needs. Never award a correctness claim based only on a button press.

### World audio: thoughtful mixing design, playback adapter, and a legacy platform dependency

The old world-audio contract models music, ambience, location, activity, interaction, transport, voice, and event categories; priorities, spatial positions, attenuation, quiet mode, and per-location profiles are present. The resolver applies category gains, distance attenuation, priority, and cooldowns. A separate runtime adapter owns player lifecycle.

However:
- The inspected playback adapter imports `expo-audio`, which is not eligible for the new no-Expo project.
- The simpler `AudioEngine.playSoundEffect` only logs a message; it does not play an audio asset.
- Audio cue resolution can return a request, but a successful audible experience still depends on a valid asset resolver, actual assets, platform player behaviour, lifecycle cleanup, focus/interruption handling, and device testing.
- Profiles are authored for several generic location types, but their presence does not establish a complete soundscape for every language world.

Carry forward the product concepts—layered sound, spatial cues, location identity, quiet mode, category controls, and audio accessibility—but design a fresh engine-agnostic audio service and native playback adapter after engine selection.

### Audio navigation: useful game idea, logic needs correction

The audio-navigation activity presents a spoken-clue route between landmarks, but the inspected `chooseWaypoint` function is effectively a no-op. In the board, the expected next waypoint is inferred from array order; when no next waypoint exists, the selection handler falls back to the selected ID as the expected ID, so a final choice can be accepted without a meaningful final-target check. The activity also renders text clues; the inspected board does not itself play spoken audio.

This is a good example of why a visible game screen and a runtime registry's `implemented: true` flag are not acceptance evidence. Language-world games need explicit route graphs, valid transitions, audio playback verification, retry/skip/accessibility paths, and unit tests for wrong, repeated, branching, and terminal choices.

### Object interactions and environmental props

The old source has a typed world-object interaction model with target kinds and available actions, plus a nearest-object lookup based on distance and interaction radius. This is a useful interaction contract concept.

But the inspected `LivingPropInteractionLayer` is visual-only (`pointerEvents="none"`) and creates four resident-linked decorative props (tea station, book clue, lantern hook, garden water) based on resident activity. It is not itself an interactive object system. The separate world interaction model is a stronger foundation concept, but its actual caller, action dispatch, persistence, and visible consequences need end-to-end tracing.

### World events, quests, discovery, and time

- The living-world event bus has a broad event vocabulary for discovery, collection, dialogue, quests, travel, object activation, activities, games, and learning. It is synchronous and in-memory; it is not a durable event log.
- `LivingWorldQuestEngine` stores quest states in a private in-memory Map. It emits start/completion events, but the inspected class has no persistence adapter of its own. A caller may serialize state, which remains to be verified.
- The separate `QuestEngine` stores quests through LocalStore and has a durable reward-claim key, but its seed data begins with several quests already completed. This is unsuitable as a clean first-time learner state without a seed-state redesign.
- Discovery progression persists completed/discovered IDs locally and maps canonical place IDs, but the inspected resolver explicitly has a Japanese/French special path while other worlds use a different fallback path. Language-world needs a consistent world-independent discovery contract and per-world authored content.
- The old environment resolver derives season and time from the device date and picks deterministic weather from a small season list and day/hour bucket. This is a lightweight atmosphere selector, not a climate or ecological simulation.

### New-project acceptance requirements

1. Audio must produce verified sound on target Android hardware, respond correctly to interruptions/focus changes, support per-category controls and quiet mode, and release resources safely.
2. Every speech feature must state whether it is playback, self-practice, transcription, speech recognition, or measured pronunciation; do not blur these categories.
3. Navigation and puzzle games need tested state transitions, explicit graph rules, restart recovery, and non-audio alternatives.
4. Decorative props and tappable objects must be separate concepts. Interactive objects need action dispatch and observable, persistent outcomes.
5. Durable world/quest state must not depend solely on an in-memory event bus or private Map.
6. First-run state must be genuinely new; demo completion, rewards, memories, and unlocks must not leak into a new learner's journey.
7. Time, weather, and season must be world-authored and deterministic where appropriate, with bounded offline simulation and explicit timezone/device-clock policies.

No old source, asset, renderer, or runtime was changed or copied. These are static inspection findings only; no microphone, audio hardware, Android build, or persistence restart test was performed.


## 30. GoPAL-AI archive review: cinematic experience, travel, and replaceable assets

**Source:** read-only review of `jamlove1318-lab/GoPAL-AI`, including its 608-file tree, master product specification, project overview, Cassidy bible/checklist, Emerald Valley world specification, mini-game catalogue, audio/animation/asset strategy documents, and representative source systems.

### Product requirements recovered

1. The first meeting is a dedicated staged experience, not a conventional onboarding form. Cassidy should introduce herself, guide the learner through Emerald Valley as the home world, show what can be explored and done there, and explain how travel to other language worlds works.
2. The opening sequence must be versioned, skippable, replay/re-entry safe, accessible, and persisted exactly once. It should leave a meaningful shared memory without trapping the learner in a long unskippable movie.
3. Language-world travel is a journey: station/terminal approach, departure preparation, boarding, vehicle interior/exterior, route montage, world-boundary transition, arrival, environmental reveal, and handoff into the playable destination.
4. Transport is a world experience, not only a route icon. Train and plane travel can connect worlds; buses, cars, boats, bicycles, and walking can serve appropriate in-world journeys.
5. Resident introductions can use anticipation, environmental clues, sound, silhouettes, camera reveal, character entrance, first interaction, and persistent follow-up.
6. Cassidy can invite the learner into secret places and her own stories/adventures, but the wider universe must also support stories, games, mysteries, creatures, and exploration independent of her or any resident.
7. Cinematic sequences need authored shot/timeline data, camera choreography, actor blocking, animation and expression cues, dialogue/subtitles/voice, audio/lighting/environment cues, preloading, skip/replay, checkpoints, interruption recovery, and reduced-motion alternatives.

### Existing GoPAL evidence (not reusable implementation)

- `cassidyWelcomeEngine.ts` contains a versioned welcome script and persistent first-meeting memory.
- `CassidyFirstMeetingCinematic.tsx` provides an animated dialogue presentation. The inspected script does not stage the complete Emerald Valley tour or demonstrate world travel.
- `destinationDepartureSceneEngine.ts` and `destinationArrivalSceneEngine.ts` define scene beats/shots, but these contracts do not prove a full vehicle journey.
- `WorldEntranceTransition.tsx` is a short title/fade transition, not a train or plane cinematic.
- `livingWorldTransport.ts` and `livingWorldVehicles.ts` define transport/network and vehicle data; the inspected render layers rely on an existing runtime and do not establish a complete boarding-to-arrival cinematic.
- `worldAnimationContract.ts` and the old animation-pipeline document describe semantic animation intent and layered motion. Their implementation and toolchain are explicitly excluded.
- The old audio architecture describes semantic location/transport/event layers, spatial attenuation, cooldowns, and crossfades. Its Expo playback runtime is excluded.

### New project decisions

- Add a dedicated Cinematic Director and reusable sequence authoring format; do not scatter cinematic timing across individual screens.
- Add a Travel Director that coordinates route state, vehicle state, boarding, departure, journey beats, arrival, destination reveal, and restart-safe handoff.
- Keep world simulation and durable state authoritative. Cinematic presentation may temporarily direct camera/actor performance but must not own persistent world progression.
- Design every sequence to work with temporary assets first and later designer-made assets through stable semantic asset IDs.
- Define asset binding for character rigs, skeleton compatibility, animation names/actions, camera framing, pivots, scale, collision/interaction targets, LODs, variants, audio, and fallbacks.
- Require placeholder-to-final replacement tests for Cassidy, a resident, a building, a train/vehicle, a prop, an environment asset, and an animation without gameplay-code rewrites.
- Engine selection remains open. No GoPAL production pipeline, renderer, model, rig, animation export, asset factory, validator, manifest contract, or Expo runtime may be adapted.

### Verification status

Product requirements recovered from source documents: high confidence. Existing first-meeting and transport foundations inspected: static source only. Full cinematic execution, actual train/plane journey, scene interruption/recovery, designer asset replacement, and Android performance remain unverified and are new-project acceptance requirements.


## 31. Narrative, quest, world-event, and creature foundations in the archive

### Source systems inspected

- `npcCharacterRegistry.ts` — generic NPC identity templates and world/role registration. Roles include residents, teachers, guides, merchants, quest-givers, travelers, guards, farmers, sailors, pilots, engineers, scientists, royals, villagers, and tourists.
- `livingWorldBehavior.ts` — generic idle, wander, patrol, follow-route, schedule, traffic, orbit, animate, spawn, and despawn behavior declarations, with daily schedule examples.
- `livingWorldEvents.ts` — typed event vocabulary for interaction, discovery, collection, learning, dialogue, quest, travel, boarding/riding, object activation, actor lifecycle, activities, mini-games, checkpoints, and language practice.
- `worldEventDirectorEngine.ts` — combines a contextual ambient event with world opportunities; explicitly leaves quests, festivals, inventory, and rewards to other owners.
- `residentStoryOpportunityEngine.ts` — maps resident relationship tone to a meeting, recognition, shared moment, or personal invitation beat.
- `livingWorldQuestEngine.ts` — objective types include discover, collect, talk, learn, travel, play, activate, and enter. Its inspected implementation keeps quest state in a private in-memory `Map`.
- `worldStoryChoiceEngine.ts` — small branching state helper with node ID, choice history, numeric flags, and completion.
- `worldInvestigationEngine.ts` — small clue collection/prerequisite/reveal state helper.

### What this reveals

GoPAL anticipated a much wider world than the implemented story UI alone suggests: characters with different roles, schedules and behaviors; contextual world events; clues and investigations; story choices; quests that react to many kinds of actions; and resident invitations that change with familiarity.

However, these pieces are separate primitives, not proof of one complete narrative/event simulation. The inspected world event bus is synchronous and in-memory; generated event IDs are runtime-random/time-based; the local quest class has private in-memory state; the story and investigation helpers are pure state transforms without durable storage or authored-canon validation. They need a new durable event and narrative architecture rather than direct reuse.

### Additional gap: creatures and wildlife

The inspected repository inventory contains general NPC/character systems and nature/environment assets, but no clearly established, dedicated creature/wildlife ecology system was identified in the source areas reviewed. A few generic character roles do not amount to a creature system.

Language-world should explicitly plan:
- species and individual creature identities;
- habitat, diet/needs, activity rhythms, social behavior, migration/seasonality where relevant;
- discovery, rumor, tracks/calls/silhouettes, reveal and safe observation;
- creature movement, locomotion/animation, sound, interaction, and relationship rules;
- hostile, neutral, helpful, guardian, and rare roles with age-appropriate boundaries;
- world-specific ecology and causal effects on plants, places, weather, and resident stories;
- speaking creatures only where authored fiction supports it, not as a universal default.

Creatures should be introduced gradually through world clues and stories before every creature is openly visible. They should not be reduced to collectible skins or generic enemies.

### New-project requirements

1. Make narrative canon and event history durable, versioned, idempotent, causally linked, and recoverable after interruption or process death.
2. Distinguish authored story truth, generated presentation, player choice, derived state, and temporary scene state.
3. Keep resident-linked stories, Cassidy stories, independent place/object mysteries, creature stories, and world-scale arcs as separate supported content categories.
4. Provide clue/evidence provenance and planned resolution for every major mystery.
5. Ensure a quest can be paused, resumed, abandoned where appropriate, and restored without duplicated rewards or lost objectives.
6. Use schedules and ambient behavior as inputs to world simulation, not as an excuse for arbitrary background state mutation.
7. Add a first-class creature/ecology domain rather than hiding wildlife inside generic NPC records.

These are design requirements recovered from the archive and the user's wider universe direction; none of the old implementations or runtime code is being reused.


## 32. Cassidy: life, autonomy, memory, and the actual character experience

### Source systems inspected

- `cassidyLifeEngine.ts` — chooses one of a fixed set of activities using learner state, weather, hour, personality thresholds, and a seed.
- `cassidyLifeStateEngine.ts` — persists current activity, mood, world/place/anchor, visit count, invitation/interaction timestamps, and dream/story/adventure seeds in LocalStore under a user key.
- `cassidyPersonalityEngine.ts` — persists six numeric traits, favorite worlds/activities, shared moment count, and a bounded list of processed event IDs.
- `cassidyPerceptionEngine.ts` and `cassidyAutonomyEngine.ts` — turn a small context snapshot into prioritized cues and an action decision.
- `cassidyActionEngine.ts` and `cassidyPresentationEngine.ts` — map the decision into fixed text, a visual action, and presentation mode; action execution writes life state and emits an event.
- `cassidyPresenceDirectorEngine.ts` — chooses activities with a 15-minute minimum stay and 30-minute invitation cooldown; may create a dream/story/adventure moment when activity changes.
- `cassidyLifeDirectorEngine.ts` — stores up to 20 recent moments and uses small fixed dream/story/adventure template arrays. It adds up to three recent memory facts to the prompt and records a memory/personality update.
- `cassidyNarrativeExperienceEngine.ts` — separate user-keyed narrative list with fixed templates.
- `cassidyInteractionLifecycleEngine.ts` — records memory, updates relationship, evolves personality, then marks the interaction processed.
- `cassidyExperienceCoordinator.ts` — filters meaningful activities and routes them to interaction recording.
- `cassidyCharacterRuntimeEngine.ts` — in-memory snapshot for world presence, expression, animation, outfit, visibility, and transition counter.
- `cassidyRuntimeSessionEngine.ts` — restores/enters/returns a session from life state.
- `cassidyWorldPresenceEngine.ts` and `cassidySceneAnchorEngine.ts` — produce world/context-specific lines and presentation anchors.
- `CassidyHomeScreen.tsx` and `CassidyVisualPresence.tsx` — a separate room experience and visual component; the visual component routes through old 2D/3D presentation code.

### Strengths worth preserving as requirements

- Cassidy has a life outside direct learner interaction: wandering, reading, visiting a café, watching rain, stargazing, dreaming, storytelling, resting, discovering, helping, and celebrating.
- Her presence is context-sensitive and includes explicit quiet/space-giving behavior.
- Invitations have a cooldown; a minimum stay reduces rapid activity switching.
- The archive distinguishes meaningful experiences from ordinary ambience.
- There are user-keyed life state, narrative history, interaction memory, and some deduplication.
- Her current world/location and scene anchor are represented separately from her visual animation/expression.

### Important weaknesses and gaps

1. Activity choice is still a small deterministic/template-driven selector, not a rich model of motives, plans, commitments, needs, relationships, or evolving personal goals.
2. Dream/story/adventure content comes from short fixed arrays. Memory is appended as a few facts, not woven through a validated long-form story with authored canon and causal continuity.
3. Personality is expressed as numeric traits with small fixed increments. This is not sufficient as the authoritative definition of a nuanced character and can create artificial score-like behavior.
4. Multiple overlapping systems exist for life, autonomy, presence, narrative, action, presentation, runtime, session, world presence, and interaction lifecycle. Their ownership and call graph must be unified.
5. `cassidyCharacterRuntimeEngine` is in-memory presentation state. It does not provide a complete physical character controller, locomotion, pathfinding, animation graph, gaze, interaction targeting, or cinematic performance.
6. The inspected `CassidyHomeScreen` is a separate themed room with local state and a visual presence; it is not evidence of a continuous embodied Cassidy moving through all world scenes.
7. Interaction processing writes memory, relationship, personality, and dedupe state in sequence. These writes are not one atomic transaction; a failure between steps can leave partial side effects.
8. Dedupe state is bounded and some in-flight coordination is process-local. Recovery after process death and long-term idempotency need a durable event/outbox design.
9. The fallback identity `local-explorer-user` appears in multiple Cassidy paths. New user identity must be explicit and strictly scoped; no shared fallback profile may leak data between learners.
10. The current invitation and presence timing relies on device wall-clock time. The new world simulation must define clock/timezone/offline progression and prevent clock changes from creating arbitrary life events.

### New Cassidy architecture requirement

Design Cassidy as one coherent character domain with separate, explicit layers:
- canonical identity, values, boundaries, voice, history, and authored character canon;
- perception of world, learner context, other characters, and events;
- motives, needs, commitments, plans, and restrained autonomy;
- physical presence, navigation, locomotion, gaze, gestures, expression, and animation requests;
- conversation/dialogue generation and localization;
- personal memory and shared memory with provenance, confidence, privacy, and retention;
- relationship expressed through accumulated shared experiences rather than a visible score;
- life simulation that can continue when the learner is away, within bounded and deterministic rules;
- cinematic performance interface that can direct Cassidy without owning her identity or persistent state.

Cassidy must remain recognizably herself across scenes, worlds, stories, and time. She should sometimes initiate an adventure, sometimes be occupied with her own life, sometimes accompany the learner, and sometimes leave the learner to explore independently.

**Do not reuse the old Cassidy runtime, renderer, model, rig, animation exports, visual resolver, production factory, or pipeline.** Her approved character bible is a creative reference only; the new physical model, rig, animation library, and runtime are produced independently.

## 33. Language-world identity and travel: archive evidence versus actual distinct worlds

### Source systems inspected

- `livingLanguageWorlds.ts` registers Emerald Valley, Japanese World, and French World. The inspected registry does not register Spanish World.
- `livingLanguageWorldLocations.ts` contains Japanese and French real/fictional location entries with experience tags and unlock order.
- `livingLanguageWorldPhysical.ts` generates a small generic set of physical features and characters for each location. Resident identities are generated from a city label (for example, a generic city local), with generic guide/teacher roles and shared schedule IDs.
- `languageWorldEngine.ts` has a separate language-world model for Japanese, Spanish, French, and Korean. Spanish has named cities such as Seville, Barcelona, Mexico City, Medellín, and Buenos Aires, but this model is not the same registry as the physical-world registry.
- `languageWorldStateEngine.ts` persists a selected language-world ID in a single AsyncStorage key, defaulting to Japanese.
- `LanguageWorldPhysicalScreen.tsx` displays a place/discovery map and uses a short `WorldEntranceTransition`; it does not itself demonstrate a complete 3D physical world or cinematic journey.
- Transport network and vehicle catalogues contain railways, roads, runways, terminals, buses, boats, trains, cars, and aircraft across several location IDs. These are authored route/feature records and moving-vehicle data, not evidence of a complete world-to-world travel experience.

### Findings

1. The archive has the beginnings of a multi-language destination catalogue, but world identity is split across two registries with different IDs and supported languages.
2. Spanish and Korean exist in one engine model, but the inspected primary world registry only lists Japanese and French alongside Emerald Valley. This is a concrete integration gap.
3. Several location physical elements and residents are generated through generic templates. The data does not yet establish a distinct ecology, climate, architecture, culture, soundscape, settlement history, creature life, and activity design for each language world.
4. A location list with real-world place names is not a complete explorable world. It needs connected geography, scale, traversal, interiors, authored landmarks, world-specific object interactions, resident identities, and world-state consequences.
5. Transport network geometry and vehicle waypoint loops are useful prototyping data, but not equivalent to a route-aware travel director, boarding/alighting interaction, animated journey, departure/arrival cinematic, or restart-safe travel transaction.
6. The current location screen's discovery/entrance treatment is primarily a map/panel/short transition interaction. It is not the user's desired cinematic journey from Emerald Valley to a Spanish-speaking world by train.

### New project requirements

- Create one canonical world registry and stable world IDs across content, travel, save data, learning, localization, and asset bindings.
- Every world must have a complete world bible and a world identity acceptance test. A Spanish world must not be treated as a single generic Spanish aesthetic: regional cultures and geography should be represented thoughtfully and accurately.
- Distinguish world, region, settlement, location, building/interior, route, and activity as separate concepts.
- Build travel as a multi-stage experience with route/vehicle state, boarding, departure, journey, arrival, reveal, and safe playable handoff.
- Keep route and vehicle data engine-neutral; the selected engine's presentation layer animates it.
- Add creature/ecology and resident content as world-owned packages, not generic generated placeholders.
- Use world-specific music, ambience, voice, environmental audio, weather, and day/night behavior.
- Allow the learner to explore without being forced down a linear unlock path; unknown places can be discoverable through clues, travel, stories, and curiosity.

This section records static source findings only. The new project's world registry, physical worlds, and cinematic travel remain to be designed and tested.


## 34. Learning, capability evidence, investigation, and personal archive: further source trace

### Learning foundations inspected

- `adaptiveConversationEngine.ts` — selects guided/supported/natural/authentic conversation support from a single mastery value and place scenario.
- `learningNeedEngine.ts` — ranks place scenarios using scenario and skill capability states.
- `languageCapabilityEngine.ts` — stores attempts/successes for scenarios and skills, plus word/phrase counts, in one AsyncStorage key.
- `worldLearningOutcomeEngine.ts` — maps a scenario result to skill, place, language, world change, memory candidate, and follow-up.
- `worldLearningIntegrationEngine.ts` — records a learning memory and emits memory/world events.
- `worldLearningFlowEngine.ts` — coordinates capability, learning integration, relationship bridge, Cassidy reaction/interaction, and world consequence.
- `wordBankAnswerEngine.ts` — composes an answer from selected word indexes.
- `WorldInvestigationBoard.tsx` — a clue UI whose investigation state is held in component-local React state.
- `MemoryEngine` — uses Supabase when configured and LocalStore fallback otherwise.
- `CreationStudio` — provides postcard, phrase-card, memory-board, and comic-strip templates and saves learner artifacts through LocalStore.
- `JourneyBookScreen.tsx` — assembles a timeline, milestones, then-vs-now, cultural artifacts, and mastered knowledge nodes.
- `TimeCapsuleModal.tsx` — stores user messages with a target unlock date; the inspected demo unlock action can explicitly unlock a capsule before the target date.

### What is worth preserving

- Conversation support should adapt to capability, but should not force every interaction into a test.
- Learning needs can be selected from place, skill, scenario history, and what the learner is ready for.
- Learning outcomes can produce more than a score: they can change a world moment, create a memory, affect a character response, and suggest a meaningful next step.
- The personal archive should preserve creations, cultural artifacts, conversations, memories, discoveries, and then-vs-now growth.
- Learners should be able to create things independently, not only co-create with Cassidy.
- Investigation clues should be discoverable and reveal other clues, but the evidence trail must survive leaving the scene and reopening the app.

### Gaps confirmed or requiring further verification

1. Capability state uses attempts/success thresholds. This is useful as a lightweight prototype but is not a complete model of recall, receptive/productive ability, confidence, hint dependence, latency, context transfer, or durable mastery.
2. Capability storage is a single global key in the inspected engine, not visibly scoped by authenticated learner ID. That is a serious account-isolation requirement for the new project.
3. The learning flow coordinates multiple side effects. The previously documented completed-key list and in-flight set do not make the whole multi-service operation atomic; interruption/retry may leave partial writes.
4. The investigation board stores clue progress only in local component state. Closing/unmounting the board loses the in-progress state unless another caller persists it.
5. Memory fallback paths need careful account isolation: the inspected memory engine's LocalStore fallback APIs do not pass the user ID, and list fallback can return the generic local memory collection.
6. Creation Studio shows a useful start but the inspected API focuses on create/list-style artifact persistence. Full edit, version history, delete, export, embedded media lifecycle, account transfer, and sync conflict behavior remain unverified.
7. Journey Book loads personal records from multiple storage domains. It is a useful product concept but does not prove a unified archive with stable provenance and complete privacy/export/delete behavior.
8. Time capsule's demo unlock path allows early unlock. The production policy must distinguish testing/admin overrides from the learner-facing date/consent contract.
9. Language capability and learning evidence should not silently reset, leak across accounts, or become a single opaque mastery percentage.

### New-project requirements

- Use an explicit learner ID for every capability, memory, creation, investigation, journey, and capsule record.
- Separate attempts, responses, hints, confidence, evidence, skill dimensions, recall scheduling, and mastery estimates.
- Keep assessment transparent: accept valid natural responses, handle dialect/variant answers, show uncertainty, and distinguish unassessed speech from measured pronunciation.
- Persist clue/evidence progress with stable IDs and event provenance; support interrupted investigations and story re-entry.
- Use a durable event/outbox or transactional workflow for learning side effects, with idempotency and recovery.
- Treat learner creations and personal records as first-class user-owned data with edit/reopen/delete/export and media lifecycle.
- Build a single coherent personal archive that can present learning history, memories, creations, discoveries, cultural experiences, and meaningful world moments without turning the experience into a progress dashboard.
- Make time-based content rules explicit and testable; production users cannot bypass an unlock policy through a demo handler.

This is static source inspection. No production-quality learning assessment, account isolation, export/delete, or interrupted-flow recovery has been proven by this review.

## 35. World objects, buildings, interiors, and interaction contracts

### Source systems inspected

Read-only reference review covered:
- `src/features/world/data/livingWorldObjectCatalog.ts`
- `src/features/world/data/livingWorldObjectRegistry.ts`
- `src/features/world/data/livingWorldObjectFactory.ts`
- `src/features/world/data/livingWorldObjects.ts`
- `src/engines/world/livingWorldObjectsStore.ts`
- `src/engines/world/worldInventoryEngine.ts`
- `src/engines/world/worldCraftingEngine.ts`

### What the archive contains

The reference includes a broad reusable object vocabulary: buildings, interiors, terrain, decoration, infrastructure, transportation, characters, gameplay objects, fantasy objects, science-fiction objects, and nature. The registry derives archetypes from a catalog and also adds more specific building, prop, infrastructure, vehicle, character, and gameplay definitions.

A location factory combines several location data sources into a common object stream. Its object contract can express identity, category, type, transform, visual theme/variant, collision, interaction, behaviour, state, tags, and metadata. Buildings, props, infrastructure, transport features, vehicles, gameplay objects, and entrances can be assembled into a location.

The object store has user-keyed local records for a small set of persistent objects, with a simple growth counter and short memory list. Inventory and crafting are represented as pure state transformations: add/remove/check/combine items and consume recipe quantities to produce outputs.

### Strengths worth carrying forward as product requirements

- A common semantic object model can connect world-building, interaction, collision, behaviour, state, and metadata.
- Buildings and interiors should be first-class place concepts, not only decorative meshes.
- A reusable archetype vocabulary can speed up authoring while retaining bespoke authored places.
- Objects can carry meaningful histories, discoveries, growth, or state changes.
- Inventory and crafting can be useful where they support exploration, creation, restoration, puzzles, or cultural activities.
- Object and asset identity should be stable and separate from visual implementation.

### Gaps and cautions

- The universal catalog is a generic vocabulary, not a complete world-authoring standard. Its themes are broadly assigned, so it does not prove that each language world has culturally and geographically specific object sets.
- The factory combines multiple catalogs, but the inspected files do not establish a complete authoring validation workflow, versioned content packages, robust placement constraints, navigation integration, streaming, or a production-grade interior portal model.
- The persistent object store covers only a small sample and simple growth/memory fields. It does not establish a general object lifecycle, ownership policy, event history, provenance, conflict resolution, or cross-device durability.
- Inventory and crafting helpers are in-memory transformations. They do not provide persistence, transaction boundaries, unique-instance identity, provenance, rollback, or a complete user experience.
- The object catalog's breadth should not become pressure to include every category. Each object family must justify its role in the world and experience design.

### New Language-world requirements

1. Define semantic object identity, archetype, instance state, ownership, provenance, lifecycle, and interaction separately.
2. Specify building shells, entrances, interiors, portals, room transitions, occlusion, navigation, accessibility, and persistence.
3. Define a world-authoring standard with coordinate units, transforms, bounds, collision, interaction anchors, navigation data, streaming zones, and validation.
4. Make object state changes durable, learner-scoped where personal, and safe to replay after interruption.
5. Treat inventory/crafting as optional experience systems with explicit purpose, not assumed core mechanics.
6. Ensure every world has authored local object families and materials; reusable technical contracts must not homogenize visual identity.
7. Keep gameplay references semantic and independent of asset filenames, renderer nodes, and engine prefab paths.

## 36. Environment, clock, world events, festivals, and offline simulation

### Source systems inspected

Read-only reference review covered:
- `src/engines/world/environmentEngine.ts`
- `src/engines/world/livingWorldClock.ts`
- `src/engines/world/worldSimulationSnapshot.ts`
- `src/engines/world/persistentWorldStateEngine.ts`
- `src/engines/world/contextualWorldEventEngine.ts`
- `src/engines/world/worldEventDirectorEngine.ts`
- `src/features/world/data/livingWorldEvents.ts`
- `src/features/world/components/SeasonalFestivalModal.tsx`
- `src/features/world/data/livingWorldEvents.ts`

### What the archive contains

The reference has several overlapping environment/time concepts:
- A lightweight environment resolver maps a supplied JavaScript date to time of day, season, and deterministic weather selection.
- A separate living-world clock maps local device time to periods such as dawn, morning, afternoon, dusk, and night, with ambience and greeting text.
- A simulation snapshot contains world/place identity, local time, day phase, weather, ambient life values, atmosphere, resident motion, and update time.
- A persistent world-state record tracks place visits, discovered event IDs, resident relationship state, a simulation snapshot, and seen event IDs.
- A contextual event selector can choose weather details, ambient life, resident moments, encouragement/kindness, and rare surprises based on a snapshot and scene context.
- A world event director combines an ambient event with available opportunities while declaring that quests, festivals, inventory, and rewards belong to other systems.
- The event vocabulary includes entry/exit, discovery, collection, learning, dialogue, quests, travel, vehicles, object activation, world-state changes, actors, activities, games, and learning outcomes.
- Seasonal festival concepts include Japanese-language seasonal traditions, cultural vocabulary, a learner activity, a creation/postcard, a memory, and a reward claim.

### Strengths worth carrying forward as requirements

- The environment should influence visuals, sound, resident activity, and the feeling of a place rather than being a decorative weather icon.
- A coherent clock and environment context can coordinate multiple presentation systems.
- Ambient events should be sparse, contextual, and subordinate to player agency.
- Places can remember visits and discoveries.
- Seasonal events can connect culture, language, community, creative artefacts, and the changing environment.
- A world-event director can coordinate opportunities without owning the state of every domain.
- Offline behaviour needs an explicit bounded model.

### Gaps and cautions

- The inspected clock and environment use local device time. The snapshot's initial weather is a fixed clear default and its advance operation recreates a snapshot from the current date; this is not a complete meteorological or ecological simulation.
- Multiple overlapping time/environment models create potential disagreement unless a single canonical simulation-time contract is designed.
- The persistent world-state engine writes through a generic LocalStore memory collection and hardcodes `local-explorer-user`; it is not a reliable multi-account persistence design.
- World event IDs generated by the event helper combine wall-clock time and randomness. The event bus is synchronous and in-memory; neither alone guarantees durable, idempotent event processing.
- The inspected festival modal owns selected/celebrated UI state, directly calls an economy reward claim, then writes a creation and memory. This is a fragile cross-system workflow if any later side effect fails; it also illustrates why festival participation, rewards, and archive creation need a durable coordinated transaction.
- Festival examples are currently Japanese-specific and attached to Emerald Valley. They do not establish culturally accurate, independently authored festivals for every world.
- A rare event selector is not a complete ecology, resident simulation, or narrative system. Event frequency, cooldown persistence, fairness, accessibility, and replay need design.

### New Language-world requirements

1. Define one canonical simulation clock, with explicit world timezone policy, device-time trust, pause/background behaviour, and offline advancement.
2. Separate real-world time, authored world time, simulation time, and presentation time.
3. Define weather and seasonal systems per world, with authored climate rules and deterministic/reproducible state where appropriate.
4. Specify bounded simulation tiers: active scene, nearby region, distant world, and offline/hibernating state.
5. Define event identity, causality, persistence, deduplication, idempotency, cooldowns, expiry, replay, and interruption recovery.
6. Use domain-owned state: the event director may orchestrate but must not silently own quest, festival, inventory, learning, or relationship records.
7. Treat festivals as authored cultural experiences with research/review, activities, accessibility, optional learning, and persistent consequences—not merely reward modals.
8. Avoid time-limited pressure or penalties for absence. Seasonal experiences should be discoverable and revisitable under explicit design rules.

## 37. Audio, animation semantics, cinematic presentation, and accessibility

### Source systems inspected

Read-only reference review covered:
- `docs/world-audio-system.md`
- `src/engines/world/worldAudioContract.ts`
- `src/engines/world/worldAudioProfiles.ts`
- `src/engines/world/worldAudioEngine.ts`
- `src/engines/world/worldAudioRuntime.ts`
- `src/engines/world/worldAnimationContract.ts`
- `src/engines/world/worldAssetAnimationRouter.ts`
- `src/engines/world/residentAnimationDirector.ts`
- `src/features/cassidy/components/CassidyFirstMeetingCinematic.tsx`

### What the archive contains

The audio concept separates semantic audio decisions from playback. It defines categories for music, ambience, location, activity, interaction, transport, voice, and events; location profiles; mix levels; priority; spatial position; quiet mode; distance attenuation; cooldowns; and a maximum active one-shot budget. The audio design notes describe crossfading music, soft density, licensing/provenance, and future weather and acoustic-zone extensions.

The world animation contract describes semantic actions such as idle, walk, greet, listen, talk, discover, celebrate, inspect, sit, and stand. It also separates animation layers, target kinds, priority, and asset bindings. A clip router maps semantic actions to authored clip aliases. A resident animation director contains short trigger-based sequences.

The first-meeting cinematic is a screen-level staged introduction with character presentation, animated atmosphere, dialogue lines, progress, continue, skip, and a completion callback.

### Strengths worth carrying forward as requirements

- World audio should have one decision-making authority and a replaceable platform playback adapter.
- Locations need acoustic identity; sound should react to place, weather, time, movement, events, and transport.
- Mix headroom, density limits, cooldowns, quiet mode, and spatial attenuation protect the experience from audio fatigue.
- Semantic animation intent allows new art assets and animation sources to replace old ones without changing gameplay intent.
- Animation should support layered posture, gaze, face, gesture, locomotion, and environment behaviour.
- Important introductions deserve authored staging, pacing, character performance, and player-controlled progression.

### Gaps and cautions

- The reference playback adapter imports `expo-audio`. This is explicitly incompatible with the new project's no-Expo decision and must not be reused.
- The semantic audio contract is a useful design reference, not a commitment to the same implementation or exact gain values.
- The animation contract lists tool-specific source names and clip aliases. Language-world must define its own neutral asset/action vocabulary and runtime adapter boundary; it must not reuse the legacy pipeline or scripts.
- The first-meeting cinematic is implemented as a UI component with locally timed animation and dialogue progression. It does not establish a reusable cinematic timeline, camera director, actor blocking system, streaming/preload strategy, durable travel state, checkpoint/recovery, localization timing, or a full accessibility model.
- The inspected cinematic has a skip/continue interaction, but this alone does not prove reduced-motion alternatives, complete keyboard/controller access, screen-reader semantics, subtitle controls, or replay policy.
- Audio documentation mentions future accessibility controls and acoustic features; their end-to-end implementation is not established by these files.

### New Language-world requirements

1. Define semantic audio cue identities, per-world/location acoustic profiles, mix priorities, ducking, transitions, concurrency limits, spatial behaviour, quiet mode, and user controls.
2. Keep audio decision logic engine-neutral and playback behind a replaceable, engine-specific adapter.
3. Define semantic animation actions and layered performance requirements without binding gameplay to a specific DCC tool, renderer, or file naming convention.
4. Design a full Cinematic Experience System with timelines, beats, cameras, actors, dialogue, voice, subtitles, music, ambience, lighting, preloading, checkpoints, skip/replay, interruption, recovery, and playable handoff.
5. Make reduced-motion, caption/transcript, volume, quiet-mode, and other accessibility behaviour part of the original system contracts.
6. Validate audio and animation on target Android hardware, including thermal/load, memory, latency, interruption, and fallback behaviour.
7. Treat all third-party or recorded assets with explicit licensing, provenance, and human review.

## 38. Persistence, local fallback, account scope, and cross-system reliability

### Source systems inspected

Read-only reference review covered:
- `src/engines/world/persistentWorldStateEngine.ts`
- `src/engines/memory/memoryEngine.ts`
- `src/lib/localStore.ts`
- `src/lib/storage.ts`
- `src/engines/world/livingWorldObjectsStore.ts`
- `supabase/schema.sql`
- Relevant festival and event workflows.

### What the archive contains

The reference has a Supabase schema with profiles, learner preferences, worlds, locations, world state, characters, relationships, memories, learning records, conversations, stories, quests, collections, postcards, progression, currency, inventory, discoveries, journey events, plant state, and other user-scoped records. Row-level security is enabled on many tables, and inspected policies use the authenticated user ID for owner checks.

There are also local AsyncStorage stores and fallback paths. Some stores use per-user key prefixes, while the generic LocalStore uses shared keys and seed records containing the literal `local-explorer-user`. The memory engine writes to Supabase when configured but falls back to generic local memory methods in several failure paths. The persistent world-state engine stores a serialized snapshot inside the generic memories collection.

### Strengths worth carrying forward as requirements

- Personal data needs explicit learner/account ownership.
- A local-first or offline-capable experience can be valuable, but it needs a deliberate synchronization model.
- Different domain records should be represented explicitly rather than hidden inside a generic catch-all field.
- Server-side row-level security and owner checks are important layers of protection.
- Memory records benefit from provenance such as source event IDs.
- A learner's creations, learning evidence, world state, and preferences deserve separate lifecycle and retention policies.

### Gaps and cautions

- The generic LocalStore methods shown use shared keys and hardcoded local learner IDs, so they do not establish safe multi-account local isolation.
- MemoryEngine's local fallback calls generic methods without passing the requested user ID. In a local-only or network-failure path, this can lose account scoping.
- The persistent world-state implementation also hardcodes a local learner ID and stores structured state as a serialized memory fact, which makes schema validation, migration, indexing, and atomic updates difficult.
- Some local object stores are user-keyed, showing a better direction, but this pattern is not consistently applied across the archive.
- Sequential side effects such as reward claim, creation, memory, relationship, and event updates can partially succeed. The inspected examples do not establish an atomic outbox/transaction workflow across these domains.
- The schema enables row-level security, but the presence of RLS declarations alone does not prove every table has correct policies for every operation. Policy completeness, grants, foreign-key behaviour, and adversarial tests require a dedicated security review.
- A local fallback must not silently return another learner's data, seed data masquerading as personal data, or success after a failed write.

### New Language-world requirements

1. Every personal record and local cache must be explicitly scoped to a stable learner/account identity.
2. Define anonymous-to-account migration, sign-out, account switching, multi-device conflict resolution, deletion, export, and recovery.
3. Design domain-specific schemas and versioned migrations; avoid using a generic memory table as the authoritative storage for unrelated state.
4. Define local-first writes, sync queues, conflict policies, idempotency keys, retry/backoff, dead-letter handling, and reconciliation.
5. Use durable events/outbox patterns for cross-domain consequences. A reward, creation, relationship update, and memory record must not become an untraceable partial sequence.
6. Define privacy and retention by data category, with clear user controls and minimal collection.
7. Test isolation between two accounts on one device, offline-to-online transitions, interrupted writes, duplicate events, corrupt local records, migration, backup/restore, and deletion.
8. Review every RLS policy and local access path with security tests before real user data is stored.

## 39. Consolidated implications for the Master Blueprint

This review strengthens several existing blueprint chapters and introduces explicit supporting specifications:
- **World Objects and Spaces:** archetypes, instances, interiors, collision/navigation, interactions, object lifecycle, provenance, inventory, and crafting.
- **World Simulation and Events:** canonical clock, time layers, weather, seasons, festivals, bounded offline simulation, event durability, and domain ownership.
- **Audio and Performance:** semantic cues, acoustic identity, mix/density rules, audio adapter, licensing, and accessibility.
- **Animation and Cinematics:** semantic performance contracts, reusable cinematic timelines, camera/actor direction, preloading, checkpoints, interruption, and accessible alternatives.
- **Persistence and Trust:** learner-scoped data, local-first policy, sync/outbox, account migration, RLS review, privacy, deletion, and recovery.

**Audit status remains ongoing.** These findings are direct inspections of selected reference files. They do not prove that every referenced feature is complete, integrated, secure, or validated end-to-end. GoPAL-AI remains read-only; all new design and implementation belong in Language-world.

## 40. Personal creations, memory museum, and time capsules

### Source systems inspected

Read-only reference review covered:
- `src/engines/creation/creationStudio.ts`
- `src/features/journey/screens/MemoryMuseumScreen.tsx`
- `src/features/journey/components/TimeCapsuleModal.tsx`
- Related creation, postcard, time-capsule, and memory methods in `src/lib/localStore.ts`
- `src/engines/journey/journeyEngine.ts` and `src/features/journey/screens/JourneyBookScreen.tsx`

### What the archive contains

The Creation Studio defines templates for cultural postcards, study phrase cards, journey memory boards, and dialogue comic strips. Creating an artefact writes it to LocalStore and then separately records a journey event. The Memory Museum brings together postcards, creations, cultural artefacts, and memory records in a single exhibit-style experience. The Journey Book builds a timeline, milestones, first-day information, and a then-versus-now view from journey events and learning evidence.

The Time Capsule concept lets a learner write a private message for their future self and select a target date. The inspected UI also exposes a demo unlock action that can mark a capsule unlocked before its target date.

### Strengths worth carrying forward

- Learning and world experiences can leave meaningful artefacts rather than only numeric progress.
- A personal archive can make the learner's history visible through creations, discoveries, cultural objects, and milestones.
- Then-versus-now comparisons can communicate increased capability more meaningfully than a generic level.
- Learner-created work should be treated as owned content, not disposable UI state.
- A future-self message or time capsule can be a reflective creative experience when privacy and unlock rules are clear.

### Gaps and cautions

- Creation storage and journey-event recording are sequential. A creation can succeed while its timeline event fails, or vice versa in other orchestration designs.
- The inspected LocalStore creation APIs generate IDs from wall-clock milliseconds and use shared local keys; this is not a robust multi-account or collision-safe identity strategy.
- The Memory Museum reads several LocalStore collections directly and does not, in the inspected screen, establish edit/reopen/delete/export, media lifecycle, account switching, or cross-device synchronization.
- The Journey Book can build a meaningful view from events, but its local fallback uses generic storage without the requested user identity.
- The Time Capsule demo unlock control bypasses the target-date rule. A prototype affordance must not become the final trust model.
- Device clock changes and timezone changes can affect client-side date checks unless an authoritative policy is defined.
- The inspected time capsule content is private by intent, but the reviewed UI alone does not establish encryption, access control, backup, retention, deletion, or export guarantees.

### New Language-world requirements

1. Treat personal creations as versioned, learner-owned records with edit/reopen, delete, export, and media lifecycle support.
2. Make archive items traceable to source experiences and events without requiring the learner to understand internal IDs.
3. Define the Journey Book as an explainable reflection of durable events and capability evidence, not a source of truth of its own.
4. Define time-capsule unlock policy, trusted time source, offline behaviour, timezone changes, clock tampering, and any legitimate override explicitly.
5. Never include a demo unlock or developer bypass in production user flows.
6. Ensure private reflections remain private by default, with clear retention and deletion controls.
7. Coordinate artefact creation and journey-event publication through a durable operation or outbox so partial success can be recovered.

## 41. Discovery progression, transport infrastructure, and the difference between a route and a journey

### Source systems inspected

Read-only reference review covered:
- `src/engines/world/worldDiscoveryProgressionEngine.ts`
- `src/features/world/data/livingWorldTransport.ts`
- `src/features/world/components/WorldObjectDiscoveryOverlay.tsx`
- Existing journey and world-event records inspected in earlier sections.

### What the archive contains

The discovery progression engine models place nodes with world identity, place identity, name, city, real-world location, area, status, prerequisite, scenario links, landmark, and hidden-gem flags. It maps some legacy place IDs to canonical IDs and stores discovered/completed progress in local storage.

The transport data defines railway and airport infrastructure features such as tracks, platforms, runways, taxiways, and route points. The discovery overlay presents a newly discovered place with a short description and a choice to continue exploring or enter.

### Strengths worth carrying forward

- Discovery should be tied to places and world identity, not only a generic checklist.
- Hidden places, landmarks, prerequisites, and contextual experiences can support exploration.
- Transport infrastructure can be represented as part of the geography of a world.
- A discovery moment should create anticipation and invite the learner to choose what happens next.

### Gaps and cautions

- The discovery progression state is stored under one generic local key in the inspected engine, not explicitly scoped to a learner.
- The inspected transport data describes map geometry and route points. It does not establish a full travel lifecycle: itinerary, ticket/eligibility, terminal state, boarding, departure, journey progress, arrival, disembarkation, destination reveal, interruption recovery, or persistent handoff.
- A route drawn on a map is not itself a travel experience. The user's requested train journey requires authored scenes and durable journey state.
- The discovery overlay is a presentation component, not a complete investigation, narrative, or persistence system.
- Canonical ID mapping in one engine illustrates the need for a central registry and migration policy rather than scattered aliases.

### New Language-world requirements

1. Define a canonical world/place/region registry and stable IDs before authoring large amounts of content.
2. Separate geographical transport networks and infrastructure from travel itineraries and travel-session state.
3. Define the full travel state machine and interruption/relaunch recovery.
4. Design discovery as a family of experiences: first sight, clue, landmark, hidden location, cultural discovery, and story revelation.
5. Scope all learner-specific discovery progress correctly and preserve world-authored discovery definitions separately from learner state.

## 42. Additional archive review status

This review extends the selected-file evidence to personal creation, reflective archive, time capsules, discovery progression, and transport infrastructure. It reinforces that the new product needs durable personal ownership, trusted time rules, canonical place identity, and a true travel experience rather than only transport geometry.

The archive review remains selective and ongoing. No claim is made that every related source file or runtime path has been inspected. GoPAL-AI remains read-only.

## 43. Cassidy canonical identity, visual design, and character production references

### Source documents inspected

Read-only reference review covered:
- `docs/cassidy/canonical-reference.md`
- `docs/cassidy-master-character-bible.md`
- `docs/cassidy-character-reference.md`
- `docs/cassidy-visual-design.md`
- `src/characters/cassidyCharacterDesign.ts`
- `src/characters/cassidyVisualDesign.ts`
- `contracts/cassidy-identity.json`
- Selected production/renderer contract documents for understanding reference boundaries only.

### What the archive records

The reference archive identifies an approved Cassidy concept sheet and establishes a written source hierarchy with the approved concept first, followed by the master art bible and other supporting references. It also notes that the canonical image binary was not stored in that repository at the time of the note. The user has separately confirmed that Cassidy's established design and character details exist and that they personally have her design.

Repeated visual identity elements include:
- Human female companion character with a warm, distinctive stylized-human face.
- Large expressive near-black eyes with warm brown undertone.
- Dark chocolate-brown hair with warm highlights; the detailed reference specifies a side braid.
- Emerald Valley adventurer outfit with a green vest/waistcoat, cream blouse, brown leather gear, fitted trousers, boots, and a signature necklace.
- Gold leaf-star-compass charm with teal/emerald centre and several contextual glow states.
- Full-body design and consistent identity across front, three-quarter, side, and rear views.
- A semantic expression/action vocabulary including idle, walk, run, turn, sit, talk, gesture, point, celebrate, think, react, greet, listen, explain, discover, encourage, and reflect.

The reference material describes personality qualities such as warmth, curiosity, intelligence, empathy, playfulness, bravery, thoughtfulness, and adventurousness. It also describes a character life with independent activities, memories, stories, dreams, and adventures.

### Conflicts and limitations identified

- Written outfit guidance for Japanese and French worlds differs between documents. The references include both pink/floral and restrained indigo/vermillion/cream directions for Japan, and both cream/beige/beret and restrained navy/burgundy/cream directions for France. The actual canonical artwork must resolve visual identity; world variants also need cultural review.
- One character reference gives an age range of 18–22 (timeless), while the master art bible does not establish a definitive age. This must not be silently converted into final Language-world canon.
- The archive contains old production pipeline instructions, technical budgets, renderer contracts, scripts, and implementation details. These are reference evidence only and are explicitly excluded from reuse in Language-world.
- The text documents alone do not replace the user's actual canonical artwork. The inspected canonical-reference note says the binary was not stored in the old repository at the time of that note.
- Old statements implying the learner is Cassidy's “most important person” or that she is “always by your side” must be reconsidered against Language-world's character autonomy and non-manipulative relationship principles.

### New Language-world requirements

1. Preserve Cassidy's existing canonical human identity; do not redesign or replace her with an invented character.
2. Separate immutable identity anchors from permitted outfit, lighting, and world-specific adaptations.
3. Resolve visual conflicts against the user's canonical artwork, not by selecting an arbitrary text variant.
4. Define Cassidy as a character with agency, boundaries, motives, commitments, and a life beyond the learner.
5. Build relationship continuity from real shared experiences and retained memories, without guilt, absence penalties, exclusivity, or fabricated memory.
6. Keep character intelligence, memory, dialogue, physical performance, cinematics, and rendering as distinct contracts.
7. Do not reuse any legacy Cassidy model, rig, skeleton, animation, renderer, factory, authoring script, exporter, validator, manifest, or runtime.
8. Record unresolved age, voice, backstory, outfit, and autonomy decisions explicitly before production.

### Language-world document created

A new independent working draft, `docs/CASSIDY_CHARACTER_BIBLE.md`, records the recovered canon, Language-world principles, source conflicts, artist handoff requirements, and approval questions. It is a new product specification, not a copy of the old implementation or pipeline.

**Audit status remains ongoing.** This review covers selected canonical and visual references, not every Cassidy source file or every runtime behaviour.

## 44. Emerald Valley world specification and language-world geography references

### Source documents inspected

Read-only review covered:
- `docs/EMERALD_VALLEY_WORLD_MASTER_SPEC.md`
- `src/features/world/data/livingLanguageWorlds.ts`
- `src/features/world/data/livingLanguageWorldLocations.ts`
- `src/features/world/data/livingLanguageWorldPhysical.ts`
- `src/features/world/data/livingWorldCharacters.ts`
- `src/engines/world/npcCharacterRegistry.ts`
- `src/features/world/data/livingWorldActivities.ts`
- `src/features/world/data/livingWorldBehavior.ts`
- `src/features/world/data/livingWorldTerrain.ts`
- `src/features/world/data/livingWorldNavigation.ts`

### What the archive describes

The Emerald Valley master specification is unusually detailed as a spatial and sensory reference. It describes a mountain valley with west/south arrival approaches, a central settlement and stream, eastern railway/tunnel continuation, and northern mountain/sanctuary/garden areas. It gives distinct identity to the café, market, library, station, sanctuary, bamboo garden, campfire clearing, stream, lanterns, paths, and environmental transitions. It also includes time/weather, sound design, discovery principles, camera language, visual composition, and return-visit acceptance ideas.

The location catalogue contains five Japanese real-place examples paired with fictional places, and four French real-place examples paired with fictional places. The top-level registry in the inspected file lists Emerald Valley, Japanese World, and French World. It does not list a Spanish world.

The inspected physical layer uses broad tag-derived themes and similar default road, sidewalk, crossing, lighting, and transit patterns for many language-world locations. The resident registry contains role templates and location-specific spawn examples; activity and schedule rules are primarily role-based and generic.

### Strengths worth carrying forward

- Emerald Valley has a strong emotional identity, readable geography, a memorable set of connected landmarks, and detailed sensory direction.
- The stream, railway, mountain tunnel, sanctuary, café, market, library, and garden create a coherent spatial vocabulary rather than isolated destinations.
- Weather, time, lighting, audio, and spatial transitions are treated as parts of place identity.
- Acceptance tests consider the first 30 seconds, a five-minute visit, and a return visit.
- Real and fictional locations can coexist when the distinction is clear.
- World bibles can connect geography, resident roles, activities, culture, and sensory identity.

### Gaps and cautions

- The Emerald Valley master specification is still a GoPAL-AI document and may contain legacy implementation assumptions, coordinates, asset references, and performance constraints. Its creative direction is research material; its coordinates, models, scene, renderer, and pipeline are not to be copied.
- The world registry inspected contains only Emerald Valley, Japanese World, and French World. This does not satisfy the user's established Spanish-world travel example or establish the full intended universe.
- The physical presentation layer applies shared generic infrastructure and tag-based themes to many locations. It does not demonstrate truly distinct geography, architecture, ecology, settlement patterns, or cultural life for each language world.
- The location catalogue is a small seed list, not a complete geography or researched cultural representation.
- Role templates and spawn points do not constitute a full authored society. Resident schedules are generic and do not establish detailed biographies, relationships, commitments, or community histories.
- The reviewed terrain/navigation helpers are implementation-level geometry abstractions, not a world-authoring and validation standard.
- Some old specification content includes technical renderer and asset-performance assumptions that must be re-evaluated against the new engine and target devices.

### New Language-world requirements

1. Author Emerald Valley as a complete home-world bible, retaining its emotional and spatial strengths while independently deciding its final geography, history, residents, ecology, and experiences.
2. Define each language world through a complete world bible, not a palette/theme parameter.
3. Add Spanish as a first-class world if it remains the first destination in the user's travel vision; its geography and identity must be authored rather than inferred.
4. Establish a canonical world/region/place registry with stable IDs, real/fictional provenance, content versions, and learner-state separation.
5. Require cultural and language review for all real-world references and world-specific variants.
6. Define world-specific architecture, infrastructure, transport, ecology, sound, weather, resident societies, and everyday activities.
7. Use reusable technical systems without making the worlds themselves generic.
8. Create first-visit, short-visit, and return-visit acceptance criteria for every world.

### Language-world document created

A new independent working draft, `docs/WORLD_UNIVERSE_BIBLE.md`, records the universe structure, recovered Emerald Valley foundation, Japanese/French location seeds, world identity standard, canonical registry requirements, travel principles, and open decisions.

**Audit status remains ongoing.** This review inspects selected world documents and source files. It does not establish complete world implementation, cultural accuracy, or end-to-end simulation.



## 45. Experience catalogue, games, stories, and activity quality

### GoPAL-AI references inspected

- `docs/world-mini-games-50-plus-catalog.md` documents 60 mini-game concepts across discovery, puzzles, arcade/reflex, social/communication, listening/audio, story/adventure, and creative/construction. Its own status section says the catalogue is documented while playable implementations, variety selection, world-reactive outcomes, and cross-language reuse remain future work.
- `src/engines/world/worldMiniGameCatalog.ts` and `worldMiniGameEngine.ts` contain typed definitions for the game family and a session-oriented engine foundation. This does not establish that every listed game has a complete playable implementation.
- `worldMiniGameSelectionEngine.ts` uses recent-play history and selection scoring. The inspected history key is not explicitly learner-scoped, so it is not an acceptable persistence model for the new product.
- `residentStoryEngine.ts` contains a small fixed set of resident story threads and stage transitions. This is a seed for multi-visit story thinking, not evidence of a deep narrative system.
- `worldStoryChoiceEngine.ts` is a small in-memory choice-state helper. Durable branching, consequence management, migration, recovery, and content validation are not established by this helper.
- `questEngine.ts` provides quest seed data and completion/reward side effects; inspected seed data includes pre-completed examples. A clean new learner experience must never inherit pre-completed state.
- `worldEventDirectorEngine.ts` coordinates ambient events and opportunities but explicitly leaves quests, festivals, inventory, and rewards to other authorities.
- `worldActivityPrimitives.ts` and `worldActivityMechanics.ts` provide small reusable geometry/selection/sequence helpers, not a universal interaction or game runtime.

### Recovered strengths

- Broad activity imagination beyond resident dialogue and conventional lessons.
- Reusable game-mechanic concepts and a separation between mechanics and location/content.
- Recognition that variety, recent history, skill needs, session length, and location context can influence discovery.
- Story threads and choice-state concepts that can support continuity.
- Ambient events and opportunities as separate from quest/reward ownership.

### Limitations and risks

- The 60-item catalogue is a concept library, not proof of 60 complete games.
- Some game descriptions are timed/reflex-oriented; overuse would make the universe feel like a quiz arcade.
- The old selection history key is not explicitly learner-scoped in the inspected code.
- Story thread coverage is small and fixed; the inspected choice helper is in-memory.
- Quest seeds include completed examples and reward-centric fields; this must not define the new product's motivation model.
- The inspected files do not prove end-to-end save/restart recovery, account isolation, localization quality, accessibility, or device performance.

### New Language-world requirements

1. Provide a universe-wide taxonomy covering exploration, mysteries, stories, games, language-in-the-world, culture, creative work, optional social experiences, world-life, travel, events, and personal archive.
2. Preserve the 60 game ideas only as research seeds until each is independently designed, tested, and approved.
3. Make non-learning experiences first-class; language learning may be core, embedded, incidental, contextual, or absent.
4. Define an experience authoring contract with identity, player fantasy, rules, outcomes, learning evidence, world consequences, assets, persistence, accessibility, safety, and QA.
5. Keep Cassidy's participation optional and consistent with her independent agency and boundaries.
6. Make stories, clues, learner evidence, world changes, and user-created artefacts recoverable across interruptions and restarts.
7. Scope all personal history and learner evidence to the correct learner/account; never inherit unscoped legacy storage assumptions.
8. Require quality gates for concept value, playability, learning integrity, narrative/world integrity, production readiness, and live quality.
9. Avoid manipulative streaks, artificial urgency, punitive lives, expiring story access, and reward-first design.
10. Build a small balanced first-release portfolio rather than attempting to ship all catalogue concepts.

### Language-world document created

Created `docs/EXPERIENCE_CATALOGUE.md`, a working specification containing the taxonomy, all 60 research seeds, authoring contract, learning integration model, variety principles, persistence boundaries, accessibility/safety standards, quality gates, and candidate portfolio. It is linked from Master Blueprint Section 36.

**Audit status remains ongoing.** This section records selected source evidence and design implications; it does not claim complete verification of every old experience or runtime behaviour.


## 46. Learning design, capability evidence, and evaluation limits

### GoPAL-AI references inspected

- `docs/world-learning-variety-blueprint.md` and `world-learning-variety-implementation.md` describe contextual learning in real locations, fictional learning spaces, and reusable mechanics rather than one fixed lesson format.
- `src/engines/learning/contextualLanguageLearningEngine.ts` builds place-based prompts across vocabulary, listening, speaking, reading, grammar, and writing.
- `adaptiveConversationEngine.ts` selects conversation support using a single numeric mastery value. This is a useful adaptation concept but too coarse to represent separate language skills and evidence.
- `languageCapabilityEngine.ts` records scenario/skill attempts and successes plus word/phrase counters. The inspected implementation stores data under one global AsyncStorage key rather than explicit learner scope; this is a serious account-isolation requirement for the new product.
- `learningEvaluationEngine.ts` uses expected-concept and sample-response matching heuristics. This can support narrow constrained text checks but does not establish robust semantic understanding, naturalness, spoken ability, or pronunciation.
- `learningNeedEngine.ts` ranks scenarios from scenario and skill capability states.
- `worldLearningScenarioEngine.ts` contains authored place-specific scenarios with target language, vocabulary, response options, cultural notes, follow-ups, and possible world changes.
- `worldLearningResponseEngine.ts` uses exact/approximate string matching; `wordBankAnswerEngine.ts` composes responses from selected word indexes.
- `worldLearningFlowEngine.ts` and `worldLearningOutcomeEngine.ts` connect capability, integration/memory, relationship, Cassidy, and world consequences. The inspected flow performs sequential side effects and uses local completion/in-flight guards; this does not prove transactional recovery across interrupted operations.

### Recovered strengths

- Language learning is connected to believable places and meaningful interactions.
- The learning model recognises multiple skills beyond vocabulary recall.
- Scenarios can include context, target language, vocabulary, cultural notes, follow-ups, and world consequences.
- Adaptive support and prioritisation of learning needs are represented.
- Learning outcomes can connect to narrative and world continuity.

### Limitations and risks

- A single mastery scalar is too coarse for multidimensional language ability.
- Attempt/success counts and fixed thresholds do not prove transfer or long-term retention.
- A global capability key risks cross-learner leakage on shared devices.
- String and sample-response matching are not robust semantic assessment.
- Microphone capture, shadowing, speech transcription, semantic speech evaluation, and pronunciation analysis are distinct capabilities; the inspected code does not establish the latter capabilities.
- Sequential multi-service side effects can leave partial outcomes if interrupted.
- The inspected files do not establish a complete spaced-repetition system, robust speech evaluation, dialect coverage, account isolation, or validated learning gains.

### New Language-world requirements

1. Define separate capability dimensions and retain raw evidence separately from derived progress summaries.
2. Track exposure, recognition, retrieval, guided production, independent production, transfer, retention, confidence, and support dependence without collapsing them into one score.
3. Adapt support using multidimensional evidence, recency, context variety, hints, and learner-controlled preferences.
4. Define valid evaluation methods and explicit limitations for multiple choice, text matching, typed responses, audio playback, recording, ASR transcripts, and pronunciation analysis.
5. Never claim speech/pronunciation assessment without an appropriate validated capability and evidence.
6. Support contextual listening, speaking, reading, writing, vocabulary, grammar, pragmatics, and cultural interpretation.
7. Require qualified language/cultural review and support valid regional, register, and dialect variation.
8. Scope every learner record to an explicit stable learner/account identity; prevent cross-account data exposure.
9. Define consent, minimised audio retention, export, correction, deletion, offline/sync, idempotency, and recovery requirements.
10. Keep practice optional and motivating without streak pressure, punitive lives, or fabricated mastery.

### Language-world document created

Created `docs/LEARNING_DESIGN.md`, a working specification covering learning philosophy, capability/evidence, adaptive support, evaluation limits, listening and speech honesty, reading/writing, vocabulary/grammar, cultural pragmatics, learner control, persistence/privacy, accessibility, and open decisions. It is linked from Master Blueprint Section 37.

**Audit status remains ongoing.** This section records selected source evidence and design implications; it does not claim full verification of all legacy learning behaviour or validated learning outcomes.


## 47. Living-world time, weather, routines, and simulation

### GoPAL-AI references inspected

- `src/engines/world/environmentEngine.ts` resolves season and time of day from a supplied/current Date and selects weather from deterministic day/hour buckets.
- `src/engines/world/livingWorldClock.ts` uses device local time with fixed day-phase boundaries.
- `src/engines/world/livingWorldSimulation.ts` stores a per-user snapshot in AsyncStorage, but recomputes phase/weather/season from current wall-clock time; elapsed minutes are mainly carried into a location-shift event.
- `src/engines/world/worldSimulationSnapshot.ts` supplies a lightweight snapshot with default clear weather and simple activity/light values.
- `src/engines/world/residentRoutineEngine.ts` uses a small hour-based activity switch and short runtime transitions.
- `src/engines/world/contextualWorldEventEngine.ts` selects lightweight ambient events from weather, routine, learner activity, and a seeded rare-event condition.
- `src/engines/world/worldEventDirectorEngine.ts` coordinates ambient events and opportunities while leaving festivals, quests, inventory, and rewards to other owners.
- `src/engines/world/npcCharacterRuntimeEngine.ts` maintains an in-memory NPC expression/animation/outfit/presence snapshot.
- `src/features/world/data/livingWorldSimulation.ts` includes local actor/vehicle simulation, seeded spawn positions, movement/navigation, and schedule/behaviour hooks.
- `src/engines/world/livingWorldRuntime.ts` bridges persisted user world state with simulation and revisit continuity.

### Recovered strengths

- Time, weather, season, ambience, and world events are recognized as part of the world experience.
- Some weather selection is deterministic rather than random on each render.
- Residents have routine/activity concepts.
- Ambient events are separated from some higher-level product systems.
- The larger world runtime includes actor movement, routes, navigation, and spawn points.
- Return visits and continuity are considered product concerns.

### Limitations and cautions

- Several clocks and snapshots use device local wall time directly.
- Weather and season logic are lightweight deterministic buckets, not an authored climate model.
- The inspected world snapshot defaults to clear weather and simple ambient values.
- Resident routine logic is highly simplified and does not establish a durable society or long-term commitments.
- NPC presentation state is in-memory; it is not a full persistent character-life model.
- The inspected sources do not establish a complete creature/ecology simulation or species/habitat system.
- The inspected sources do not establish a robust plant lifecycle, care, and habitat model.
- Offline elapsed time, device clock changes, daylight-saving/time-zone behaviour, event recovery, and cross-device determinism are not fully proven.

### New Language-world requirements

1. Define one canonical world clock and an explicit time-zone/calendar policy; no subsystem may independently infer time from device wall clock.
2. Define day/night, seasonal, and weather profiles separately for each authored world.
3. Use deterministic, bounded weather and event transitions with accessible presentation fallbacks.
4. Author resident routines as flexible plans with commitments, exceptions, weather/season adjustments, and limited attention.
5. Define creatures as ecological participants with habitats, needs, rhythms, signs, population bounds, and world-specific behaviour.
6. Define plant/garden lifecycles and reversible care states without punitive absence mechanics.
7. Give every durable event a stable identity, causal source, scope, version, and idempotent recovery policy.
8. Define bounded offline catch-up and clock-tampering/daylight-saving/time-zone behaviour.
9. Separate persistent world truth from transient presentation and use simulation fidelity tiers for Android performance.
10. Ensure important events and story content are recoverable after absence rather than expiring through FOMO.

### Language-world document created

Created `docs/WORLD_SIMULATION_SPEC.md`, a working specification covering simulation ownership, canonical clock options, offline progression, day/night, climate/weather, residents, creatures/ecology, plants/gardens, world events, environmental storytelling, performance tiers, persistence, authoring validation, and open decisions. It is linked from Master Blueprint Section 38.

**Audit status remains ongoing.** This section records selected source evidence and design implications; it does not claim all old simulation systems were exhaustively audited or that the reference simulation works end-to-end.


## 48. World objects, buildings, interiors, and interactions

### GoPAL-AI references inspected

- `src/features/world/data/livingWorldObjects.ts` defines a common object instance with identity/category/type, transform, visual, collision, interaction, behaviour, state, tags, and metadata.
- `livingWorldObjectCatalog.ts` and `livingWorldObjectRegistry.ts` enumerate broad archetypes for buildings, interiors, terrain, decoration, infrastructure, transport, characters, gameplay, fantasy, and sci-fi.
- `livingWorldObjectFactory.ts` adapts multiple earlier catalogs into a shared object stream.
- `livingWorldInteraction.ts` derives available actions and nearest interaction targets from object properties and proximity.
- `livingWorldEntrancesObjects.ts` adapts entrance definitions into object instances.
- `src/engines/world/livingWorldObjectsStore.ts` stores learner-keyed plant/companion/artifact-like objects with growth and memory; it also contains prefilled sample memories and a special legacy migration path.
- `src/engines/world/worldInventoryEngine.ts` provides in-memory add/remove/combine helpers.
- `src/engines/world/worldStateEngine.ts` persists flags/history under a global AsyncStorage key in the inspected implementation, not explicitly learner-scoped.
- `livingWorldLocationSchema.ts` and `livingWorldLocationFactory.ts` define location object collections, environment/rule flags, and template-based construction.

### Recovered strengths

- A shared object-instance concept can connect buildings, props, infrastructure, transport, characters, and gameplay.
- Archetypes cover a broad range of physical and fictional world content.
- Interactions can be derived from semantic object properties and proximity.
- Entrances can be represented as world objects.
- Personal living objects and inventory concepts provide useful product seeds.

### Limitations and cautions

- The object factory adapts multiple catalogs; a single authoritative content-authoring source is not established by the inspected code.
- Generic extensible object state does not itself establish domain-specific ownership and lifecycle contracts.
- The inspected world state store uses a global key and risks cross-learner leakage.
- The personal object store is learner-keyed but includes prefilled demo memory and a special migration path that must not be copied.
- Inventory helpers are in-memory; durable inventory, conflict handling, and cross-device recovery are not established.
- The inspected files do not establish a complete building/interior lifecycle, robust multi-floor navigation, or designer-grade asset replacement workflow.

### New Language-world requirements

1. Define a stable spatial hierarchy and semantic IDs independent of display names, filenames, renderer nodes, and storage keys.
2. Author each place with geography, routes, entrances, buildings, interiors, environment, actors, interactions, accessibility, and performance metadata.
3. Treat buildings as spatial containers with connected interiors, entry/exit anchors, navigation, schedules, and persistent context.
4. Separate object identity, authored definition, instance placement, presentation, collision, interaction, durable state, ownership, and provenance.
5. Define object lifecycle transitions and make durable changes idempotent.
6. Use contextual interactions with clear prerequisites, feedback, accessibility, cancellation, and recovery.
7. Distinguish inventory, collections, story evidence, user creations, consumables, and world-placed objects; do not add an economy without a product reason.
8. Scope personal spaces and all learner-specific object/world state to the correct account.
9. Use semantic asset bindings so placeholder-to-final replacement does not break gameplay, navigation, narrative, or saved data.
10. Validate spatial reachability, entrances, object state, asset fallback, offline recovery, and Android performance.

### Language-world document created

Created `docs/WORLD_OBJECTS_AND_SPACES.md`, a working specification covering spatial hierarchy, place authoring, buildings/interiors, object lifecycle, interactions, navigation, inventory, personal spaces, semantic events, replaceable art, accessibility, and open decisions. It is linked from Master Blueprint Section 39.

**Audit status remains ongoing.** This section records selected source evidence and design implications; it does not claim every legacy place/object or interior was fully audited.


## 49. Transport, destination arrival, and travel lifecycle

### GoPAL-AI references inspected

- `src/features/world/data/livingWorldTransport.ts` defines railway/airport networks with track, platform, runway, taxiway, and terminal-apron geometry plus optional route points.
- `src/features/world/data/livingWorldVehicles.ts` defines train, bus, car, bicycle, boat, and airplane actors with waypoint routes, speed, and local loop behaviour.
- `src/engines/world/destinationArrivalSceneEngine.ts` creates destination arrival scenes with establishing, wide-environment, weather, life, and resident-reveal shots.
- `src/engines/world/destinationArrivalTimelineEngine.ts` creates a fixed-duration sequence and encounter handoff.
- `src/engines/world/destinationExperienceEngine.ts` and `worldDestinationExperienceEngine.ts` supply destination atmosphere, visible places, discoveries, and learning moments.

### Recovered strengths

- Multiple transport modes and infrastructure types are represented.
- Vehicles can follow authored waypoints and connect to local transport networks.
- Arrival is recognized as a cinematic moment with environmental continuity and a resident reveal.
- Destination identity and local discovery can inform the arrival experience.

### Limitations and cautions

- Inspected vehicle routes are mostly looping local movement, not persistent inter-world journeys.
- Transport networks describe visual geometry and route points, not a complete boarding/departure/arrival domain.
- The inspected arrival timeline is a fixed short sequence, not a complete cinematic authoring or travel recovery system.
- The inspected sources do not establish a durable journey state machine, transfers, interruption-safe handoff, or cross-world route graph.
- A moving vehicle actor is not equivalent to a learner-controlled travel experience.
- The first Spanish-world train journey is a product requirement to author, not a completed legacy feature.

### New Language-world requirements

1. Define canonical route graphs between worlds, regions, places, and spaces.
2. Choose transport based on geography, infrastructure, distance, and authored world canon.
3. Persist journey state independently of cinematic playback, including boarding, departure, transfers, arrival, and handoff.
4. Make boarding/departure/arrival transitions idempotent and recoverable after app termination.
5. Author transport-specific cinematic beats and destination reveals rather than generic vehicle animations.
6. Keep in-transit activities optional; core arrival never depends on completing a language task.
7. Define first-visit and return-visit journey variants and appropriate replay/skip behaviour.
8. Coordinate travel time and timezone transitions with the canonical world clock.
9. Provide reduced-motion, captions, audio controls, interruption handling, and accessible alternatives.
10. Author the Emerald Valley-to-Spanish-world train journey as a product-defining reference route.

### Language-world document created

Created `docs/TRAVEL_EXPERIENCE_SPEC.md`, a working specification covering transport modes, route graphs, durable journey states, cinematic staging, optional travel activities, Cassidy boundaries, arrival handoff, accessibility, reliability, and open decisions. It is linked from Master Blueprint Section 40.

**Audit status remains ongoing.** This section records selected transport and arrival source evidence; it does not claim all legacy travel code was exhaustively audited.


## 50. Audio, voice, soundscapes, and cinematic performance

### GoPAL-AI references inspected

- `src/engines/audio/audioEngine.ts` contains a small ambient-track catalogue and mute preference; the inspected sound-effect method logs playback rather than producing an audible effect.
- `src/engines/world/worldAudioContract.ts` defines music, ambience, location, activity, interaction, transport, voice, and event categories; location profiles, priority, mix values, and distance attenuation.
- `src/engines/world/worldAudioEngine.ts` resolves gain, priority, distance attenuation, cooldown, and concurrency decisions in a lightweight in-memory resolver.
- `src/engines/world/worldAudioProfiles.ts` provides example profiles for Emerald Valley, station, café, library, forest, airport, study room, and night street.
- `src/engines/world/worldAudioRuntime.ts` is a thin player adapter that imports `expo-audio`; it is excluded from Language-world because Expo is explicitly rejected.
- `src/engines/world/worldAnimationContract.ts` and `worldAssetAnimationRouter.ts` show a semantic action vocabulary and clip alias resolution; useful as conceptual separation, not as reusable code.
- `src/features/cassidy/components/CassidyFirstMeetingCinematic.tsx` combines animated UI, character rendering, dialogue, and completion side effects in one component.

### Recovered strengths

- Audio is treated as more than music: ambience, location, activity, interaction, transport, voice, and events are represented.
- Location-specific profiles, priorities, distance attenuation, and cooldowns are recognised.
- A semantic animation vocabulary illustrates the separation between action intent and art clip names.
- The first-meeting and destination-arrival concepts support the intended emotional and environmental role of audio and performance.

### Limitations and cautions

- The basic audio engine has a small fixed ambient catalogue; the inspected SFX method is a logging placeholder, not audible playback.
- The inspected resolver tracks active cues in memory and uses runtime wall-clock time for cooldowns; it is not a durable content or simulation authority.
- The inspected playback adapter depends on Expo Audio and cannot be reused.
- Audio cue/profile coverage, final asset provenance, and voice production are not proven complete.
- The reviewed first-meeting component combines presentation, UI, and completion side effects; new cinematic playback must be separate from durable onboarding state.
- The inspected audio sources do not establish microphone consent, speech recognition, validated pronunciation assessment, retention, or voice-data deletion policy.

### New Language-world requirements

1. Author a sound identity bible for every world and major location; avoid generic ambience packs with superficial cultural overlays.
2. Use stable semantic cue IDs and versioned audio manifests, not filenames or middleware IDs in gameplay.
3. Separate Audio Director, Mix Director, and platform playback adapter.
4. Define priorities, ducking, concurrency, fades, cooldowns, spatialization, and quiet-zone rules.
5. Commission or license original music and record source, performer, rights, and permitted use.
6. Define consistent character voice identities, pronunciation guides, localized performance, and performer rights.
7. Distinguish playback, shadowing, capture, speech recognition, pronunciation assessment, and conversation; never overclaim what is measured.
8. Require explicit microphone consent, visible recording state, stoppability, purpose limitation, retention/deletion policy, and vendor transparency.
9. Provide captions/transcripts, speaker labels, sound alternatives, adjustable category levels, quiet mode, and no-music support.
10. Handle audio focus, calls, headphone changes, app lifecycle, offline assets, missing files, and native resource disposal.
11. Keep audio and animation presentation signals separate from durable world/story/travel state.
12. Validate sound quality, accessibility, localization, and performance on target Android devices.

### Language-world document and consolidation updates

Created `docs/AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md`, a working specification for world sound bibles, cue contracts, mix architecture, adaptive soundscapes, music, voice, language-learning audio integrity, accessibility, interruptions, delivery, and open decisions. It is linked from Master Blueprint Section 41.

The existing `CINEMATIC_EXPERIENCE_BLUEPRINT.md` was strengthened with sequence lifecycle, beat/track ownership, interruption/version migration, and quality gates. Existing `ASSET_HANDOFF_STANDARD.md` and `ASSET_AND_CINEMATIC_PIPELINE.md` were strengthened with authoritative document boundaries, validation, versioning, and the explicit no-legacy-pipeline rule. These documents remain working specifications, not approved final production contracts.

**Audit status remains ongoing.** This section records selected-source observations and does not claim an exhaustive audit of all audio, animation, or cinematic content.


## 51. Stories, quests, investigations, and narrative continuity

### GoPAL-AI references inspected

- `src/engines/quest/questEngine.ts` defines quest categories and seeded quests; inspected seed data includes pre-completed sample progress. Completion updates quest state, claims an economy reward, and writes a journey event in sequential side effects.
- `src/engines/world/residentStoryEngine.ts` defines three fixed resident story-thread templates with seeded/waiting/ready/resolved stages; waiting-to-ready uses a five-minute elapsed-time threshold.
- `src/engines/world/residentStoryOpportunityEngine.ts` derives story opportunity tone from a broad resident relationship tier and adds fixed text.
- `src/engines/world/worldInvestigationEngine.ts` implements clue prerequisites, collection, reveal, and completion as pure state transitions.
- `src/engines/world/worldStoryChoiceEngine.ts` provides a small story-node/choice model with history and numeric flags.
- `src/engines/world/worldEventDirectorEngine.ts` combines contextual ambient events and opportunities while leaving quests, festivals, inventory, and rewards to other owners.
- `src/features/world/data/livingWorldQuestEngine.ts` holds quest state in an in-memory map, updates objectives from events, and timestamps start/completion.
- `src/features/learning/components/WorldInvestigationBoard.tsx` holds investigation progress in component state; remounting loses progress unless a caller persists it.
- `src/features/learning/components/WorldStoryChoiceBoard.tsx` holds story node/history/flags in component state.
- `src/features/world/components/WorldStoryTraceLayer.tsx` polls resident threads and renders fixed-position traces for a small set of known thread IDs.

### Recovered strengths

- Resident story threads and contextual opportunities are represented.
- Clues can have prerequisites and reveal other clues.
- Story choices can preserve a basic choice history.
- One event director separates ambient opportunity selection from quest/reward ownership.
- Narrative traces can be represented spatially in the world.

### Limitations and cautions

- The inspected resident story engine has only a few fixed templates and a fixed five-minute waiting threshold, not a rich authored narrative scheduler.
- Story-choice and investigation components hold state locally; durable re-entry is not established by those components.
- Generic quest seed data includes pre-completed sample progress.
- Quest completion performs sequential persistence, reward, and journey-event side effects; the inspected code does not prove a transactional outbox or crash-safe cross-domain completion.
- The in-memory world quest engine does not by itself establish durable progress or account scoping.
- Relationship-tier-derived story text does not replace authored character knowledge, motives, or nuanced memory.
- These selected files do not prove a complete world/universe mystery, long-running story arc, fair clue graph, or coherent narrative canon system.

### New Language-world requirements

1. Author multiple narrative scales, from short moments and local stories to world and universe arcs.
2. Separate world canon, learner knowledge, learner choices, character knowledge, and cinematic/UI presentation.
3. Give every fact and clue provenance, reliability, scope, and version.
4. Design fair mysteries with alternative discovery routes, evidence connections, hint levels, and recoverable critical clues.
5. Make choices meaningful and traceable without reducing characters to hidden numeric relationship meters.
6. Give residents their own motives, commitments, knowledge, and stories that do not all depend on the learner.
7. Preserve Cassidy's agency and boundaries; she is not a universal quest giver or narrator.
8. Use quests only where objectives clarify meaningful intent; do not turn every activity into a checklist or daily chore.
9. Persist story progress, clues, choices, and consequences outside UI component state.
10. Make journal/recap support gentle re-entry without guilt or expiring essential content.
11. Use stable idempotent narrative events and domain-owned consequences.
12. Integrate language practice without making narrative outcomes depend on unvalidated pronunciation or one exact phrase.
13. Review canon, culture, accessibility, localization, audience suitability, and content-version migration.

### Language-world document created

Created `docs/NARRATIVE_AND_STORY_CONTINUITY_SPEC.md`, a working specification for narrative scales, canon/knowledge, story authoring, fair mysteries, choices, resident autonomy, Cassidy boundaries, quests, journals, durable events, learning integration, and cultural/quality review. It is linked from Master Blueprint Section 42.

**Audit status remains ongoing.** This section records selected-source observations and does not claim an exhaustive review of all story content or narrative assets.


## 52. Persistence, privacy, identity, and synchronization audit

### Selected GoPAL-AI sources inspected

- `src/lib/localStore.ts` — local keys, seeded defaults, world/character/memory/journey/creation state, local mutations, reset behavior.
- `src/lib/storage.ts` — prefixed cache helpers.
- `src/lib/supabaseClient.ts` — Supabase configuration and auth persistence.
- `src/services/auth.ts` — configured and local fallback identity behavior.
- `src/engines/memory/memoryEngine.ts` — remote memory reads/writes and local fallback paths.
- `supabase/schema.sql` — personal-data tables, row-level security enablement, and selected owner policies.

### Recovered strengths

- The project attempted both local persistence and remote persistence.
- Its schema recognizes many useful personal-state domains: profile/preferences, world state, relationships, memories, learning sessions, stories, creations, progression, discoveries, inventory, and journey events.
- Some tables use explicit owner checks through row-level security.
- Memory categories and source-event references point toward a useful provenance model.
- A separate cache prefix distinguishes some cached values from the main local store.

### Concrete limitations observed

- LocalStore keys share a global prefix and do not include a learner identity.
- Several local defaults and writes use the hard-coded `local-explorer-user` identity.
- Unconfigured auth returns a shared local demo identity rather than provisioning a distinct anonymous learner.
- MemoryEngine's local fallback omits the supplied userId when calling LocalStore methods, so a remote failure can write/read shared local memory state.
- A remote memory query returning no rows may fall back to local records, confusing an empty remote account with local fallback state.
- Multiple LocalStore getters return pre-populated demo progress, memories, creations, bookmarks, artifacts, and revisit counts.
- LocalStore writes catch and log errors without exposing a durable pending/failed status to the caller.
- Read-then-write local mutations lack a transaction or recovery journal in the inspected implementation.
- Local memory and journey-event IDs use Date.now(), which is not robust global identity or idempotency.
- Memory records contain a fact and timestamp but not confidence, detailed provenance, visibility, retention, or correction metadata.
- The SQL schema enables row-level security on many tables and defines policies for selected owner-scoped tables; enabling RLS does not establish complete policy coverage for every table.
- The inspected files do not establish account migration, multi-device sync, conflict resolution, export, deletion propagation, backup, or crash recovery.
- Auth persistence uses AsyncStorage; the new project must independently assess protected token storage and its threat model.

### Language-world requirements added

1. Give every learner a stable, isolated identity, including local anonymous learners; never use shared fallback identities.
2. Scope every personal local key, remote row, cache, event, media object, and queued mutation to the learner.
3. Define explicit account-linking migration with validation, idempotency, conflict handling, and recovery.
4. Declare offline capability and distinguish local save, queued sync, and confirmed remote sync.
5. Use durable outbox/saga semantics for cross-domain effects and recover interrupted operations.
6. Define conflict policies by data type; never apply last-write-wins indiscriminately to stories, learning history, memory, or creations.
7. Separate world-authored content from learner-owned state, transient session state, caches, and operational records.
8. Define UTC, world-local, monotonic, and untrusted device-clock semantics; bound offline simulation.
9. Give personal memories provenance, confidence, purpose, scope, retention, correction, and deletion semantics.
10. Establish data minimization, explicit voice/AI consent, provider transparency, secure secret handling, and backend authorization tests.
11. Support portable export, deletion across derived data/media, backup, restore, and corruption recovery.
12. Test account switching, anonymous migration, offline replay, duplicate events, clock changes, and cross-learner authorization.

### New Language-world document

Created `docs/PERSISTENCE_PRIVACY_AND_SYNC.md`, a working specification for identity, local-first operation, sync/conflicts, durable events, memory, privacy, security, creation/media lifecycle, export/deletion, backup, recovery, and acceptance tests. It is linked from Master Blueprint Section 43.

**Audit status remains ongoing.** These findings are limited to selected files and are not a complete security review or proof of end-to-end behavior.


## 53. Creative experiences, Journey Book, and personal archive audit

### Selected GoPAL-AI sources inspected

- `src/engines/creation/creationStudio.ts` — four creation templates and create/list operations.
- `src/features/journey/screens/JourneyBookScreen.tsx` — timeline, milestones, then-versus-now, artifact shelf, transcript entry point.
- `src/features/journey/screens/MemoryMuseumScreen.tsx` — postcards, creations, artifacts, and memory views.
- `src/features/journey/components/TimeCapsuleModal.tsx` — future-self message and unlock flow.
- `src/features/journey/components/ConversationArchiveModal.tsx` — transcript archive UI.
- Selected types and methods in `src/lib/localStore.ts`.

### Recovered ideas

- Four initial creative forms: postcards, phrase cards, memory boards, and dialogue comics.
- A personal Journey Book with chronology, milestones, artifacts, and learning reflections.
- A Memory Museum grouping several types of keepsakes.
- Future-self time capsules.
- Conversation excerpts as material for later language practice.
- Journey events linked to creation.

### Limitations observed

- CreationStudio stores a small text-oriented record (type, title, subtitle, content, theme, tags, timestamp); no full editor, revision, or deletion lifecycle was observed in that engine.
- Creation and journey-event writes are sequential, not one atomic operation.
- Creation, postcard, and capsule IDs use timestamp-derived values.
- Postcards store location and image-theme metadata, not a demonstrated editable composition or media ownership lifecycle.
- Journey Book displays a timeline and learning reflections but does not demonstrate a full learner-authored journal editor.
- Memory Museum combines distinct object types in one view; the inspected screen loads local records without visibly passing a learner scope.
- ConversationArchiveModal contains hard-coded sample sessions; its Listen action shows a text toast rather than actual audio playback.
- Transcript examples include scores and feedback but do not establish authentic stored transcripts or validated speech assessment.
- TimeCapsuleModal exposes an early-unlock demo action, bypassing the intended date.
- Capsule records do not encode explicit owner scope, privacy controls, revision policy, milestone conditions, or trusted clock behavior.
- Related LocalStore getters use seeded examples, so an empty first-run archive is not assured.
- The selected models do not establish consistent structured source documents, versioning, media lifecycle, sharing permissions, export, or deletion.

### Requirements carried into Language-world

1. Treat journal, phrasebook, postcards, comics, boards, museum, capsules, and transcript archive as distinct experiences sharing robust archive infrastructure.
2. Preserve editable structured source; treat previews and exports as derivatives.
3. Require stable learner-owned IDs, schema versions, timestamps, revisions, source provenance, media references, privacy state, and lifecycle state.
4. Keep default visibility private; sharing is a deliberate, reviewable action.
5. Clearly label AI-generated suggestions and preserve learner authorship.
6. Do not auto-archive every conversation, mistake, or action as personal memory.
7. Preserve transcript truthfulness and audio provenance; never fake playback or assessment.
8. Make time capsules respect declared unlock rules, time zones, offline behavior, and deletion.
9. Ensure cultural artifacts have provenance and appropriate expert review; do not gamify sacred or sensitive objects.
10. Support accessible editing, multilingual scripts, export, conflict recovery, and deletion propagation.
11. Sequence a small set of useful experiences before expanding the creative catalogue.

### New Language-world document

Created `docs/CREATIVE_EXPERIENCES_AND_PERSONAL_ARCHIVE.md`, a working specification for experience families, archive architecture, structured creative objects, revisions, media lifecycle, discovery events, privacy/sharing, AI boundaries, cultural integrity, accessibility, sequencing, and acceptance tests. It is linked from Master Blueprint Section 44.

**Audit status remains ongoing.** Findings are limited to selected source files and do not prove full end-to-end behavior.


## 54. Consolidated GoPAL-AI idea recovery and transfer audit

### Research consolidation

Created `docs/GOPAL_IDEA_RECOVERY_AUDIT.md` as the consolidated product-idea recovery record. It draws on the GoPAL-AI master blueprint, project overview, large product specification and its 173 numbered concepts, feature audit, completion tracker, Emerald Valley world specification, learning/game catalogues, audio design notes, and selected source across world, learning, Cassidy, narrative, travel, audio, journey, memory, creation, economy, and persistence domains.

### Repository inventory and scope

The GoPAL-AI main tree was retrieved without truncation: 709 entries (608 files). The audit distinguishes inventory from content inspection and does not claim every source line or runtime behavior was verified.

### Transfer boundary

The user explicitly clarified that Language-world should take **ideas only**. No GoPAL-AI code, images, models, GLB/GLTF, Blender projects, rigs, skeletons, animation clips, audio, media, asset packages, manifests, registries, importers/exporters, validators, production scripts, factories, or existing pipeline implementation may be transferred. Cassidy's design is owned by the user and will be preserved through the user's approved design material, not by importing repository artwork.

### Main recovered idea families

- A place worth returning to; gentle re-entry and meaningful continuity.
- A multi-world universe with distinct geography, culture, ecology, stories, and sound.
- Contextual language learning and learner-selected experience intentions.
- A 60-seed game catalogue across discovery, puzzle, arcade, social, listening, adventure, and creative families.
- Cassidy and resident autonomy, routines, relationships, boundaries, and evidence-based character observations.
- Micro-stories, mysteries, clues, environmental evidence, and story arcs at multiple scales.
- Time, weather, seasons, plants, ecology, festivals, and bounded offline continuity.
- Interactive objects, collections, inventory, crafting, personal spaces, and object provenance.
- Passport, travel, destination discovery, and journey identity.
- Context-aware audio, world radio, quiet moments, and learning-audio integrity.
- Journey Book, Memory Museum, postcards, phrasebooks, comics, personal notes, time capsules, and learning recaps.
- Experience Director, World DJ, Surprise Me, explainable recommendations, session sizing, and return-friendly design.
- Optional future shared presence and community experiences.

### Main failure lessons

The consolidated report records registry mismatch, disconnected surfaces, aspirational-vs-implemented confusion, duplicate ownership, in-memory authority, UI-local progress, non-atomic side effects, weak event identity, unscoped personal storage, seeded demo data, overclaimed learning evidence, template-heavy character behavior, wall-clock shortcuts, fake/incomplete media actions, demo bypasses, catalogue inflation, and technical spectacle preceding product proof.

### Language-world decisions

The report includes early specification ideas (first-open/return rituals, persistent home, ambient learning, review stories, explanation modes, practical mission preparation, world-event scale, progression dimensions, accessibility, progressive fidelity), later cross-industry concepts, a review of player-facing surfaces/reachability, a transfer matrix (adopt, redesign, expand, candidate, defer, reject), new opportunities beyond GoPAL-AI, evidence labels, remaining research boundaries, and a product-owner review checklist. It does not approve implementation scope. The Master Blueprint now links this consolidation in Section 45.

**Status:** A substantial idea-recovery consolidation is complete. The wider GoPAL-AI source audit is still targeted rather than line-by-line, and product-owner review remains open. No GoPAL-AI implementation or asset is transferred; no Language-world implementation is authorized.


## 55. Master Blueprint reconciliation: missing decisions and document consistency

### Scope of review

Compared the current Master Blueprint, World & Universe Bible, Cassidy Character Bible, Experience Catalogue, Learning Design, World Simulation, World Objects and Spaces, Travel, Cinematics, Asset Handoff/Pipeline, Audio/Voice, Narrative, Persistence/Privacy/Sync, Creative Archive, Engine Evaluation, Roadmap, Architecture Decisions, Work Register, and the consolidated GoPAL-AI Idea Recovery Audit.

### What is already captured

The major idea families—place-worth-returning-to, distinct language worlds, contextual learning, broad games/activities, Cassidy/resident autonomy, stories/mysteries, simulation/ecology, objects/spaces, cinematic travel, audio identity, personal archive, and healthy personalization—are represented in the current specifications. They do not need to be repeatedly rediscovered.

### Product-level gaps

The comparison identifies unresolved or insufficiently integrated decisions:
- Audience, age policy, initial learner profile, and proficiency range.
- First-release promise, content boundary, and excluded features.
- End-to-end user journeys, navigation, activity entry/exit/resume, and re-entry.
- One bounded Experience Director contract across domains.
- Complete universe premise, definitive Emerald Valley geography, first destination, and actual world bibles.
- Cassidy canon approval, voice/performance direction, knowledge boundaries, and authored-versus-generated dialogue policy.
- Unified AI/voice governance, provider boundaries, consent, retention, truthful capability claims, and fallback.
- Progression/economy/monetization policy that does not default to XP or reward grinding.
- Operations, content updates, support, diagnostics, and live-event policy.

### Cross-document inconsistencies found

1. The Master Blueprint work order was stale relative to the supporting documents already created.
2. The Master Blueprint supporting-document table named three files that did not match the repository's actual canonical filenames.
3. The Roadmap still included legacy GoPAL asset inventory/licensing inspection, conflicting with the user's ideas-only transfer boundary.
4. Roadmap Phase 4 wording could be misread as importing GoPAL-AI Cassidy assets; it now explicitly refers only to user-approved material supplied for independent production.
5. The Work Register contained literal escaped newline artefacts and an outdated audit section count.
6. The World Bible correctly labels place lists as seeds, but the Master Blueprint still needs to keep recovered concepts distinct from approved world canon.
7. Architecture decision numbering contained a duplicate ADR-010 and duplicate ADR-013 after the first correction; the final numbering is now sequential through ADR-016.

### Changes made in this reconciliation pass

- Created BLUEPRINT_RECONCILIATION.md.
- Updated Master Blueprint Sections 31–32, corrected supporting-document links, and added Section 46.
- Updated Roadmap Phase 1 to a targeted ideas-only research checkpoint and clarified Phase 4 Cassidy reference sourcing.
- Updated the Blueprint Work Register and README.
- Renumbered the Architecture Decisions list to remove duplicate ADR identifiers.

### Status and evidence limits

These changes were verified by fetching the updated documents again. This is a document-level consistency review, not proof that all product decisions are resolved or that every system specification is implementation-ready. The Product Systems Audit remains selected-source research, not a line-by-line or runtime audit.

**Next critical design artifact:** TECHNICAL_ARCHITECTURE.md, followed by UX/accessibility/navigation, product scope/age policy, and AI/voice governance. No engine, backend, or service provider is selected by this reconciliation. No implementation is authorized.


## 56. Technical Architecture working specification

Created TECHNICAL_ARCHITECTURE.md as an engine/backend-neutral architecture draft. It defines logical layers, domain state ownership, explicit command/query/event boundaries, state classes, durable cross-domain operations, idempotency/recovery, runtime lifecycle, separate time domains, offline/sync classes, content pack and semantic asset contracts, cinematic/travel integration, AI/voice boundaries, privacy/security, observability, and testing.

The architecture deliberately leaves engine, backend, database, authentication, AI, speech, and content-delivery providers open. It makes no implementation authorization and requires reconciliation with UX/navigation, product scope, AI/voice governance, and production/quality specifications.

**Status:** working draft created and linked from the Master Blueprint, README, and Work Register; technical and product-owner review remain open.


## 57. UX, navigation, and accessibility working specification

Created UX_AND_ACCESSIBILITY_SPEC.md to address a product-level gap identified in the reconciliation. It defines a world-first information architecture without copying GoPAL-AI's tabs; first-launch and return journeys; exploration, learning, story, creative, travel, and settings journeys; activity lifecycle and recovery; minimal HUD; touch/spatial interaction; vision, hearing, motion, motor, cognitive and sensory accessibility; localization; notification boundaries; and save/sync/loading/error UX.

Audience, age policy, final navigation, input modes, accessibility conformance target, and first-release journey maps remain open. This is a working specification, not an approved UI design or implementation authorization.


## 58. Product scope: Emerald Valley home identity, learning choice, and upgrade progression

Created `PRODUCT_SCOPE_AND_RELEASE_DEFINITION.md` to formalize the product owner's additional requirements.

Key product rules:
- Emerald Valley is the learner's home world, not the singular learning goal or a course to complete. It supports everyday conversations with Cassidy and residents, ordinary life, exploration, local stories, games, optional learning, and return visits.
- Learning is universe-wide and offers multiple formats: conversations, focused practice, listening, reading, writing, quizzes, puzzles, mini-games, stories, investigations, cultural activities, and location-based scenarios.
- Buildings and locations in Emerald Valley should be upgradeable. Upgrades can visibly change exteriors, interiors, facilities, equipment, atmosphere, and available activities.
- Scenarios should also evolve: location upgrades may add new variants, roles, dialogue branches, props, challenges, clues, or richer situations while preserving accessible/replayable earlier options.
- Learners earn points through meaningful learning and participation and can spend them on building/scenario upgrades. Point balance is not a proxy for language mastery; progress domains remain separate.
- Progression must avoid grind, absence penalties, manipulative streaks, pay-to-progress assumptions, and rewards for trivial farming.

The specification includes home-life, learning-choice, building-development, story/discovery, and travel loops; a candidate first-release slice; open decisions; and acceptance gates. Exact upgrade trees, currency design, point awards/costs, audience, language scope, and first-release content remain unapproved.

**Status:** working product-scope draft created and linked; product-owner review and cross-document reconciliation remain open. No implementation or economy experiment is authorized.
