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

