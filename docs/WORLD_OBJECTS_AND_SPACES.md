# Language-world — World Objects and Spaces

**Status:** Working specification v0.1; not approved for implementation.  
**Purpose:** Define how places, buildings, interiors, objects, interactions, navigation, inventory, and personal spaces are authored and persist.  
**Source boundary:** GoPAL-AI is a read-only research archive. This is an independent product contract; its object schemas, catalogues, factories, geometry, and storage code are not dependencies.

---

## 1. A place is more than a collection of props

Every world location should feel authored, spatially coherent, and useful to inhabit. A location is a composition of geography, routes, architecture, interiors, objects, people, nature, sound, lighting, and possible experiences.

The system must support:
- Outdoor spaces, streets, paths, parks, markets, stations, harbours, gardens, and natural environments.
- Enterable buildings with distinct interiors and meaningful connections to the outside.
- Multi-room spaces, floors, thresholds, doors, stairs, lifts, platforms, and hidden areas where appropriate.
- Static objects, interactive objects, stateful objects, movable objects, and objects with narrative significance.
- World-specific architecture and construction language rather than generic reskinned kits.
- Temporary placeholders that can be replaced by final art without rewriting gameplay or story logic.
- Persistent changes where they matter, and ephemeral visual effects where they do not.

The map is a spatial world, not a linear lesson route. A learner should be able to understand where places connect and choose where to go.

## 2. Spatial hierarchy

Use a canonical hierarchy:
1. **Universe** — the complete fictional setting.
2. **World** — Emerald Valley or a distinct language world.
3. **Region** — a geographic/cultural subregion within a world.
4. **Settlement/area** — town, neighbourhood, district, village, natural area, or campus.
5. **Place** — a station, café, garden, street, library, workshop, landmark, or other visitable location.
6. **Space** — outdoor scene, building, interior, room, platform, courtyard, tunnel, or connected subspace.
7. **Object/actor** — authored physical or interactive entity within a space.
8. **Interaction/experience** — what can happen with or around an entity.

Each entity has a stable semantic ID independent of its display name, translated label, art filename, renderer node, or storage key. IDs must survive localization, asset replacement, and content revision.

A place must identify its parent world and region, its neighbouring spaces, entry/exit connections, map coordinates or spatial transform, accessibility/navigation metadata, and content version.

## 3. World and place authoring

Each place specification includes:
- Stable ID, name, description, parent world/region, and content version.
- Real-world inspiration, fictional status, and provenance.
- Geographic role and relationship to nearby places.
- Layout, landmarks, sightlines, boundaries, elevation, traversal routes, and entrances.
- Architecture/material palette and environmental identity.
- Day/night, weather, season, and event variants.
- Ambient audio and spatial sound zones.
- Residents, creatures, vehicles, and activity anchors.
- Interactive object placements and experience entry points.
- Accessibility, navigation alternatives, and camera considerations.
- Performance tier and asset fallback profile.
- Narrative facts and persistent state boundaries.

Real-world inspired locations require cultural and geographic review. Fictional locations may be fantastical, but must still be internally coherent.

## 4. Building and interior contracts

A building is not just a sprite or mesh with an enter button. It is a spatial container with a relationship to the world outside.

A building definition should include:
- Building ID, type, purpose, owner/operator, world and place.
- Exterior placement, footprint, collision, entrance locations, and visual variants.
- Interior availability and interior-space IDs.
- Access rules and opening/availability schedule where narratively relevant.
- Navigation graph between entrances and rooms.
- Floors, stairs, lifts, corridors, thresholds, and accessible routes.
- Interior lighting, acoustics, ambient activity, and environmental rules.
- Resident/actor placement and activity anchors.
- Object placements, interactions, and stateful features.
- Exit/return anchors so leaving an interior restores a sensible outside position.
- Content/asset version and replacement bindings.

Interiors may be authored as:
- A unique designed environment.
- A modular arrangement of reusable semantic pieces.
- A simplified interior for a low-performance tier.
- A narrative/cinematic set with controlled staging.

Do not silently teleport between unrelated spaces. Entry and exit should preserve orientation, position, context, and relevant actor/world state. A cinematic transition can present the move, but canonical space state belongs to the world-navigation system.

## 5. Object identity and lifecycle

