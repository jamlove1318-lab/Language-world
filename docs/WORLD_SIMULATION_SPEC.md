# Language-world — World Simulation Specification

**Status:** Working specification v0.1; not approved for implementation.  
**Purpose:** Define the living-world simulation contract for time, weather, seasons, residents, ecology, plants, creatures, events, and offline continuity.  
**Source boundary:** GoPAL-AI is a read-only research archive. This specification does not reuse its simulation runtime, code, assets, event bus, or pipeline.

---

## 1. The world should feel alive, not busy

A living world is not a screen filled with constantly moving actors. It is a place with believable rhythms, change, continuity, and quiet.

The world should:
- Have a recognizable identity and rhythm independent of the learner.
- Change in ways that are observable, understandable, and consistent.
- Support quiet periods and stillness; constant motion is not proof of life.
- Have residents, plants, creatures, weather, and events with their own rules and relationships.
- Preserve important changes when the learner leaves.
- Avoid pretending to simulate every detail of a real ecosystem or society.
- Use authored intent and bounded simulation rather than uncontrolled randomness.
- Remain playable on target Android devices without exhausting battery, memory, or thermal headroom.

Each language world must author its own climate, seasons, ecology, daily rhythms, architecture, cultural calendar, and environmental sound. A reusable simulation framework must not make all worlds behave alike.

## 2. Simulation domains and ownership

The world simulation coordinates domains but does not own every product system.

| Domain | Owns | Does not own |
|---|---|---|
| World clock | Canonical world-local date/time, day phase, elapsed simulation time | Device UI clock or account identity |
| Weather/climate | Authored climate rules, weather state and transitions | Real-time meteorological claims unless separately integrated |
| Season/calendar | Seasonal state, local calendar and authored festivals | Learner streaks or expiring access |
| Environment presentation | Lighting, sky, fog, wind, precipitation presentation, ambient cues | Persistent world facts |
| Residents | Schedules, commitments, activities, relationships and location intent | Cassidy canon or learner account |
| Creatures/ecology | Species, habitat, needs, rhythms, population and ecological events | Collectible/reward economy |
| Plants/gardens | Species, growth stage, needs, care history and habitat impact | Arbitrary daily engagement tasks |
| World events | Scheduled/triggered happenings and their durable outcomes | Quest rewards, learning scores, or travel state |
| Narrative | Story-specific flags, clues and authored consequences | The global simulation clock |
| Travel | Route, transport stage, departure and arrival handoff | Cinematic presentation timeline |
| Presentation runtime | Rendered actors, animation, audio, lighting and transient effects | Canonical persisted world state |

Each domain must have one authoritative owner and stable interfaces. Presentation systems consume snapshots and events; they do not silently mutate durable world truth.

## 3. Canonical world time

### 3.1 Requirements
- Every world has a canonical local date/time and a defined time-zone/calendar policy.
- Simulation must not depend directly on the device wall clock in every subsystem.
- Time progression is based on trusted elapsed time where available, with explicit offline and clock-change handling.
- The world clock must support day phases, local schedules, season boundaries, festival dates, and authored special dates.
- A world can use a different time zone from the learner's device.
- The user-facing experience should make the current world time understandable without requiring exact clock precision.
- The system must define behaviour for daylight-saving changes, leap days, time-zone rule updates, travel between world time zones, and device clock tampering.

### 3.2 Time models to evaluate
The product owner must choose a policy before implementation:
1. **Real local time:** each world follows the actual local time of its real-world geographic inspiration. This is intuitive but introduces timezone and daylight-saving complexity.
2. **Shared universe time:** all worlds share one fictional clock/calendar. This simplifies synchronization but may weaken place identity.
3. **Authored accelerated time:** world time advances at a defined ratio to real elapsed time. This supports authored day/night and season pacing but must be understandable and deterministic.

A hybrid may be considered, but must be explicit. Do not let different systems independently choose different clock models.

### 3.3 Offline progression
- Persist the last trusted simulation timestamp and world-clock state.
- On return, calculate elapsed time using a bounded catch-up policy.
- Do not simulate every frame or every resident action while offline.
- Use deterministic catch-up steps or summarized transitions for plants, residents, weather, and events.
- Define maximum offline simulation window and what happens beyond it.
- Prevent clock rollback/forward jumps from granting resources, skipping story beats, or breaking event order.
- If time cannot be trusted, pause time-sensitive progression and explain the limitation where needed.
- Offline catch-up must be idempotent: retrying the same elapsed interval cannot apply growth or events twice.

