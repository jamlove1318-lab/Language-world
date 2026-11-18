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

