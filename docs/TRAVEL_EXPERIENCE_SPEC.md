# Language-world — Travel Experience Specification

**Status:** Working specification v0.1; not approved for implementation.  
**Purpose:** Define travel as a persistent, authored experience connecting places and language worlds—not merely movement or a loading transition.  
**Related specifications:** [Cinematic Experience Blueprint](CINEMATIC_EXPERIENCE_BLUEPRINT.md), [Asset and Cinematic Pipeline](ASSET_AND_CINEMATIC_PIPELINE.md), [World Objects and Spaces](WORLD_OBJECTS_AND_SPACES.md), [World Simulation Specification](WORLD_SIMULATION_SPEC.md).  
**Source boundary:** GoPAL-AI is a read-only research archive. Its transport definitions and movement code are evidence only, not dependencies.

---

## 1. Travel is part of the world

Travel should express geography, distance, culture, anticipation, and the character of the destination. The learner should feel that they are leaving one place and arriving somewhere else—not that a world selector has opened another scene.

A journey may contain:
- Choosing or discovering a destination.
- Learning why the destination matters and what is known about it.
- Preparing for departure.
- Reaching a station, airport, harbour, bus stop, or other departure place.
- Finding the correct platform, gate, dock, or vehicle.
- Boarding and settling in.
- Departure and a distinct transition out of the origin world.
- A journey sequence with environmental storytelling and optional activities.
- Approaching and revealing the destination.
- Arrival, disembarkation, and orientation.
- A handoff into free exploration or a specific story/experience.

Not every trip needs every beat. The journey director selects a suitable authored route and transport mode while preserving the same durable travel-state contract.

## 2. The first inter-world journey

The first authored example in the product vision is a train journey from Emerald Valley to the Spanish world.

It should include:
1. A reason to travel and a destination introduction.
2. Discovery of the Valley Station and the departure context.
3. A station arrival scene with platform, signage, announcements, staff, travellers, and local atmosphere.
4. Ticket/boarding interaction appropriate to the story and learner's language level.
5. Train arrival, boarding, doors closing, and departure.
6. A view of Emerald Valley receding and a clear sense of leaving home.
7. A journey through changing landscapes, with authored sound, lighting, camera, and optional observations.
8. A contextual transition that does not imply a magical teleport unless that is the world's canon.
9. The first reveal of the Spanish world's distinct geography, architecture, light, sound, and social atmosphere.
10. Arrival at the destination station, disembarkation, and a welcoming orientation.
11. A playable handoff into the new world, preserving the arrival location and current travel state.

The train journey is a product-defining cinematic, not a generic transition template with different background art. Later journeys can use planes, boats, or other transport where distance and geography justify them.

## 3. Transport modes and selection

Transport mode is determined by geography, infrastructure, world canon, journey distance, and narrative intent.

### Rail
Suitable for connected regions and inter-world routes where a railway network exists. Supports stations, platforms, timetables, announcements, boarding, carriage interiors, windows, stops, tunnels, bridges, changing landscapes, and arrival.

### Air
Suitable for long distances, islands, or world connections without a plausible continuous land/rail route. Supports airport/terminal arrival, check-in or boarding context, gate, aircraft boarding, takeoff, flight, descent, landing, and destination arrival. Do not trivialize aviation safety procedures or require complex simulation for a short authored scene.

### Road: car, bus, coach
Suitable for local and regional journeys with connected roads. Supports stops, traffic, landscapes, passengers, local conversations, route landmarks, and arrival. Road journeys may include optional stops or observations.

### Water: boat, ferry, ship
Suitable for coastlines, islands, rivers, harbours, and maritime worlds. Supports docks, boarding, departure, sea/river atmosphere, weather, wildlife, and arrival.

### Other authored transport
Fantasy, science-fiction, or culturally specific transport can exist where the world bible justifies it. It must follow the same travel-state, safety, accessibility, and interruption contracts.

Do not choose a mode only because the old asset catalogue has a train or plane model. The route and world must justify it.

## 4. Route graph and destination model

Travel is based on a canonical route graph, not hard-coded screen transitions.

A route definition includes:
- Stable route ID and content version.
- Origin and destination world/place/space IDs.
- Ordered route segments and meaningful stops.
- Transport mode and compatible vehicle/service.
- Departure and arrival anchors.
- Infrastructure dependencies and access conditions.
- Journey duration band and presentation pacing.
- Geography/landscape sequence and world boundary transition.
- Available experiences or observations along the way.
- Accessibility alternatives.
- Unlock/availability rules and narrative prerequisites.
- Fallback route or recovery policy.

