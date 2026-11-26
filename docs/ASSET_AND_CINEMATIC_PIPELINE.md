# Replaceable Assets and Cinematic Experience Pipeline

**Status:** Foundation specification; engine-neutral  
**Purpose:** Build the world and its experiences with attractive lightweight assets now, while making later professional asset replacement predictable and low-risk.

## 1. Core decision: build the sockets before the final assets

We will not wait for high-quality art before making the product. Early development should use the best suitable lightweight assets available: carefully selected legal asset packs, simple original placeholders, greybox geometry, temporary audio, and basic animation.

The application must be designed so the graphics designer can later deliver final characters, environments, props, vehicles, materials, effects, and animation without requiring gameplay or story logic to be rewritten.

The quality of the temporary art may be modest. The quality of the asset contracts, scene architecture, cinematic direction, and replacement workflow must not be.

## 2. Asset tiers

Every asset has an explicit tier and provenance:

- **Blockout:** primitive geometry, proxy characters, camera marks, temporary UI, and timing-only animation. Used to test scale, flow, and mechanics.
- **Prototype:** attractive, lightweight, coherent art suitable for early user testing. May come from properly licensed packs or new low-poly work. Not assumed to be final canon.
- **Production:** designer-approved final assets with complete source files, optimized runtime exports, materials, rig/animation support, LODs, collision, and documentation.
- **Variant/platform:** optional lower-cost or higher-quality versions for different Android capability tiers.

Do not mix prototype and production content silently. The asset manifest must state the current tier and replacement status.

## 3. Stable asset contract

Every replaceable asset is addressed by a stable semantic ID, never by a hard-coded file path scattered through gameplay code.

An asset record should describe:
- Stable asset ID and semantic role.
- Asset type: character, environment, building, prop, vehicle, creature, VFX, audio, UI, or cinematic.
- World/location ownership and tags.
- Tier, version, source provenance, creator, and licence/usage rights.
- Source file and runtime import reference.
- Unit scale, forward/up axes, origin/pivot, bounds, and placement anchor.
- Materials, texture sets, shader expectations, and texture budgets.
- Collision/navigation representation, interaction anchors, and occlusion rules.
- Skeleton/rig ID and compatibility version where applicable.
- Supported animation IDs and required animation events.
- LOD/impostor variants and platform quality tiers.
- Dependencies, memory estimate, loading group, and fallback asset.
- Validation status and replacement history.

Gameplay and story systems request semantic assets and capabilities. They do not assume a particular polygon count, mesh layout, file format, or designer's folder structure.

## 4. Character and animation contracts

Character identity and gameplay state are separate from the visual model. Cassidy's canonical identity is not changed when her prototype model is replaced.

A character presentation package should define:
- Stable character ID and visual variant ID.
- Rig/skeleton compatibility ID and retargeting policy.
- Required locomotion set: idle, walk, run, turn, start/stop, slopes/steps as needed.
- Interaction set: attention, pointing, greeting, listening, talking, giving/receiving, reactions.
- Emotional expression set and facial/viseme support appropriate to the chosen art style.
- Named animation events for footsteps, hand contact, prop use, vehicle entry/exit, and dialogue beats.
- Root-motion versus code-driven movement policy per animation.
- Attachment sockets for props, carried objects, and costume items.
- Bounds, collision capsule, navigation footprint, and interaction anchors.
- LOD and fallback policy.

A replacement rig may require a mapping/retargeting profile, but it must not change Cassidy's domain identity, memory, dialogue, or story state.

## 5. Cinematic experiences are a first-class system

The app will contain many directed sequences, not just animated UI transitions. Examples include:
- First launch: Cassidy introduces herself, welcomes the learner, and leads a guided introduction to Emerald Valley as home.
- Home-world tour: Cassidy demonstrates what can be explored, where activities happen, how travel works, and how the learner can return.
- World travel: departure preparations, station/airport arrival, boarding, vehicle interior, journey views, arrival, and first steps in the destination.
- Resident introductions: anticipation and environmental clues before a character is directly revealed; then a character-specific entrance and interaction.
- Secret discoveries and adventures: Cassidy may notice clues, invite the learner, or reveal a place through a directed sequence.
- Story moments: authored camera staging, actor performances, environmental reactions, music, ambience, dialogue, and meaningful choices.

