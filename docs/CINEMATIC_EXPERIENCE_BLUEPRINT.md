# Cinematic Experience Blueprint

**Status:** Product and runtime specification; engine-neutral  
**Scope:** First-launch welcome, world orientation, resident reveals, secret adventures, and inter-world transport.

## 1. The cinematic language of this universe

Cinematics are not decoration between menus. They are a way the universe communicates emotion, scale, personality, history, and change.

Use directed sequences when they create something that ordinary free movement cannot:
- A first impression that deserves deliberate staging.
- A reveal that benefits from anticipation and controlled information.
- A journey whose departure, movement, and arrival matter.
- A personal story moment where expressions, silence, sound, and camera carry meaning.
- A major world event that changes how a place feels.

Do not turn every door, conversation, or short walk into a cutscene. Keep everyday life interactive. Cinematic direction should enhance agency, not take it away.

## 2. First-launch experience: Cassidy welcomes the learner

### Purpose

Make the learner feel personally welcomed into a place—not presented with a tutorial checklist. Establish Cassidy as a human character with warmth and personality, establish Emerald Valley as home, and communicate that the universe extends far beyond it.

### Sequence outline

**Beat A — Arrival**
- Begin with a short atmospheric view of Emerald Valley.
- Establish sound, weather, light, and a sense of place before overwhelming the learner with information.
- Cassidy is present in the scene, doing something natural. Avoid a static character standing in front of a title card.
- Camera finds her through the environment rather than a sudden UI pop-up.

**Beat B — Introduction**
- Cassidy notices the learner and approaches or turns toward them.
- She introduces herself in her own voice and personality.
- The learner can choose a response or simply continue; no forced account/profile questions inside the scene.
- Her expressions, gaze, gestures, timing, and pauses should support the dialogue.
- Captions/subtitles are available from the beginning.

**Beat C — “This is home”**
- Cassidy leads the learner to a vantage point or meaningful home-world landmark.
- The camera reveals the valley and its distinct landmarks in a controlled sequence.
- Cassidy explains that Emerald Valley is their home world: a place to return to, discover, and see change over time.
- Do not imply Emerald Valley is the only world or that the learner must complete it before seeing the wider universe.

**Beat D — What can happen here**
- Cassidy demonstrates a small number of concrete possibilities through visible examples: explore a path, inspect an object, enter a place, discover a story clue, visit an activity, meet someone, or simply wander.
- The sequence should show rather than list. Each example is brief and can be explored immediately or saved for later.
- Explain that Cassidy sometimes has her own plans and discoveries; she is not a permanently attached guide who narrates every action.

**Beat E — The wider universe**
- Introduce the world-travel concept through a visible landmark such as a travel hub, station, map room, or departure platform.
- Reveal glimpses of distinct destinations. Avoid presenting every world as a row of identical selectable tiles.
- Explain that different worlds have their own places, people, cultures, stories, and ways to learn.
- The first-launch sequence may tease travel without forcing the learner to depart immediately.

**Beat F — Return control**
- Cassidy invites the learner to choose what to do next.
- Return full movement and interaction control.
- The learner can explore, ask Cassidy something, follow a nearby opportunity, or leave the introduction.
- Store the sequence completion and any chosen optional discoveries in durable state.

### First-launch safeguards

- Provide skip, pause, captions, dialogue replay, and reduced-motion alternatives.
- Skipping must not skip essential onboarding state. Show concise accessible follow-up prompts in the world.
- If interrupted, resume at a safe checkpoint or restart the current beat without duplicating rewards/events.
- Do not make the learner repeat the entire introduction on every app launch.
- Make the introduction replayable from a journal/help location.
- Keep the learner's first meaningful choice genuine and low-pressure.

## 3. Inter-world travel: Emerald Valley to the Spanish world by train

A train journey is an authored travel experience with real origin/destination state. It should feel like leaving one world and arriving in another, not an animated loading screen.

### Journey phases

1. **Invitation and intent:** learner chooses to travel or accepts an invitation. Cassidy can explain the destination and what is known, without forcing the choice.
2. **Preparation:** optional station exploration, ticket/check-in interaction, luggage or keepsake preparation, and a chance to postpone.
3. **Station arrival:** establish the station's architecture, signage, local language context, crowd ambience, platform, and departure board.
4. **Boarding:** show train arrival or waiting train, doors, boarding gesture, and transition into the carriage.
5. **Departure:** camera returns to the platform or window as the train begins moving. Emerald Valley recedes in a visually memorable way.
6. **Journey:** moving scenery, soundscape, carriage details, changing light, optional conversation, observation, listening activity, or quiet time. Do not require constant tasks.
7. **Approach:** destination cues gradually appear—landscape, architecture, signs, climate, and sound.
8. **Arrival:** station announcement, braking/doors, platform reveal, and a clear contrast with the home world.
9. **Disembarkation:** learner exits the train and gains control in the new world.
10. **Continuity:** Spanish-world state is activated while Emerald Valley remains preserved at its previous state.

