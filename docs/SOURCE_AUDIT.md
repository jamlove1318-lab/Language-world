# GoPAL-AI Source Audit

## Purpose and boundary

This is a working audit of the GoPAL-AI repository as a read-only reference for Language-world. It is not a claim that every file, asset, workflow, or runtime path has been fully reviewed. Findings must be verified as the audit progresses.

**Reference repository:** https://github.com/jamlove1318-lab/GoPAL-AI  
**New implementation repository:** https://github.com/jamlove1318-lab/Language-world

Do not commit, edit, delete, rename, or change configuration in GoPAL-AI.

## Repository inventory snapshot

A previously retrieved recursive Git tree reported:
- 709 entries total: 608 files and 101 directories.
- TypeScript: 223 files; TSX: 104; Markdown: 77; GLB: 65; Python: 42; JSON: 23; MJS: 13; PNG: 12; ZIP: 10; plus other formats.
- Major top-level concentrations included `src/` (324 files), `assets/` (108), `docs/` (61), `factory/` (34), `tools/` (16), and `scripts/` (14).
- Within `src/`, world engine and world feature code are especially substantial; Cassidy, learning, and character systems are also significant.

Counts are a snapshot, not a measure of quality or integration.

## Previously identified product surfaces

A prior audit described two overlapping product directions:
- A conventional reachable app flow with onboarding, dashboard, flat lesson list, tutor chat, and profile.
- A richer world/path/lesson experience with map, lesson route, progression, and world systems that appeared partially disconnected from the primary navigation.

This needs fresh import/navigation/runtime tracing before final conclusions are made.

## Findings inspected in this audit pass

### Living world runtime

Inspected:
- `src/features/world/data/livingWorldRuntime.ts`
- `src/features/world/data/livingWorldSimulation.ts`
- `src/features/world/data/livingWorldManifest.ts`

Observed capabilities include location loading and travel events, world objects, interaction/action execution, movement and collision, simulation snapshots, residents/characters, schedules/behaviors, navigation paths, vehicles/routes, activities, learning, games, quests, and save/restore.

Risks to investigate:
- Runtime ownership and lifecycle across multiple presentation surfaces.
- Event producer/consumer coverage and event duplication.
- Simulation tick policy and visibility/relevance tiers.
- Whether state mutations are deterministic and safely persisted.
- Whether location catalogs and language-world identity agree.

### Language-world registry

Inspected `src/features/world/data/livingLanguageWorlds.ts`.

It defines Emerald Valley as home and includes Japanese and French world entries, with location IDs supplied by another module. This is a useful concept but not a complete multi-world universe specification.

A separate `livingWorldManifest.ts` contains a generic seven-entry list (Emerald Valley, Learning Campus, Azure Coast, Cloudpine Village, Moonveil Kingdom, Nova Outpost, Chaos Arena). This is not the intended final language-world model. Do not copy it as the new universe architecture.

### Cassidy visual identity and asset contracts

Inspected:
- `docs/cassidy/canonical-reference.md`
- `docs/cassidy/phase-3b-renderer-contract.md`
- `src/characters/cassidyCharacterMaster.ts`
- `src/characters/cassidyProductionAssetRegistry.ts`

The canonical reference says Cassidy's approved concept is the visual source of truth. The character master contract defines face, eyes, hair, body, outfit, accessory, expressions, animations, and cross-world consistency. The renderer contract correctly separates character state from renderer implementation.

The production registry lists canonical concept, turnaround, face, hair, outfit, expressions, pose, accessory, materials, model, rig, and animation records. Several production records are still pending. A registry entry or report is not proof that a real model/rig/animation binary exists, is licensed, or is integrated.

Important: Cassidy is a human female character. Never reinterpret her as an animal, fox, mascot, or anthropomorphic character.

## Existing audit baseline from earlier work

Earlier static analysis identified potential duplication across AI, XP, streak, themes, and UI systems; unlinked learning/path surfaces; possible dead or legacy code; mutable progression state; and implicit cross-store dependencies. These are leads, not deletion instructions. Trace imports, navigation, runtime use, tests, and persistence before classifying anything as unused.

## Audit work still required

- Trace all source files, entry points, imports, routes, and actual reachability.
- Identify authoritative owners for world, Cassidy, learning, progress, memory, and settings.
- Map all event types to producers, subscribers, side effects, and persistence.
- Inspect all language-world location data and world-specific content.
- Review all 65 GLB files, manifests, Blender archives, source provenance, licences, and runtime references.
- Visually inspect canonical Cassidy references and compare every candidate runtime asset.
- Verify whether reported Cassidy model/rig/animation exports are actually tracked and integrated.
- Inspect Supabase schema, migrations, row-level security, authentication, and offline behavior.
- Review all docs for superseded, contradictory, incomplete, or aspirational claims.
- Inspect CI, tests, asset validation, build scripts, and reproducibility.
- Validate representative behavior on actual Android hardware.

## Audit classification vocabulary

- **Active:** demonstrably reachable and used in the current runtime.
- **Reusable idea:** product behavior worth reimagining, independent of existing implementation.
- **Candidate for redesign:** useful capability with architectural or UX weaknesses.
- **Legacy/overlapping:** duplicates another system or represents a superseded direction.
- **Unverified:** evidence is insufficient.
- **Not adopted:** deliberately excluded from Language-world, with a recorded reason.

No source feature should be discarded merely because it is disconnected from one app entry point. Preserve useful ideas in the audit until their value is understood.

## Explicit exclusion: legacy 3D pipeline

The user has explicitly rejected the existing GoPAL-AI 3D pipeline based on prior hands-on testing. It is not a candidate foundation and must not be reused, ported, adapted, or treated as a starting point. This exclusion covers its models/rigs/exports, renderers and runtime integration, asset factories and Blender automation, import/export/validation scripts, manifests, registries, and production contracts.

Cassidy's approved design and character identity information may still be used as creative reference material. No legacy 3D production artifact or pipeline implementation may be used to create her new in-world representation. The new project's visual-production workflow is a fresh design task and must pass an Android device proof of concept before production adoption.

This decision supersedes any earlier audit note that described the old Cassidy/world 3D pipeline as a possible production foundation. Further audit work may identify product ideas worth rethinking, but must not turn the rejected 3D implementation into a reuse candidate.

