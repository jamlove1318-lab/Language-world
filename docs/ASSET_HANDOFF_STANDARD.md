# Graphics and Asset Handoff Standard

**Status:** Initial designer/engineering contract  
**Audience:** Graphics designer, animator, technical artist, engineer  
**Goal:** Make early placeholder assets replaceable by final production assets without rewriting game logic.

## 1. Working agreement

The designer does not need to create final-quality assets for the first prototype. Engineering will use lightweight assets with the correct approximate scale, role, silhouette, pivot, rig class, and animation contract.

The designer can later deliver higher-quality versions against the same contract. The team agrees IDs and compatibility rules before production batches are created.

A visual upgrade should be a content change, not a gameplay rewrite.

## 2. Required package structure

A delivered asset package should use a predictable structure. This is a suggested handoff layout, not a restriction on the designer's preferred authoring project:

```text
asset-package/
  package.json
  manifest.json
  source/
    editable-source-files...
  runtime/
    model-and-material-exports...
  textures/
  animations/
  previews/
    thumbnail.png
    front.png
    side.png
  validation/
    notes.md
```

Keep editable source files. Runtime exports are generated deliverables and should not be the only surviving copy.

## 3. Semantic IDs

Use stable IDs based on meaning, not filenames or quality level.

Examples:
- `character.cassidy`
- `world.emerald_valley.station.main`
- `vehicle.train.valley_express`
- `prop.station.departure_board`
- `creature.spanish_world.<specific-creature-id>`
- `cinematic.onboarding.welcome`

Do not encode `lowpoly`, `final`, `v2`, or a file extension into the semantic identity. Quality/version is metadata. A prototype and its production replacement can implement the same semantic asset ID if they satisfy the same contract.

## 4. Example manifest

This is an illustrative engine-neutral shape. The eventual import tool may add fields, but gameplay should depend only on stable IDs and declared capabilities.

```json
{
  "schemaVersion": 1,
  "packageId": "character-cassidy-prototype",
  "packageVersion": "0.1.0",
  "tier": "prototype",
  "creator": "Language World team",
  "license": {
    "name": "original-or-recorded-third-party-license",
    "source": "record-source-location",
    "attributionRequired": false,
    "commercialUseAllowed": true,
    "modificationsAllowed": true
  },
  "assets": [
    {
      "id": "character.cassidy",
      "type": "character",
      "worlds": ["world.emerald_valley"],
      "runtimeFile": "runtime/cassidy-placeholder",
      "units": "meters",
      "forwardAxis": "+Z",
      "upAxis": "+Y",
      "origin": "ground_center",
      "boundsMeters": [0.6, 1.75, 0.45],
      "rig": {
        "skeletonId": "humanoid.languageworld.v1",
        "compatibilityVersion": 1,
        "retargetProfile": "humanoid-standard-v1"
      },
      "capabilities": [
        "locomotion",
        "greeting",
        "listening",
        "talking",
        "pointing"
      ],
      "animations": {
        "idle": "cassidy.idle",
        "walk": "cassidy.walk",
        "greet": "cassidy.greet",
        "talk": "cassidy.talk"
      },
      "lod": {
        "near": "runtime/cassidy-near",
        "far": "runtime/cassidy-far"
      },
      "fallbackAssetId": "character.cassidy.proxy"
    }
  ]
}
```

The example is a contract sketch, not a committed production schema. Fields and validation rules must be finalized alongside the selected engine and first asset importer.

## 5. Designer delivery checklist

For every character:
- Editable source project and runtime exports.
- Front, side, and back reference views; neutral pose.
- Agreed real-world height and proportions.
- Forward/up axes, origin, and scale.
- Rig/skeleton identifier and version.
- Skin weights and deformation check.
- Required animation list, names, duration, loop behaviour, and root-motion notes.
- Facial expression/viseme support where required.
- Attachment sockets and interaction anchors.
- Collision/navigation guidance.
- LODs or agreed platform variants.
- Texture/material inventory and expected memory cost.
- Preview renders and known limitations.

For every environment, building, prop, or vehicle:
- Dimensions, origin, orientation, and placement anchors.
- Collision meshes and navigation blockers.
- Interaction points and access/entry/exit anchors.
- Material and texture inventory.
- LOD/platform variants where needed.
- Interior/exterior boundaries and occlusion expectations.
- Animation hooks for doors, wheels, moving parts, and effects.
- Preview renders and runtime cost notes.

For every animation:
- Target rig and compatibility version.
- Stable animation ID and clip name.
- Start/end pose and loop policy.
- Root-motion or in-place policy.
- Named events (footsteps, contact, handoff, door open, etc.).
- Expected blend transitions and interruption behaviour.
- Preview on the agreed reference character.