### Travel is a domain transaction

The travel domain owns:
- Journey ID and version.
- Origin world/location and destination world/location.
- Transport mode and route.
- Preparation/boarding/departure/in-transit/arrival/completed/cancelled state.
- Durable timestamps and recovery checkpoint.
- Any learner choices or meaningful discoveries made during travel.

The cinematic director reads this state and presents the corresponding beat. It cannot silently change the destination or mark travel complete merely because a timeline reached its end.

If the learner skips, backgrounds the app, loses power, or the sequence fails:
- Resume at a safe checkpoint, or
- Offer a safe completion/return decision according to the current travel state.
- Never strand the learner in a half-loaded world.
- Never duplicate travel rewards or arrival events.

## 4. Other cinematic families

### Resident introductions
- Establish presence through a sound, silhouette, activity, environmental trace, or another character's reaction.
- Let anticipation build before a direct reveal.
- Give each resident a distinct entrance and behavioural signature.
- The reveal should arise from their personality and situation, not a generic camera zoom.
- Allow the learner to approach or wait when the scene permits.

### Cassidy's secret adventures
- Cassidy may notice something unusual, remember a clue, receive a message, or decide to investigate.
- She can invite the learner, but the learner can decline or discover the place independently later.
- The secret location should have a real world-space entrance, authored environment, meaningful interactions, and consequences.
- Some adventures can happen without residents; some may include Cassidy; others can be discovered by the learner alone.
- Cassidy must not become a universal key that gates all content.

### Story and world-event moments
- Use environmental storytelling before exposition.
- Give characters room for silence, reaction, and conflicting motives.
- Tie choices and outcomes to durable narrative/world state.
- Make important story information recoverable in a journal, archive, object, letter, or conversation.
- Avoid presenting every mystery as a dialogue tree.

## 5. Cinematic authoring roles

Separate responsibilities so a designer, animator, writer, sound designer, and engineer can work without editing one monolithic script.

- **Sequence director:** beat order, timing, branch points, checkpoints, skip/replay.
- **Camera track:** shots, targets, transitions, framing, safe areas.
- **Actor performance track:** actor references, animation state, gestures, gaze, expressions, movement.
- **Dialogue track:** localized lines, voice assets, captions, speaker, timing, optional learner responses.
- **Audio track:** ambience, music, sound effects, mix automation, ducking, spatial cues.
- **Environment track:** lighting, weather presentation, particles, moving set elements.
- **Travel track:** vehicle and route choreography, but only as a presentation of domain travel state.
- **Interaction track:** windows when the learner can move, choose, inspect, or interrupt.

Each track uses stable IDs and references versioned content assets. Timeline time is not a substitute for domain state.

## 6. Production workflow for a cinematic

1. Write the emotional purpose and learner takeaway in plain language.
2. Create a beat sheet with duration ranges and learner-agency moments.
3. Greybox camera, character positions, movement paths, and environmental reveal.
4. Use proxy character/environment/vehicle assets and temporary audio.
5. Test timing and comprehension with captions before final voice recording.
6. Validate skip, pause, replay, reduced motion, background/resume, and process-death recovery.
7. Replace proxies with designer assets using stable asset/rig/animation IDs.
8. Review performance and visual readability on target Android devices.
9. Localize dialogue, captions, signage, and audio.
10. Lock a versioned sequence package with rollback.

## 7. First cinematic vertical slice

The first implementation should be intentionally small:
- A 20–40 second welcome scene with Cassidy proxy, environmental establishing shot, greeting, captions, and learner-controlled continuation.
- A compact Emerald Valley reveal with two or three landmarks.
- A travel hub glimpse that communicates there are other worlds.
- A 30–60 second train journey prototype with station, boarding, moving-window shot, arrival, and destination handoff.
- A simple resident reveal beat using a silhouette or environmental clue.
- A short optional Cassidy-led secret discovery beat.

Only the welcome and one travel sequence need to be wired into the first vertical slice. The resident and secret-adventure beats can remain greyboxed storyboards until the core director proves itself.

## 8. Success criteria

