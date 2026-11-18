# Architecture Decisions

This document records current decisions and explicitly unresolved choices. Update it when evidence changes a decision.

## ADR-001 — GoPAL-AI is reference-only

**Status:** Accepted

GoPAL-AI may be inspected for product ideas, specifications, character canon, assets, and lessons learned. It must not be modified. Language-world is an independent implementation; do not port source code wholesale.

## ADR-002 — No Expo

**Status:** Accepted

Expo is not an option for this project. Do not scaffold Expo or build the product on an Expo/React Native foundation.

## ADR-003 — Emerald Valley is the home world

**Status:** Accepted

Emerald Valley is the home anchor, not the entire universe and not a generic map template. Other languages receive distinct worlds.

## ADR-004 — Every language world has its own identity

**Status:** Accepted

Geography, climate, ecosystems, architecture, inhabitants, culture, soundscape, stories, activities, and learning situations are authored as world-specific content. Shared runtime systems are allowed; reskinned geography is not.

## ADR-005 — Cassidy is a central human character

**Status:** Accepted

Cassidy is human and female. Her canonical design and character facts are sourced from GoPAL-AI reference materials. The new project must preserve that canon. Her runtime intelligence is separated from rendering.

## ADR-006 — Engine/runtime selection requires Android evidence

**Status:** Open pending proof

Candidates include Godot, Unity, and Unreal; other viable options may be evaluated. Compare them with the same representative vertical slice and target Android hardware. Do not choose based on marketing, familiarity, or desktop-only results.

Required measurements: frame time and stability, memory, load/transition time, build size, animation and interaction correctness, thermal/battery behavior during sustained use, tooling workflow, asset pipeline, and low-end fallback feasibility.

## ADR-007 — Hybrid 2D/2.5D/3D presentation

**Status:** Accepted

Choose the presentation method per location and interaction. Avoid a universal mandate to render everything in 3D.

## ADR-008 — Domain simulation is renderer-independent

**Status:** Accepted

World state, learning outcomes, Cassidy identity/personality/memory, and persistence are domain concerns. A renderer consumes visual state/commands and cannot become their source of truth.

## ADR-009 — Replaceable asset pipeline before polish

**Status:** Accepted

Define manifests and conventions for scale, pivots, collision, materials, skeletons, animation, LOD, licensing, and validation before producing large quantities of final assets.

## ADR-010 — Local-first, versioned persistence

**Status:** Accepted in principle

Use domain-specific repositories and versioned data. Specify migrations, synchronization, conflict resolution, export, deletion, and offline behavior before connecting a backend.

## ADR-011 — Living-world simulation is relevance-based

**Status:** Accepted

Use bounded simulation updates and relevance tiers. Visible nearby actors may receive richer updates; distant or inactive systems can use coarse progression or pause. Avoid per-frame domain mutations.

## ADR-012 — Build a measured vertical slice before scaling

**Status:** Accepted

Prove the engine, asset pipeline, camera, interaction, character animation, scene transitions, persistence, and mobile performance in a small playable slice before producing many worlds or polished assets.

## ADR-013 — Main experience is a place, not a dashboard

**Status:** Accepted

The primary navigation experience should be an explorable world. Conventional interface patterns remain appropriate for settings, account, accessibility, forms, and focused utility screens, but not as the main world presentation.

## ADR-010: Reject the Existing GoPAL-AI 3D Production Pipeline

**Status:** Accepted

**Decision:** The existing GoPAL-AI 3D pipeline is explicitly excluded from the new project's implementation foundation. The user has already tested that pipeline and does not consider it suitable.

The new project must not reuse, port, adapt, or depend on any part of that pipeline, including:
- 3D models, meshes, rigs, skeletons, animation assets, or generated character/world exports produced by it.
- Renderer implementations, scene/runtime integration, visual resolvers, or rendering controllers from it.
- Asset-generation/factory scripts, Blender automation, export/conversion steps, validation scripts, or production tooling from it.
- Pipeline-specific manifests, renderer contracts, asset contracts, registries, package layouts, or assumptions that couple content to that workflow.

**Fresh-start requirement:** Design a new asset-production and runtime pipeline independently. Evaluate the target engine and the production workflow together, with Android device proof-of-concept tests before committing to a production approach. Establish new conventions for source assets, scale/units, origins, skeletons, animation naming, materials, textures, collision, LODs, import settings, validation, packaging, runtime loading, and replaceable asset references.

**Permitted reference boundary:** Cassidy's approved character design and character/identity information remain canonical creative references. They do not authorize reuse of the old 3D model, rig, generated outputs, or production pipeline. Recreate her new in-world representation from the approved design using the new workflow. If a design reference is embedded in an old pipeline document, extract only the character-design information—not the pipeline method or technical artifacts.

**Verification gate:** Before any 3D production investment, demonstrate a minimal new pipeline end to end on target Android hardware: create a fresh placeholder asset, import it, place it in a scene, animate and interact with it, replace it with a revised asset without changing gameplay code, and measure performance/resource use. Record the workflow and test results in this repository.

**Reason:** Repeating a previously tried and rejected pipeline would carry forward known weaknesses and undermine the fresh technical foundation this project requires.



## ADR-014 — Lightweight assets first; production assets replace them

**Status:** Accepted

Start with the best suitable lightweight prototype assets available, including original proxies and properly licensed third-party assets. High-quality final assets will be produced by the project's graphics designer later. Stable semantic asset IDs, versioned manifests, rig/animation contracts, import validation, platform variants, and replacement tests must be designed before asset volume grows. Compatible production assets must replace prototypes without gameplay/story rewrites. No old GoPAL-AI 3D pipeline or generated outputs may be reused.

## ADR-015 — Cinematics and directed travel are first-class systems

**Status:** Accepted

The experience includes authored cinematic sequences: Cassidy's first-launch welcome and home-world introduction, resident reveal sequences, story/adventure moments, and transport journeys between and within worlds. Sequences may orchestrate cameras, character performance, animation, dialogue, subtitles/captions, sound, environmental cues, vehicles, and learner choices. They are data/content-driven where practical, accessible, skippable, replayable according to policy, and recoverable after interruption. Durable travel, character, and world state remains owned by domain systems; cinematic presentation cannot become the source of truth.