Every object definition must separate:
- **Identity:** stable semantic ID and object type.
- **Authored definition:** canonical properties and intended role.
- **Placement/instance:** location, transform, orientation, scale, layer, parent/space.
- **Presentation:** visual asset binding, material/variant, animation, visibility, LOD.
- **Physics/navigation:** collision, bounds, traversal blocking, interaction radius.
- **Interaction:** available actions, prerequisites, target, feedback and outcome.
- **State:** active, locked, discovered, collected, repaired, opened, moved, grown, damaged, or other domain-specific state.
- **Ownership/scope:** global world fact, learner-specific state, shared state, or temporary session state.
- **Provenance/version:** author, content version, source, and change history.

An object may have one or more semantic capabilities, but its definition must not mix unrelated domain ownership. A door can be an entrance, a puzzle target, and a story clue; each capability should have a clear contract and authoritative state owner.

### Object lifecycle states
A lifecycle must be defined for stateful objects:
- Authored/placed.
- Discovered or unknown.
- Available/locked.
- Interacted with.
- Changed (opened, repaired, activated, moved, planted, etc.).
- Completed/consumed/collected where appropriate.
- Archived, replaced, or retired.

Not every object needs every state. Transitions must be validated and idempotent. An object cannot be collected twice or restored to an invalid state by replaying an event.

## 6. Interaction model

Interactions should be discoverable and contextually appropriate.

Each interaction definition includes:
- Stable interaction ID and target object/actor.
- Action type and human-readable label.
- Availability conditions and prerequisites.
- Range, focus, input method, and accessibility alternatives.
- Required learner/world/story state.
- Resulting event(s) and authoritative state change.
- Feedback, animation/audio cues, and failure path.
- Cancel, retry, and interruption behaviour.
- Privacy and safety classification if input or user content is involved.

Interaction actions may include inspect, read, listen, talk, enter, exit, use, collect, place, repair, water, open, close, activate, combine, create, travel, or start an experience. These are semantic actions, not a fixed universal button list.

Avoid interaction overload. A place should not display a button for every object at once. Use proximity, gaze/focus, contextual prompts, readable affordances, and optional inspection. Do not rely on tiny touch targets or pixel-perfect taps.

## 7. Navigation, traversal, and spatial connections

- Define walkable surfaces, boundaries, obstacles, collision, and navigation links.
- Use stable route/connection IDs between places and spaces.
- Distinguish pedestrian routes, accessible paths, vehicle routes, rail networks, waterways, and air routes.
- Define slope, stairs, width, barriers, crossings, and movement alternatives.
- Provide clear route feedback and avoid trapping the learner in unreachable areas.
- Support re-entry to the last meaningful position after interruption.
- Fast travel is optional and must not replace authored travel journeys when the journey itself is part of the experience.
- Vehicle/transport systems own route and travel state; object/space definitions provide stations, stops, docks, runways, roads, platforms, and terminals.

## 8. Inventory, collections, and crafting

Inventory is not a universal solution for every object. Decide whether an item belongs in:
- Physical inventory (usable item carried by learner).
- Collection/archive (record of discovery, not a carried object).
- Personal creation library (user-authored artefact).
- Quest/story evidence (clue, document, key, or proof).
- World placement (object that remains in a place).
- Consumable/resource system (if the product has a justified economy).

Each item definition needs stable ID, name/localization, category, provenance, stackability, quantity rules, usability, ownership scope, acquisition source, loss/consumption policy, and asset binding.

Crafting/combination definitions need:
- Explicit input requirements and quantities.
- Output and state changes.
- Whether inputs are consumed.
- Repeatability and idempotency.
- Prerequisites and valid context.
- Failure/undo behaviour.
- Narrative or world consequences.
- Accessibility and explanation.

Do not introduce inventory, crafting, or a resource economy merely because the engine supports it. Every mechanic must serve the experience and world fiction. Avoid forcing learners to grind materials to access stories or learning.

## 9. Personal spaces and care objects

A home, study, garden, room, or personal display area should be a place the learner can shape over time.

Requirements:
- Learner-owned placements and arrangement state.
- Save/reopen and recovery after interruption.
- Clear limits, placement validation, undo/reset, and safe defaults.
- Distinguish owned items from world-authored objects.
- Plant/companion/artifact state follows its own domain lifecycle and privacy scope.
- User-created decorations and media remain user-owned and manageable.
- No punitive decay, abandonment guilt, or loss of personal space due to inactivity.
- Personal space state must not leak between learner accounts on a shared device.

Plant growth and ecological effects are governed by the [World Simulation Specification](WORLD_SIMULATION_SPEC.md); creation ownership and archive rules are governed by the experience and privacy specifications.

## 10. Object and world events

Object interactions emit semantic, stable events. Events should describe what happened, not how a button was pressed.

