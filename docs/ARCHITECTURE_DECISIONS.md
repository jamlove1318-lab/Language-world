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
