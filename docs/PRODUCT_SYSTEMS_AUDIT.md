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