## 4. Day/night and atmosphere

Each world authors:
- Day-phase boundaries and transition durations.
- Sunrise/sunset logic appropriate to its geography or fictional calendar.
- Lighting, sky, cloud, fog, shadow, and interior-lighting changes.
- Ambient activity levels and resident/creature visibility by phase.
- World-specific audio layers and transition cues.
- Quiet-hour rules and any sensitive content restrictions.

Day phase is not merely a UI label. It affects how a place feels and what can be observed. However, it must not hard-lock essential content or make a story permanently unavailable at one time of day.

The simulation may use discrete states for logic and smooth presentation interpolation for lighting and sky. Presentation smoothing must not alter canonical event order.

## 5. Seasons, climate, and weather

### 5.1 World-authored climate profiles
Every world bible must specify:
- Climate zones and local variation.
- Season model and season duration.
- Typical temperature/precipitation/wind/fog patterns.
- Extreme weather boundaries and safety/content treatment.
- Seasonal plants, animal behaviour, clothing, architecture, and public life.
- Weather-specific ambience, audio, lighting, and visibility.
- Cultural and community events connected to seasons.

Do not assign the same four-season pattern to every world. Some geographies have wet/dry seasons, monsoon patterns, subtropical variation, or fictional climate systems. The calendar must reflect the authored world.

### 5.2 Weather simulation
Weather states should be authored and bounded, not arbitrary per-frame random values. Define:
- Current condition, intensity, temperature band, wind, precipitation, visibility, and transition state as needed.
- World/region-specific allowed conditions and seasonal probabilities.
- Forecast horizon and uncertainty model, if a forecast is shown.
- Deterministic seed/version so offline and synchronized clients can agree.
- Transition rules and minimum/maximum duration.
- Effects on ambience, visibility, movement, resident activities, plants, and creatures.
- Safe fallback for unsupported rendering or low-performance devices.

The product must not imply it is showing actual local weather unless a real weather service is integrated, disclosed, and appropriately licensed. Fictional world weather should be clearly understood as part of the world.

### 5.3 Weather must not be a blocker
- Core learning and story content should remain accessible across weather states.
- Weather can alter route feel, optional discoveries, sound, and activity, but must not punish the learner.
- Extreme conditions should be represented thoughtfully and not trivialize real disasters.
- Accessibility settings can reduce intense flashes, wind/rain audio, visual effects, and motion.

## 6. Residents and society

Residents are people with their own lives, not interactive vending machines.

### 6.1 Resident definition
Each resident specification should include:
- Stable character ID and canon reference.
- Home, workplace, community roles, affiliations, and meaningful relationships.
- Daily/weekly routines and schedule variants.
- Responsibilities, commitments, goals, and personal interests.
- Typical locations and route graph.
- Activity, social, rest, and privacy boundaries.
- Dialogue/voice/localization and cultural context.
- Reaction boundaries and conditions for interaction.
- Narrative arcs and changes over time.
- Accessibility/performance requirements for their presentation.

### 6.2 Routine model
Routines should be authored as flexible plans, not a single fixed hour-to-action switch. A routine can include:
- Time window and location intent.
- Activity and duration range.
- Dependencies, exceptions, and commitments.
- Weather/season adjustments.
- Community events and story overrides.
- Interruptibility and response to the learner.
- Recovery when the actor is unavailable or the world state changes.

Residents should not all face the learner, follow them, or become instantly available. Their attention is limited and context-sensitive. The learner can observe without interacting. A resident may decline, be busy, or not be present.

### 6.3 Continuity and autonomy
- Durable commitments and story-relevant changes must persist.
- Minor ambient movement can be simulated locally and discarded.
- Offline progression may summarize routine changes rather than replay every action.
- Avoid fabricated dialogue claiming that a resident performed an unobserved event.
- Do not use absence-based guilt or emotional pressure.
- Cassidy's separate canon, agency, memory, and autonomy are governed by the Cassidy Character Bible and must not be reduced to generic NPC scheduling.

## 7. Creatures and ecology

Creatures are part of the world's ecology and identity, not collectible skins or generic enemies.

Each species/creature definition must specify:
- Species ID, visual/animation identity, and world/region provenance.
- Habitat and ecological niche.
- Diet/resources, needs, activity cycle, and seasonal behaviour.
- Social structure, territorial behaviour, migration or movement range.
- Sensory cues: tracks, calls, silhouettes, movement, nests, burrows, and signs.
- Interaction distance, response, fear/curiosity/defence, and safety boundaries.
- Relationship to plants, climate, other species, residents, and the learner.
- Population bounds and habitat capacity.
- Conservation/cultural review where real-world inspiration is used.
- Performance representation: full actor, distant animation, audio cue, or abstract state.