Examples:
- `space.entered`
- `space.exited`
- `object.discovered`
- `object.inspected`
- `object.opened`
- `object.repaired`
- `object.placed`
- `item.collected`
- `item.used`
- `item.combined`
- `route.unlocked`
- `experience.started`

Each event requires stable event ID, learner/world scope, actor/target, causal ID, timestamp from canonical world clock where relevant, content version, and idempotency key. Durable state transitions must be committed before presentation effects claim success. Event consumers must tolerate retries and out-of-order delivery.

## 11. Replaceable art and placeholder strategy

World content must not reference renderer-specific node names or asset filenames directly.

Use semantic asset bindings such as:
- `world.emerald-valley.landmark.mount-emerald`
- `building.komorebi-cafe.exterior`
- `building.komorebi-cafe.interior.main-room`
- `prop.lantern.paper.warm`
- `vehicle.train.regional.passenger`
- `nature.tree.sugi.mature`

The final naming grammar will be defined in the asset handoff standard. The important rule is that gameplay and world state refer to semantic identities, while the asset manifest resolves the current visual/audio asset for a platform and quality tier.

Placeholder-to-final replacement must preserve:
- Semantic object identity.
- Transform conventions, scale, pivot, orientation, and coordinate system.
- Collision and interaction bounds.
- Navigation and entrance anchors.
- Animation/action semantics.
- Audio attachment points.
- LOD and fallback variants.
- Content compatibility and migration.

A designer should be able to replace the exterior model of a café without changing its interaction IDs, story state, or saved learner data.

## 12. Performance and accessibility

- Use LOD, culling, instancing, simplified collision, and bounded active-object counts.
- Distinguish visual complexity from interaction logic.
- Avoid per-frame updates for static or distant objects.
- Support simplified interior/exterior variants for lower-end devices.
- Provide clear focus states, large touch targets, readable prompts, captions, audio cues, and non-audio alternatives.
- Do not communicate important object state only through colour, animation, or sound.
- Reduced-motion mode must preserve navigation and interaction clarity.
- Interactions must recover safely from app pause, backgrounding, scene unload, and device restart.

## 13. GoPAL-AI research findings

Selected source files reviewed:
- `src/features/world/data/livingWorldObjects.ts`: canonical instance shape for object ID/category/type, transform, visual, collision, interaction, behaviour, state, tags, and metadata.
- `livingWorldObjectCatalog.ts` and `livingWorldObjectRegistry.ts`: broad reusable object archetypes across buildings, interiors, terrain, decoration, infrastructure, transportation, characters, gameplay, fantasy, and sci-fi.
- `livingWorldObjectFactory.ts`: adapts several older catalogs into one object stream.
- `livingWorldInteraction.ts`: derives available actions and nearest interactable target from object data.
- `livingWorldEntrancesObjects.ts`: adapts entrance data into object instances.
- `src/engines/world/livingWorldObjectsStore.ts`: learner-keyed plant/companion/artifact-like objects with growth and memory; includes prefilled sample seed memories and a legacy migration path.
- `src/engines/world/worldInventoryEngine.ts`: pure in-memory inventory add/remove/combine helpers.
- `src/engines/world/worldStateEngine.ts`: persistent flags/history under one global AsyncStorage key in the inspected implementation, not explicitly learner-scoped.
- `livingWorldLocationSchema.ts` and `livingWorldLocationFactory.ts`: location object collections, environment/rule flags, and template-based location construction.

### Recovered strengths
- A common object-instance concept can connect buildings, props, infrastructure, transport, characters, and gameplay.
- Object archetypes cover a broad range of physical and fictional world content.
- Interactions are derived from semantic object properties and proximity.
- Entrances can be represented as world objects.
- Personal living objects and simple inventory concepts exist as design seeds.

### Limitations and cautions
- The factory adapts multiple catalogs rather than proving a single fully authoritative content-authoring source.
- Object state is generic and extensible; domain-specific ownership and lifecycle contracts are not consistently established by the inspected shape.
- The inspected world state store uses a global key and risks cross-learner state leakage.
- The personal object store has learner-keyed storage but includes prefilled demo memory and a special legacy migration path that should not be copied.
- The inventory helper is in-memory; durable inventory, conflict handling, and cross-device recovery are not established by that helper.
- The inspected files do not establish a complete building/interior lifecycle, robust multi-floor navigation, or designer-grade asset replacement workflow.

These are selected-source observations, not a full audit of every object, location, building, or interaction.

## 14. Open decisions