Cinematics must be authored experiences with a clear purpose and an explicit relationship to world state—not long unskippable interruptions.

## 6. Engine-neutral cinematic sequence model

A sequence definition should support:
- Stable sequence ID, version, title, context, prerequisites, and replay policy.
- Actor/character references and scene/level dependencies.
- Timeline duration and named tracks.
- Camera cuts, blends, framing targets, camera rails, and safe framing bounds.
- Actor transforms, movement paths, animation states, facial/emotion cues, and timed events.
- Dialogue, subtitles, voice assets, localization keys, and caption timing.
- Music, ambience, sound effects, mix changes, and audio ducking.
- Environment cues: lighting, weather, time-of-day presentation, particles, and set changes.
- Vehicle/transport choreography and travel-state transitions.
- Choice windows and points where learner agency returns.
- Save checkpoints and idempotent world-state consequences.
- Skip, pause, replay, interruption, background/resume, and accessibility policies.
- Performance budget, asset preload list, fallback shots, and transition cover.

The cinematic director orchestrates presentation. It must not become the authority for character identity, travel ownership, learning outcomes, or durable world state.

## 7. Vehicle travel is a complete experience

A train journey between Emerald Valley and a language world is not a loading spinner disguised as a train animation. It is a sequence of connected states:

1. Invitation or travel decision.
2. Departure location and preparation.
3. Station/airport approach and orientation.
4. Ticket/boarding or equivalent interaction.
5. Boarding animation and interior staging.
6. Journey sequence: moving scenery, soundscape, dialogue/opportunities, optional learner activities.
7. Arrival announcement and destination reveal.
8. Disembarkation and first view of the new world.
9. Destination state becomes active; the previous world is preserved.

Trains, planes, cars, buses, boats, and other transport each have their own reusable choreography and interaction model. In-world transport may be continuous playable movement or a directed cinematic, depending on distance, device budget, and narrative purpose. Do not force every journey to use the same transition.

The travel system owns route, origin, destination, and durable travel state. The cinematic presents the journey and reports completion through stable events. Skipping a sequence must still complete or safely cancel the underlying travel transaction.

## 8. Cinematic lifecycle and accessibility

Every sequence must define:
- When it can start and what state it requires.
- What state changes on success, skip, interruption, or failure.
- Whether it can be replayed and where.
- Whether dialogue can be paused, skipped, or shown as subtitles/transcript.
- Reduced-motion and camera-sensitivity alternatives.
- Captions for speech and meaningful sound cues.
- Controls for voice/music/effects volume.
- Touch-safe controls and clear return to agency.
- Recovery after app backgrounding, process death, or device interruption.

Do not use rapid flashing, excessive camera shake, forced motion, or tiny unreadable subtitle text. Important narrative information must remain available after a skipped cinematic through a journal, recap, dialogue, or other accessible record.

## 9. Asset replacement workflow

1. Designer or asset source supplies a versioned source package and provenance/licence.
2. Import pipeline validates format, scale, axes, pivots, bounds, materials, texture dimensions, rig compatibility, animation names, collision, and dependencies.
3. Generate optimized runtime variants for target Android tiers.
4. Register the package under existing semantic asset IDs or explicitly versioned new IDs.
5. Run automated contract tests and scene-preview tests.
6. Compare screenshots/poses/animation markers and check clipping, foot sliding, collisions, anchors, and camera framing.
7. Run a replacement test: swap the prototype asset for the production asset without modifying gameplay/story code.
8. Profile memory, GPU/CPU cost, load time, and package size on Android.
9. Approve and promote the asset tier; preserve rollback to the prior compatible version.

If a production asset cannot meet the runtime budget, the pipeline should select an approved lower tier rather than break the scene.

## 10. Asset sourcing and legal safety

Temporary external assets must have documented licences and permitted use for the intended distribution. Record author, source, licence version, attribution obligations, modifications, and any restrictions. Do not assume that an asset visible online is free to use.