The learner should be able to discover ecology through observation: tracks after rain, calls at dawn, migration, nesting, feeding, seasonal flowers, or a changed habitat. Not every creature should be approached, captured, fought, or rewarded.

The first release does not need a complex biological simulation. It needs a small number of authored, believable ecological relationships with deterministic and observable consequences.

## 8. Plants, gardens, and habitat care

Plants should grow according to world time, species, season, climate, and meaningful care—not a punitive daily login loop.

A plant definition should include:
- Species and world provenance.
- Growth stages and visual variants.
- Water/light/soil/temperature or fictional needs.
- Growth and dormancy rules.
- Seasonal behaviour and environmental effects.
- Care actions and their meaningful consequences.
- Recovery from neglect and limits on permanent loss.
- Propagation, harvest, or lifecycle rules where appropriate.
- Accessibility and low-frequency interaction options.

Garden/personal-space state must be learner-scoped and persist across sessions. Do not make a plant die simply because the learner was absent. If care is neglected, use reversible states such as slower growth, dormancy, or a gentle recovery opportunity. Avoid turning care into a streak obligation.

Habitat restoration should have visible and coherent effects on related plants, creatures, ambience, and future discoveries.

## 9. World events, festivals, and surprises

Events can be:
- Scheduled calendar events.
- Seasonal or weather-triggered events.
- Place-specific ambient moments.
- Resident/community events.
- Narrative-triggered events.
- Rare discoveries or surprises.
- Long-running world projects.

Every event definition should include:
- Stable ID and version.
- Trigger/eligibility conditions.
- World/place/time scope.
- Start, duration, end, and recurrence policy.
- Priority and conflict rules.
- Narrative, resident, environment, and world-state effects.
- Accessibility and content settings.
- Offline/re-entry behaviour.
- Whether it is missable and how a learner can recover it.
- Idempotency and event history requirements.

Rare moments should be authored and bounded. Do not rely on unbounded random chance for critical story content. Avoid FOMO, punitive expiration, or exclusive access to important narrative. A learner should be able to return to the story after an absence.

## 10. Environmental storytelling and continuity

The environment can communicate change without a notification:
- A repaired bridge remains repaired.
- A market stall changes with the season.
- A resident's workshop shows the result of a shared project.
- A plant grows or enters dormancy.
- A creature's tracks appear after rain.
- A festival leaves decorations or a community keepsake.
- A familiar place has a new sound, light, or object.

Each change must have a source event and a durable owner. Visual presentation is derived from world state, not the source of truth. The system must distinguish:
- Permanent canonical world facts.
- Learner-specific world changes.
- Temporary environmental conditions.
- Ephemeral presentation effects.
- Narrative-only facts and memories.

Avoid showing a world change to one learner that belongs to another account. Shared-world consequences, if ever introduced, need explicit rules for ownership, synchronization, moderation, and conflict resolution.

## 11. Simulation scale and performance tiers

The world does not need to simulate every actor at full fidelity at all times.

Define tiers:
- **Near/player focus:** full interaction, navigation, animation, audio, and relevant state updates.
- **Visible nearby:** simplified movement and presentation; no unnecessary decision loops.
- **Distant:** low-frequency or abstract presence, culling, and simplified animation.
- **Off-screen in loaded region:** bounded state updates only when relevant.
- **Offline/unloaded:** deterministic summarized catch-up for durable systems; no frame simulation.

Performance controls should consider actor count, animation complexity, update frequency, navigation, particle/weather effects, audio voices, memory, and thermal state. The simulation must degrade gracefully on lower-end Android hardware without changing canonical outcomes.

## 12. Save, event, and recovery requirements

- Stable IDs for all durable world events; do not use runtime-random IDs as the only deduplication identity.
- Every event has world/account scope, causal source, timestamp/clock version, content version, and idempotency key.
- Persist authoritative state transitions; presentation-only effects can be transient.
- Use an outbox or equivalent durable delivery boundary for cross-domain effects.
- Retries must not duplicate growth, resident commitments, rewards, discoveries, or event completion.
- Handle content version changes and migration of durable state.
- Define conflict policy for multi-device and offline edits.
- Provide deterministic recovery after app kill, device restart, travel interruption, and clock correction.
- Keep learner-private state isolated from other accounts.
- Log diagnostics without collecting unnecessary personal data.