A learner can understand who Cassidy is, why Emerald Valley is home, and that the universe is larger than one location. The welcome feels personal rather than like a tutorial video. The train journey has a clear beginning, middle, and arrival. The learner can skip or interrupt without losing state. The same cinematic structure works with proxy and production assets. The designer can improve the visual quality without rewriting sequence logic.


## 9. Runtime contract and sequence lifecycle

The sequence is authored data interpreted by a cinematic director. It is not a component containing all dialogue, animation, timing, and persistence logic.

A sequence package must declare:
- Stable sequence ID, content version, supported schema version, purpose, audience/context, prerequisites, and completion policy.
- Required scene/place/actor/asset dependencies and preload groups.
- A beat graph with ordered beats, optional branches, choice windows, skip targets, and checkpoint IDs.
- Track references for camera, actor performance, dialogue/captions, audio, environment, transport presentation, and learner interaction.
- Expected domain state before start and the domain events that may be requested at named checkpoints.
- Replay policy, first-visit/return-visit variant, localization, accessibility, and fallback presentation.
- Estimated duration range, not just a single hard-coded runtime.

### Beat and track rules

- Tracks use a shared sequence timebase and stable beat/event IDs.
- Tracks may overlap, but conflicts must be resolved by explicit priority and ownership.
- Dialogue and captions share timing metadata; localization changes must not silently desynchronize captions.
- Actor performance expresses semantic intent (walk, greet, listen, look-at, gesture, expression) and maps to the current asset's animation capabilities.
- Camera tracks declare target, framing, transition, motion intensity, and safe composition bounds.
- Audio cues use semantic IDs from the Audio, Voice, and Soundscape Specification.
- Environment tracks request presentation changes; canonical weather/time/world state remains owned by world simulation.
- Transport tracks visualize travel state; they do not create or complete journeys.
- Learner interaction windows are explicit. A sequence must never imply that the learner has control when input is being ignored.

### Lifecycle

1. **Resolve:** validate prerequisites, content version, localization, accessibility preferences, and required assets.
2. **Preload:** load essential scene, actor, voice, caption, and transition assets; optional assets may be omitted with declared fallbacks.
3. **Prepare:** obtain a durable start/checkpoint record from the owning domain.
4. **Present:** run authored tracks and emit presentation events.
5. **Checkpoint:** request domain-owned commits only at named, validated checkpoints.
6. **Complete/skip:** settle the sequence outcome and return control or hand off to the next experience.
7. **Release:** dispose transient players, camera overrides, actors, and scene resources.
8. **Recover:** reconcile persisted sequence/domain state after pause, process death, asset failure, or version change.

A presentation event is not proof of a domain transaction. For example, a train-door animation reaching its final frame does not prove that the learner boarded; the travel domain must commit boarding and the sequence must reconcile with that result.

## 10. Interruption, failure, and migration matrix

Every sequence must define behaviour for:
- App backgrounding and foreground return.
- Process termination at each durable checkpoint.
- Missing or corrupt asset, voice line, or localization.
- Audio focus loss and device route changes.
- Learner skip, pause, replay, or exit.
- Reduced-motion preference changed before or during playback.
- Content update while a sequence is in progress.
- Destination/domain state committed but presentation not yet played.
- Presentation completed but domain commit failed.

Recovery must prefer a coherent world state over replaying a broken timeline. A sequence can resume, restart its current beat, switch to a simplified presentation, or conclude with a recap. It must not duplicate rewards, travel, story outcomes, or onboarding completion.

Sequence versions need migration rules. If a new version removes a beat that an existing learner checkpoint references, provide a stable migration target or safe completion path.

## 11. Cinematic quality and approval gates

Before a sequence is approved:
- Its emotional purpose and learner takeaway are clear.
- Story, character, and world canon are respected.
- The sequence works with proxy assets and final assets.
- Camera and actor staging communicate the action without relying on spoken explanation.
- Dialogue, captions, localization, and voice timing have been reviewed.
- Audio can be muted or reduced without losing essential information.
- Skip, pause, replay, reduced motion, interruption, and recovery are tested.
- Domain state transitions are owned by the correct systems and are idempotent.
- No learner is trapped in a forced wait or repeated unskippable content.
- Performance and memory budgets are measured on target Android devices.

Related audio, travel, and asset requirements are specified in [Audio, Voice, and Soundscape](AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md), [Travel Experience](TRAVEL_EXPERIENCE_SPEC.md), and [Asset and Cinematic Pipeline](ASSET_AND_CINEMATIC_PIPELINE.md).

**Status note:** This document defines the cinematic experience and production direction. The exact engine/runtime implementation remains open. It complements, rather than replaces, the durable travel and world-state contracts.
