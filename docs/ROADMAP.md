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

- [x] Retrieve the complete repository tree and inventory the reference archive.
- [x] Review principal product specifications and the early/later idea catalogues.
- [x] Inspect selected high-value source domains and record evidence limits.
- [x] Consolidate the ideas-only transfer matrix and failure lessons in GOPAL_IDEA_RECOVERY_AUDIT.md.
- [ ] Perform only targeted follow-up research where a concrete Language-world product question requires it.

**Exit gate:** major product idea families have a documented adopt/redesign/defer/reject decision. This is not a line-by-line source audit or runtime validation; legacy assets and pipeline inspection are out of scope.

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
- [ ] Establish replaceable asset manifests and import/validation pipeline using lightweight prototype assets first.
- [ ] Define asset tiers, provenance/licensing, semantic IDs, rig/animation contracts, and designer handoff requirements.
- [ ] Prove that a higher-quality asset can replace a prototype without gameplay/story code changes.
- [ ] Prototype Cassidy's first-launch welcome and Emerald Valley introduction with proxy assets.
- [ ] Prototype a directed cinematic sequence with camera, character staging, animation, dialogue/captions, audio, skip/replay, and interruption recovery.
- [ ] Run a graphics-designer handoff exercise: replace a proxy character/prop with an upgraded asset without gameplay/story code changes.
- [ ] Prototype a complete transport journey with departure, vehicle boarding, journey, arrival, and durable world transition.
- [ ] Create one small explorable Emerald Valley location.
- [ ] Add player movement and a small set of world interactions.
- [ ] Add one environmental loop (time/weather/ambient motion).
- [ ] Add a contextual learning interaction with feedback and replay.
- [ ] Add save/restore and background/resume behavior.
- [ ] Measure on target Android tiers and implement fallbacks.

**Exit gate:** a stable, measurable, playable slice with replaceable assets, one working cinematic, one complete travel sequence, and no architectural dependency on a polished content library.

## Phase 4 — Cassidy foundation

- [ ] When the user is ready, receive or locate the user's own approved canonical Cassidy design material for the independent Language-world production process.
- [ ] Verify provenance and usage permission for user-designated material. Do not copy GoPAL-AI repository artwork, models, rigs, animation, or other assets.
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