A route can be multi-modal (for example, walk to station → train → local bus). Each segment has its own boarding, movement, and arrival semantics. Transfers must be authored and connected; do not silently skip a required change of vehicle.

A destination record must declare:
- Canonical world and place IDs.
- Arrival space and spawn/entry anchor.
- First-visit reveal variant and return-visit variant.
- Orientation information and nearby points of interest.
- Destination-specific ambience, weather continuity, and local time policy.
- Optional introduction, resident reveal, or story handoff.
- What state is committed before the learner gains control.

## 5. Durable travel state machine

Travel has a persistent domain state, separate from cinematic presentation.

Suggested domain states:
- `planned`
- `preparing`
- `at_departure`
- `boarding`
- `departed`
- `in_transit`
- `at_transfer`
- `arriving`
- `disembarking`
- `arrived`
- `cancelled`
- `interrupted`
- `recovery_required`

Transitions are validated against the route and current state. Not every route uses every state. State changes have stable IDs, timestamps from the canonical clock, route/segment IDs, and idempotency keys.

The travel domain owns:
- Current journey and route.
- Origin, destination, and segment.
- Transport/vehicle assignment.
- Boarding/departure/arrival status.
- Current travel checkpoint.
- Whether the destination handoff has been committed.
- Recovery path after interruption.

The cinematic director owns only presentation playback: shot timeline, camera, actor blocking, animation, audio, subtitles, and transition cues. It cannot declare a journey arrived merely because a timeline elapsed.

## 6. Cinematic staging

Each route segment can author a sequence using the [Cinematic Experience Blueprint](CINEMATIC_EXPERIENCE_BLUEPRINT.md) and [Asset and Cinematic Pipeline](ASSET_AND_CINEMATIC_PIPELINE.md).

A travel sequence may include:
- Establishing shot of the departure place.
- Character/learner arrival and staging.
- Environmental and transport details.
- Boarding choreography and door/vehicle interactions.
- Departure movement and camera transition.
- Exterior travel shots and landscape progression.
- Interior moments, conversations, observations, or quiet time.
- Transition across a world/region boundary.
- Destination approach and reveal.
- Arrival choreography and handoff.

The cinematic timeline should support authored beats, optional dialogue, sound/music/ambience, camera cuts and blends, character locomotion/gestures, weather continuity, preload cues, and scene handoff.

The sequence must be authored with the destination in mind. A train ride through mountains, a plane descent toward a coastal city, and a bus ride through a neighbourhood should not share identical pacing or imagery.

## 7. Optional journey activities

Travel can include optional experiences:
- Look through the window and notice a landmark or ecological detail.
- Hear an announcement and understand the destination/platform.
- Read a ticket, sign, route map, or message.
- Talk with a fellow traveller where contextually appropriate.
- Listen to music, a story, or a short local audio scene.
- Notice changing geography, weather, architecture, or language.
- Reflect on what the learner expects to discover.

These activities must never make the journey mandatory study. A learner may simply enjoy the ride. Core arrival must not depend on completing an optional language task. If the learner ignores or skips an activity, the route continues.

## 8. Cassidy and companions during travel

Cassidy may accompany the learner, share context, notice something, tell a story, or remain quiet. Her participation must fit her own character and the situation. She is not required to explain every landmark or fill every silence.

- She may have her own reason for travelling.
- She can express anticipation or curiosity without manufacturing emotional dependence.
- She must not guilt the learner for skipping dialogue or returning later.
- If Cassidy is not present, the journey must still be complete.
- Other companions/residents can travel only when the story and route justify it.
- Character staging must preserve identity, continuity, and physical plausibility.

## 9. Arrival and world handoff

Arrival is not complete when a background image changes.

The travel domain must:
1. Validate that the current segment is ready to arrive.
2. Commit destination world/place/space and arrival anchor.
3. Commit the journey state as arrived.
4. Apply required durable travel consequences exactly once.
5. Load destination environment and world simulation context.
6. Preserve destination local time/weather policy and continuity.
7. Play or resume the arrival cinematic if appropriate.
8. Hand control to exploration, resident encounter, or the authored next experience.
9. Record the journey in the learner's history/archive if the product policy allows it.

The handoff must be restart-safe. If the app closes after arrival is committed but before the cinematic plays, the learner should resume at a coherent arrival point. If the cinematic completes but the domain state has not committed, the system must reconcile without duplicating the journey.

