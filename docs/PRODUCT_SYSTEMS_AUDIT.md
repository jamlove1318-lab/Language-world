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