## 13. Content authoring and validation

World authors need tools and contracts to define:
- World clock/calendar and timezone policy.
- Climate/season profiles and weather transitions.
- Day/night lighting and ambience.
- Resident schedules, route graphs, commitments, and exceptions.
- Creature species, habitat relationships, and ecological events.
- Plant lifecycle and care rules.
- Event calendars, triggers, and recovery paths.
- World-state consequences and presentation bindings.
- Localization, cultural review, audio, and accessibility.

Validation should detect:
- Invalid or conflicting schedules.
- Unreachable locations and invalid routes.
- Impossible event windows or missing return paths.
- Climate states unsupported by the world's authored profile.
- Missing assets or fallbacks.
- Unbounded offline growth or resource generation.
- Non-idempotent event transitions.
- Cross-account state references.
- Stories dependent on permanently missable events.
- Performance budgets exceeded by population or effects.

## 14. GoPAL-AI research findings

Selected source files reviewed:
- `src/engines/world/environmentEngine.ts`: season/time-of-day resolution and deterministic weather buckets derived from the current device date/hour.
- `src/engines/world/livingWorldClock.ts`: a lightweight clock using device local time and fixed day-phase boundaries.
- `src/engines/world/livingWorldSimulation.ts`: per-user AsyncStorage snapshot, but phase/weather/season are recomputed from current wall-clock time; elapsed minutes are primarily emitted as a location-shift event.
- `src/engines/world/worldSimulationSnapshot.ts`: simple snapshot with a default clear-weather state, basic activity and light flags.
- `src/engines/world/residentRoutineEngine.ts`: a small hour-based resident activity switch with short runtime transitions.
- `src/engines/world/contextualWorldEventEngine.ts`: lightweight ambient event candidates based on weather, routine, learner activity, and a seeded rare event.
- `src/engines/world/worldEventDirectorEngine.ts`: coordinates ambient events and opportunities while leaving festivals, quests, inventory, and rewards to other owners.
- `src/engines/world/npcCharacterRuntimeEngine.ts`: in-memory NPC expression/animation/outfit/presence snapshot and restore.
- `src/features/world/data/livingWorldSimulation.ts`: local actor/vehicle simulation, seeded spawn positions, movement/navigation and schedule/behavior hooks.
- `src/engines/world/livingWorldRuntime.ts`: bridges per-user persisted world state with simulation and visit continuity.

### Recovered strengths
- Time, weather, season, ambience, and world events are recognized as part of the experience.
- Some weather selection is deterministic rather than random on every render.
- Residents have routine/activity concepts.
- Ambient events are separated from some higher-level product systems.
- The larger 2D runtime includes actor movement, routes, navigation, and spawn points.
- Return visits and continuity are treated as product concerns.

### Limitations and cautions
- Several clocks and simulation snapshots use device local wall time directly.
- Weather and season logic are lightweight deterministic buckets, not a complete authored climate model.
- The inspected world snapshot defaults to clear weather and simple ambient values.
- Resident routine logic is highly simplified and does not establish a durable society or long-term commitments.
- NPC presentation state is in-memory; it is not a full persistent character life model.
- The inspected source does not establish a complete creature/ecology simulation or species/habitat system.
- The inspected source does not establish a robust plant lifecycle, care, and habitat model.
- Offline elapsed time, device clock changes, daylight-saving/time-zone behaviour, event recovery, and cross-device determinism are not fully proven.

These are selected-source observations. They do not prove all world systems are absent; they define what remains to be verified and specified for the new product.

## 15. Open decisions

- Time model: real local time, shared universe time, authored accelerated time, or a hybrid.
- World time-zone and daylight-saving policy.
- Season/calendar model for each launch world.
- Whether weather is entirely fictional or has any real-world data integration.
- Offline catch-up limits and behaviour when time cannot be trusted.
- Which residents, creatures, plants, and ecological relationships exist at launch.
- Whether any world state is shared between learners.
- Performance tiers and target Android device class.
- How festivals and narrative events remain available after absence.
- Cultural/ecological review standards for real-world-inspired species and practices.

---

**Current status:** The simulation domains, clock policy options, climate/weather, residents, ecology, plants, events, environmental storytelling, performance tiers, persistence, and validation requirements are documented as a working specification. World-specific authored profiles and key time/offline decisions remain open. No implementation is authorized.