- Which worlds and places require enterable buildings/interiors at launch?
- What is the first-release navigation model and accessibility baseline?
- Which items are inventory, archive, evidence, creation, or world-placed objects?
- Are crafting/resource mechanics needed at all, and where?
- What personal-space customisation is in first release?
- Which world facts are global, learner-specific, or shared?
- What is the canonical asset ID grammar and coordinate convention?
- How will place authoring, object placement, and interior validation be performed?
- What target-device object/actor/geometry budgets apply?

---

**Current status:** Spatial hierarchy, place/building/interior, object identity/lifecycle, interaction, navigation, inventory, personal-space, event, asset replacement, accessibility, and validation requirements documented as a working specification. Launch content and technical contracts remain open. No implementation is authorized.


## 15. Upgradeable buildings, locations, and scenarios

**Product requirement:** Buildings and locations in Emerald Valley can be upgraded over time, and scenarios associated with those places can also gain richer forms and additional options. The learner earns points through meaningful learning and participation and may spend them on these upgrades. See `PRODUCT_SCOPE_AND_RELEASE_DEFINITION.md` for the product-level progression rules and open economy decisions.

### 15.1 Separate authored upgrade definitions from learner state

Model the system as distinct records:
- **Building definition:** stable building identity, function, permitted upgrade branches, prerequisites, and compatible variants.
- **Building instance:** placed world identity and learner/world ownership scope.
- **Upgrade definition:** stable upgrade ID, tier/branch, cost rule, prerequisite, effects, content dependencies, and compatibility/version.
- **Upgrade ownership/state:** learner's acquired upgrades, selected variants, transaction reference, and current effective configuration.
- **Scenario definition:** authored situation, location/context, roles, learning opportunities, objectives, support, difficulty, and outcome contract.
- **Scenario variant:** versioned alternative staging, dialogue, role, prop, clue, task, challenge, or interaction set.
- **Scenario availability/progress:** which variants are available or discovered and the learner's own completion/evidence state.
- **Presentation binding:** replaceable geometry, materials, props, animation, audio, lighting, and scene composition.

A visual model or scene node must never be the identity of a building, upgrade, or scenario.

### 15.2 Upgrade effects

Upgrade effects may include:
- Visible exterior and interior changes.
- New rooms, furniture, equipment, facilities, exhibits, or activity stations.
- New services or interaction affordances.
- New scenario variants, dialogue branches, roles, props, puzzles, clues, or challenge types.
- New replay options or optional complexity.
- Environmental and acoustic changes that make the improvement perceptible.

An upgrade should communicate what changes before the learner spends points. It should not silently remove access to existing activities or make accessibility options conditional on progression.

### 15.3 Scenario progression without forced difficulty

A more developed location may support more varied or richer scenarios, but the learner must retain choice:
- Earlier and familiar variants remain available where appropriate.
- Added complexity is optional or clearly selected.
- Difficulty and language support are independent of building prestige.
- A location upgrade does not imply the learner has mastered the language associated with its scenarios.
- Scenario rewards depend on meaningful participation and evidence, not simply selecting the hardest variant.

### 15.4 Point transactions and domain ownership

The points/economy domain owns the authoritative balance and immutable earn/spend transaction history. The learning domain owns capability evidence; the experience/story domains own their completion outcomes; the world/building domain owns upgrade definitions and applied building state.

An upgrade purchase should be one durable, idempotent operation linking:
1. The learner's explicit upgrade choice.
2. A validated current price and prerequisite check.
3. A points debit transaction.
4. The acquired upgrade record.
5. The resulting building/scenario configuration event.

If any step fails, recovery must not duplicate a debit or grant an upgrade without its corresponding transaction. UI/cinematic presentation must not own the durable purchase state.

### 15.5 Content updates and migration

Upgrade definitions and scenario variants are versioned authored content. When a content update changes an upgrade tree, existing ownership must remain valid or be migrated through an explicit, testable rule. Removed content must not silently erase learner investments. If an upgrade becomes unavailable, provide a clear replacement, preservation, or compensation policy for product-owner approval.

### 15.6 Acceptance checks

- A learner can understand the upgrade's cost and visible/functional effect before confirming.
- Earned points, spending, and upgrade ownership remain consistent after interruption and relaunch.
- Repeated requests cannot debit points twice.
- The world visibly reflects the acquired upgrade.
- Scenario variants become available according to authored rules and persist correctly.
- Existing scenarios remain accessible and replayable where intended.
- Upgrade content works with placeholder assets and later designer replacement.
- Upgrade paths do not gate essential accessibility or core learning access.

**Status:** Required product/system direction; detailed trees, costs, transaction model, launch locations, and variants remain open. No implementation is authorized.