## 10. Skip, replay, interruption, and accessibility

- Every travel cinematic needs a clear skip/shorten policy.
- Skipping must not skip required domain state transitions.
- Replay should be available where narrative and storage policy allow it.
- Pause/backgrounding, calls, audio focus loss, app termination, and device restart must be handled.
- Resume from a checkpoint or safely restart the presentation while preserving the committed travel state.
- Reduced-motion mode uses calmer camera movement, fewer cuts, and stable framing.
- Provide subtitles/captions, speaker labels, adjustable audio, and optional transcript.
- Essential destination information must be available outside the cinematic.
- A journey should not trap the learner in an unskippable sequence.
- Avoid long forced waits. Duration should serve the story and be adjustable for repeat visits.

## 11. Travel, world time, and weather

Travel connects worlds that may have different time zones, climates, calendars, and weather. The system must define:
- Whether travel duration advances canonical world time.
- How time zones are handled at departure and arrival.
- Whether weather continuity applies to the journey segment or only origin/destination.
- How day/night transitions are shown during long trips.
- Whether offline travel can progress and under what conditions.
- How clock correction or time uncertainty affects scheduled departures and arrivals.

These rules depend on the final world-clock policy in the [World Simulation Specification](WORLD_SIMULATION_SPEC.md). Do not implement independent travel-time logic that conflicts with the canonical world clock.

## 12. Reliability, privacy, and analytics

- Stable route, journey, segment, and event IDs.
- Idempotent boarding, departure, arrival, and handoff transitions.
- Durable checkpoints and recovery after interruption.
- No duplicate rewards, story consequences, or journey records on retry.
- Explicit learner/account scope for private journey history.
- Avoid collecting precise real-world location; fictional travel does not need it.
- Analytics should measure reliability and experience quality without collecting unnecessary personal conversation/audio.
- Define route content migration when world/place IDs or segments change.
- Keep travel availability separate from streaks or daily engagement systems.

## 13. GoPAL-AI research findings

Selected source files reviewed:
- `src/features/world/data/livingWorldTransport.ts`: railway/airport networks with track/platform/runway/taxiway/apron geometry and optional route points.
- `src/features/world/data/livingWorldVehicles.ts`: train, bus, car, bicycle, boat, and airplane definitions, route waypoints, speeds, and looping local vehicle paths.
- `src/engines/world/destinationArrivalSceneEngine.ts`: destination arrival scene templates with establishing, wide, weather, life, and resident-reveal shots.
- `src/engines/world/destinationArrivalTimelineEngine.ts`: a fixed-duration arrival timeline and encounter handoff.
- `src/engines/world/destinationExperienceEngine.ts` and `worldDestinationExperienceEngine.ts`: destination atmosphere, visible places, discoveries, and learning moments.

### Recovered strengths
- Multiple transport modes and route/infrastructure concepts exist.
- Vehicles can follow authored waypoints and connect to transport networks.
- Arrival is recognized as a cinematic moment with environmental continuity and resident reveal.
- Destination identity and local discovery can inform the arrival experience.

### Limitations and cautions
- Inspected vehicle routes are mostly looping local movement, not a persistent inter-world journey.
- Transport networks describe visual geometry and route points, not a complete booking/boarding/departure/arrival domain.
- The arrival timeline is a fixed short sequence; it is not a complete cinematic authoring or travel recovery system.
- The inspected sources do not establish a durable journey state machine, transfers, interruption-safe handoff, or cross-world route graph.
- A moving vehicle actor is not equivalent to a learner-controlled travel experience.
- The current first Spanish-world train journey remains a product requirement to author, not a completed old implementation.

These are selected-source findings, not proof that no other travel code exists elsewhere in the repository.

## 14. Open decisions

- First inter-world route and destination world content.
- Which routes use train, plane, boat, bus, or other transport.
- Whether journeys are fully playable, cinematic-only, or a mix by route.
- First-visit versus repeat-visit travel length and replay policy.
- Whether travel time advances the canonical world clock and how time zones work.
- Offline travel and interruption/recovery behaviour.
- Which optional language activities, if any, are included during travel.
- How much route geography is represented physically versus cinematically.
- First-release travel asset and animation scope.

---

**Current status:** Travel experience taxonomy, route graph, durable travel state machine, cinematic staging, optional journey activities, Cassidy boundaries, arrival handoff, accessibility, reliability, and open decisions documented as a working specification. The first Spanish-world route remains to be authored and approved. No implementation is authorized.