Designer-created production assets must include agreed ownership/usage terms, source files, export settings, and delivery checklist. Do not use the excluded GoPAL-AI 3D pipeline or its generated outputs.

## 11. First implementation scope

Do not build every cinematic or vehicle now. Prove the architecture with a small vertical slice:
- One lightweight environment and one interior.
- One proxy human character with a minimal but consistent rig and a small animation set.
- One 20–40 second guided welcome sequence with camera, character staging, captions, and audio placeholders.
- One short vehicle travel sequence with departure, journey, arrival, and a durable world transition.
- One interactable prop with a visible persistent consequence.
- A complete asset replacement test using a second model/animation package.
- Skip/replay/restart and process interruption recovery.
- Android performance capture.

The welcome and travel sequences can use temporary art. Their staging, timing, state transitions, and accessibility must be real.

## 12. Acceptance criteria

The pipeline is ready for scale when:
- A designer can deliver an asset using the documented contract.
- An asset can be imported, validated, previewed, and replaced predictably.
- Gameplay and story code remain unchanged during a compatible replacement.
- Characters retain identity and animation events across visual upgrades.
- Cinematics can be authored and sequenced without hard-coding all content into gameplay.
- Travel can be skipped or interrupted without corrupting world state.
- Sequences support captions, reduced motion, pause/skip, and replay policy.
- Android budgets are measured and enforceable.


## 13. Ownership boundaries and technical neutrality

This document is the engine-neutral architecture contract for replaceable assets and cinematic presentation. It is complemented by:
- [Asset Handoff Standard](ASSET_HANDOFF_STANDARD.md) for the graphics designer's delivery package and checklist.
- [Cinematic Experience Blueprint](CINEMATIC_EXPERIENCE_BLUEPRINT.md) for the authored experience, sequence lifecycle, and quality gates.
- [World Objects and Spaces](WORLD_OBJECTS_AND_SPACES.md) for semantic world entities, placement, interactions, and spatial ownership.
- [Travel Experience](TRAVEL_EXPERIENCE_SPEC.md) for durable journey state and route semantics.
- [Audio, Voice, and Soundscape](AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md) for cue IDs, sound bibles, mix, voice, and audio lifecycle.

Keep the following owners separate:
- World/character/story domains own canonical identity, facts, and persistent state.
- Asset registry resolves semantic asset IDs to compatible platform variants.
- Import/validation tooling verifies packages and generates runtime-ready content.
- Character presentation maps semantic action intent to available rig/animation capabilities.
- Cinematic Director orchestrates camera, actor, dialogue, environment, and audio tracks.
- Audio Director and playback adapter resolve and play audio without owning narrative outcomes.
- Travel Director owns journey state; cinematic tracks only present it.
- UI/accessibility layer owns learner controls, captions presentation, and user preferences.

A renderer, animation clip, audio callback, or timeline completion must never become the authoritative source of story, learner, inventory, character, or travel truth.

### Independent production boundary

The new pipeline must be designed and implemented from first principles. It must not import, adapt, wrap, copy, or depend on the GoPAL-AI renderer, asset registry, model/rig/animation assets, Blender scripts, asset factory, import/export/validation/conversion tools, generated outputs, or pipeline-specific contracts. The only permitted relationship is research documentation about lessons learned and requirements.

## 14. Import, versioning, and content safety

- Every manifest has a schema version and every package has an immutable package version.
- Content references semantic IDs and declared capabilities, not physical filenames.
- A compatible replacement may be promoted without changing gameplay/story code.
- An incompatible change requires a new capability profile or explicit migration.
- Import validation runs before content is available to a scene or sequence.
- Runtime loading must verify package compatibility and fallback availability.
- Content rollback must restore the last known-good package without changing learner-owned state.
- Asset packages must be signed or integrity-checked where the distribution architecture supports it.
- Third-party packages must be reviewed for malicious files, licence restrictions, and unsafe embedded content.
- Source projects and runtime exports have separate retention and access rules.
- No pipeline step may overwrite the only editable source copy.

These requirements remain engine-neutral until the engine and importer are selected.