## 6. Animation naming and event policy

Names should describe the action and remain stable. Example IDs:
- `cassidy.locomotion.idle`
- `cassidy.locomotion.walk`
- `cassidy.interaction.greet`
- `cassidy.interaction.point`
- `cassidy.performance.surprised`
- `resident.<id>.reveal.entrance`
- `vehicle.train.door.open`
- `vehicle.train.departure`

Animation events are presentation signals. They can request a footstep sound or notify a cinematic track that a hand reached a prop. They must not independently grant items, complete quests, or commit travel. Domain systems validate and commit those outcomes.

## 7. Replacement compatibility

A new asset can replace an existing semantic ID only if:
- Its dimensions and anchors remain within agreed tolerances, or an explicit placement migration is supplied.
- It satisfies the required rig and animation capabilities.
- Interaction/collision/navigation contracts remain valid.
- Cinematic framing remains valid or updated camera metadata is supplied.
- Memory, texture, material, and draw-call budgets are approved for the target tier.
- It passes import, preview, automated, and Android device checks.

If it cannot satisfy the old contract, introduce a new version/capability profile and migrate scenes deliberately. Never silently break existing content.

## 8. Quality tiers and Android variants

A single semantic asset can map to different runtime variants:
- **Prototype:** lightweight and visually coherent, used while systems are built.
- **Standard:** intended default production quality for supported devices.
- **High:** enhanced geometry/material/texture detail for stronger devices.
- **Fallback:** reduced material/geometry/effect cost while preserving silhouette, readability, and interaction.

Quality selection should be based on device capability and measured budgets, not only screen resolution. A high tier should never be mandatory for a story or learning interaction to function.

## 9. Provenance and ownership

Every external asset needs a recorded source and exact licence terms. Every commissioned asset needs written ownership/usage rights and permitted modification/distribution. Include attribution obligations, restrictions, and creator credits. Never assume free-to-view means free-to-ship.

The old GoPAL-AI 3D models, rigs, animations, generated exports, factory scripts, Blender automation, and pipeline contracts are excluded. New production must be authored and processed independently.

## 10. First handoff exercise

Before commissioning a large asset library, run a small shared test with the designer:
1. Engineering supplies one proxy human character and one proxy prop with semantic IDs and dimensions.
2. Designer returns one upgraded model and one animation against the agreed rig/contract.
3. Engineering imports and validates the package.
4. Replace the proxy references without modifying gameplay or story logic.
5. Verify anchors, collision, animation events, camera framing, and Android performance.
6. Record friction and revise the contract before scaling production.


## 11. Authoritative contract boundaries and validation

This document is the artist-facing delivery checklist. The engine-neutral asset/runtime boundary and cinematic integration are described in [Asset and Cinematic Pipeline](ASSET_AND_CINEMATIC_PIPELINE.md). The world-object semantic identity and placement contract is described in [World Objects and Spaces](WORLD_OBJECTS_AND_SPACES.md). Audio cue identity and delivery are described in [Audio, Voice, and Soundscape](AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md).

The following rules are mandatory:
- A semantic ID identifies meaning, not a file, export, artist, engine, or quality tier.
- A package manifest must declare schema version, package version, asset IDs, dependencies, provenance, licence/rights, compatibility, and validation status.
- Runtime exports must be reproducible from retained editable source files and documented export settings.
- A replacement may change visual implementation, but must preserve declared capabilities and compatibility or supply a deliberate migration.
- Animation clips and events are presentation signals. They cannot directly commit inventory, story, learning, relationship, or travel state.
- Every delivery must include a known-good fallback and rollback path for the supported target tier.
- No GoPAL-AI model, rig, animation, generated export, importer, exporter, validator, conversion script, manifest contract, or asset-factory code may enter the new production pipeline.

### Minimum automated validation

The future independent importer/validator must check:
- Manifest/schema validity and unique semantic IDs.
- Required source files, runtime exports, hashes, and package dependencies.
- Licence/provenance completeness and rights metadata.
- Units, axis, pivot/origin, bounds, and scale tolerance.
- Rig/skeleton compatibility and required semantic animation capabilities.
- Clip naming, duration, loop, root-motion policy, and event declarations.
- Collision, navigation, interaction, attachment, and entrance anchors.
- Texture dimensions, material/shader requirements, LODs, memory estimate, and platform variants.
- Audio format/loudness/loop/caption metadata where relevant.
- Missing dependencies, fallback availability, and package version compatibility.

These are validation requirements, not a claim that an importer or pipeline has already been built.
