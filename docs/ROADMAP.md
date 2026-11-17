# Project Roadmap

This roadmap is evidence-led. Each phase has an exit gate; do not skip the engine and Android proof merely to produce a large scaffold.

## Phase 0 — Repository and product foundation

- [x] Establish Language-world as an independent project.
- [x] Record the no-Expo constraint.
- [x] Establish GoPAL-AI as read-only reference.
- [x] Establish Emerald Valley as home world, with distinct worlds per language.
- [x] Establish Cassidy as a canonical human female character.
- [x] Record initial architecture decisions and audit baseline.
- [ ] Add contribution rules, decision log conventions, and validation policy.
- [ ] Establish repository CI and documentation navigation.

**Exit gate:** the product boundary and non-negotiable principles are documented.

## Phase 1 — Complete reference audit

- [ ] Inventory all source files and trace entry points/imports/reachability.
- [ ] Map world systems, location content, environment, travel, activities, quests, and interactions.
- [ ] Map Cassidy identity, personality, autonomy, conversation, memory, relationship, animation, and presentation.
- [ ] Map learning systems and contextual learning loops.
- [ ] Map persistence, auth, synchronization, schemas, and privacy.
- [ ] Inventory assets, manifests, provenance, licensing, and integration status.
- [ ] Review docs, tests, scripts, CI, and known defects.
- [ ] Produce a feature disposition register: reuse idea, redesign, defer, or do not adopt—with rationale.

**Exit gate:** no major product subsystem is dismissed without evidence and a recorded decision.

## Phase 2 — Engine/runtime evaluation

- [ ] Define target Android device tiers and minimum supported hardware.
- [ ] Select comparable test scenes and a repeatable measurement protocol.
- [ ] Prototype the same small scene in Godot, Unity, and any other credible candidate.
- [ ] Test character animation, interactions, camera, lighting, scene loading, and transitions.
- [ ] Measure frame-time distribution, memory, build size, load time, thermal behavior, and battery impact.
- [ ] Evaluate asset pipeline, iteration speed, debugging, accessibility, audio, and long-term maintainability.
- [ ] Record results and choose an engine with an ADR.

**Exit gate:** engine choice is supported by real Android evidence. No Expo.

## Phase 3 — Technical vertical slice

- [ ] Establish project structure and automated build/test pipeline.
- [ ] Establish coordinate, camera, scene, collision, navigation, and interaction conventions.
- [ ] Establish replaceable asset manifests and import/validation pipeline.
- [ ] Create one small explorable Emerald Valley location.
- [ ] Add player movement and a small set of world interactions.
- [ ] Add one environmental loop (time/weather/ambient motion).
- [ ] Add a contextual learning interaction with feedback and replay.
- [ ] Add save/restore and background/resume behavior.
- [ ] Measure on target Android tiers and implement fallbacks.

**Exit gate:** a stable, measurable, playable slice with replaceable assets and no architectural dependency on a polished content library.

## Phase 4 — Cassidy foundation

- [ ] Transfer/locate canonical references in the project asset pipeline without changing their identity.
- [ ] Verify source files, provenance, licence, and production status.
- [ ] Define engine-neutral character identity and state contracts.
- [ ] Prototype the human model/rig/animation pipeline using canonical design.
- [ ] Implement movement, attention, expressions, and world interaction.
- [ ] Build personality, perception, dialogue, and bounded autonomy as separate domain systems.
- [ ] Design episodic memory, consent controls, and relationship continuity.
- [ ] Validate character readability and performance on Android.

**Exit gate:** Cassidy is recognizably canonical, embodied, interactive, and independent of renderer-owned intelligence.

## Phase 5 — Home-world life and contextual learning

- [ ] Build a coherent Emerald Valley home location and nearby discoverable places.
- [ ] Add a small cast of inhabitants with believable schedules and interactions.
- [ ] Integrate learning into errands, conversations, signs, objects, stories, and activities.
- [ ] Add journal/discovery and meaningful world-state changes.
- [ ] Ensure focused study remains available without replacing the living-world experience.

**Exit gate:** the learner can return to a persistent place where people and activities remember meaningful events.

## Phase 6 — First distinct language world

- [ ] Choose the first target language/world based on product priorities and content readiness.
- [ ] Author its geography, climate, ecosystems, architecture, settlements, inhabitants, and cultural context independently.
- [ ] Design language-specific learning situations and progression.
- [ ] Build meaningful travel from Emerald Valley.
- [ ] Test that the world is not a reskinned Emerald Valley.

**Exit gate:** the first language world has a distinct identity and a complete small playable loop.

## Phase 7 — Expand the universe

- Add further language worlds with their own authored identity.
- Expand stories, characters, wildlife, festivals, activities, and travel.
- Improve localization, voice, accessibility, and low-end device support.
- Add shared universe systems only where they genuinely improve coherence.

## Continuous quality gates

Every feature must have:
- A documented owner and state model.
- Tests for core domain behavior.
- Explicit lifecycle and persistence behavior.
- Accessibility and localization considerations.
- Performance budgets and lower-end fallbacks.
- Asset provenance/licence and replacement metadata where relevant.
- A clear distinction between implemented, tested, and merely planned.
