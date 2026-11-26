# Language-world — Audio, Voice, and Soundscape Specification

**Status:** Working specification v0.1; not approved for implementation.  
**Purpose:** Define the sound identity and runtime behaviour of the universe across exploration, characters, stories, learning, travel, cinematics, and accessibility.  
**Related specifications:** [Cinematic Experience Blueprint](CINEMATIC_EXPERIENCE_BLUEPRINT.md), [Asset Handoff Standard](ASSET_HANDOFF_STANDARD.md), [World Simulation Specification](WORLD_SIMULATION_SPEC.md), [Travel Experience Specification](TRAVEL_EXPERIENCE_SPEC.md).  
**Source boundary:** GoPAL-AI is a read-only research archive. Its sound categories and mix concepts are research evidence only; its playback runtime and Expo dependencies are excluded.

---

## 1. Audio is part of world identity

Audio should make a place recognisable with eyes closed. It carries geography, material, scale, weather, time, culture, social activity, emotion, and narrative information.

The audio identity of a world is not one looping music track. It is a layered, changing soundscape:
- Natural ambience: wind, water, leaves, insects, birds, distant wildlife, weather.
- Place ambience: room tone, market activity, station atmosphere, workshop sounds, café life.
- Movement: footsteps, fabric, doors, vehicles, wheels, surfaces, water movement.
- Interaction: object feedback, mechanisms, discoveries, tools, transitions.
- Character: voice, breath where appropriate, movement, vocal reactions, creature calls.
- Music: authored themes, adaptive layers, silence, and transition cues.
- Story/event: distinctive audio motifs and authored moments.
- Learning: speech examples, listening scenes, pronunciation playback, and optional voice capture.

Audio must support the scene rather than constantly demand attention. Silence and low-density sound are valid authored states.

## 2. World-specific sound bibles

Every world must have an authored sound identity. It must not inherit a generic sound pack with a few local instruments layered on top.

A world sound bible records:
- Acoustic identity and emotional vocabulary.
- Climate, terrain, vegetation, water, wildlife, and natural ambience.
- Architectural materials and characteristic interior reverberation.
- Settlement density, public spaces, transport and social sound.
- Day/night, weather, season and festival variations.
- Musical language, instrumentation references, tempo and density ranges.
- Signature motifs and sounds that should be rare.
- Quiet zones and locations where music is absent or minimal.
- Cultural review and provenance for instruments, performances, language, and sound references.
- Mix priorities and accessibility alternatives.

Each major location may have a location sound profile, but location profiles must inherit from the world bible and specify intentional exceptions.

## 3. Audio cue contract

Every cue has a stable semantic ID independent of filename or playback engine.

A cue definition should include:
- Cue ID and content version.
- Category and semantic purpose.
- World/location/activity/story scope.
- Asset binding and supported format/codec.
- Duration, loop points, tail, and fade behaviour.
- Loudness target and peak/true-peak constraints.
- Spatial or non-spatial presentation.
- Position/attachment anchor if spatial.
- Priority, concurrency group, cooldown, and maximum simultaneous instances.
- Weather/time/season/event conditions where relevant.
- Ducking and side-chain relationships.
- Fallback cue or silent fallback.
- Accessibility meaning and caption/transcript if informative.
- Licence, source, creator, performer, and usage rights.

Gameplay and content refer to cue IDs, not filenames, audio middleware object IDs, or platform-specific paths.

## 4. Runtime mix architecture

Separate authored sound decisions from the playback adapter.

**Audio Director** resolves which cues should be active based on world state, place, time, weather, activity, cinematic tracks, user preferences, and current interruptions.

**Mix Director** combines categories, applies priorities, ducking, fades, concurrency limits, and user volume preferences.

**Playback Adapter** owns platform-specific players, decoding, streaming, spatialization, and resource disposal. It must be replaceable when the engine is selected.

Suggested mix buses:
- Master.
- Music.
- Natural ambience.
- Location/architecture.
- Movement/vehicles.
- Interaction/SFX.
- Character voice/dialogue.
- Creature/wildlife.
- Cinematic score and authored moments (may share music bus but needs track-level priority).
- Learning/media playback.

The exact bus graph and number of simultaneous voices are engine/device decisions, not fixed assumptions at blueprint stage.

The mix must avoid clipping and preserve dialogue intelligibility. Category defaults are starting points only; actual levels require listening tests on speakers, headphones, and low-volume mobile playback.

## 5. Adaptive soundscape rules

Audio changes with context, but must not behave unpredictably.

- Entering a place transitions its sound profile with controlled crossfades.
- Weather changes affect appropriate environmental layers without abrupt restarts.
- Day/night and season may alter wildlife, activity, and ambience.
- Movement affects footsteps, surface sounds, and nearby vehicle cues.
- Distant sources are attenuated and culled.
- Important story cues may take priority but cannot overwhelm voice or safety information.
- Repeated one-shot cues use cooldowns and concurrency limits.
- Music may adapt by adding/removing layers rather than restarting a full track.
- Quiet places can reduce music or remove it entirely.
- Rare signature sounds are protected from overuse.
- Soundscape changes must be deterministic enough to support reproducible story scenes and testing.

## 6. Music and original composition

Music is authored to support a place, character, story, or activity—not to fill every second.

Requirements:
- Establish a coherent musical identity per world and major character/story arc.
- Use original compositions or properly licensed music with documented rights.
- Define loop points, stems/layers, transition points, tempo ranges, and intensity.
- Avoid using culturally significant instruments or styles as superficial decoration; consult knowledgeable reviewers.
- Support music-off and low-stimulation settings without breaking narrative comprehension.
- Do not imitate identifiable copyrighted melodies, recordings, or living artists' signature styles.
- Keep music assets and stems versioned with source projects and mix notes.

## 7. Voice, dialogue, and character performance

Voice is part of character identity and language learning, and requires deliberate production.

Each voice package should define:
- Character/speaker ID and approved voice identity.
- Language, locale, accent/dialect, register, and pronunciation guidance.
- Age-appropriate performance direction without relying on stereotypes.
- Emotional/performance range and boundaries.
- Dialogue asset IDs and script version.
- Recording session metadata, performer rights, permitted use, and retention.
- Clean, edited, mastered and runtime versions.
- Caption/transcript alignment and localization status.
- Pronunciation notes and approved variants.

Cassidy's voice should remain recognisable across scenes and localizations. Her language ability, accent, vocabulary, and code-switching must follow character and world canon. Voice acting must not imply she has capabilities or memories that the written story does not support.

Residents should have distinct, respectful voices grounded in their character and context. Avoid caricatured accents and exaggerated pronunciation for comedy.

## 8. Language-learning audio integrity

The product must distinguish what audio features actually do.

- **Playback:** learner hears an authored or generated reference.
- **Shadowing:** learner repeats after or alongside a reference; completion alone is not proof of accuracy.
- **Microphone capture:** audio is recorded or processed from the learner.
- **Speech recognition:** a model returns a transcription or recognition result; it may be wrong.
- **Pronunciation assessment:** a validated method evaluates specified pronunciation features with known limitations.
- **Conversation:** learner and character exchange meaning; evaluation must distinguish semantic success from pronunciation and fluency.

Never claim that a learner's pronunciation is correct merely because audio played, a microphone opened, a recording was saved, or a transcription exists. Assessment must disclose uncertainty and avoid false precision.

Voice capture must be explicit, purpose-limited, visible while active, and stoppable. Do not record in the background or treat ambient microphone access as world ambience. The privacy policy must specify processing location, retention, deletion, vendor access, and whether audio is used for model training.

Learning audio should support replay, slower playback where appropriate, transcript/captions, speaker separation, and accessible alternatives.

## 9. Captions, transcripts, and sound accessibility

Provide:
- Captions for dialogue and meaningful non-speech audio.
- Speaker labels and clear turn boundaries.
- Transcript/replay for important spoken information.
- Adjustable speech/music/effects/ambience levels.
- Mute, quiet mode, and no-music options.
- Visual alternatives for meaningful audio cues.
- Optional haptic alternatives only where appropriate and user-controlled.
- Controls that remain usable with screen readers and touch accessibility.
- No essential information communicated only through stereo position, pitch, or a sound effect.
- Caption timing that remains synchronized when playback speed changes.
- Localized captions and transcripts with quality review.

Quiet mode should reduce density and nonessential cues; it must not remove required dialogue or safety/interaction feedback without an accessible alternative.

## 10. Interruptions, focus, and lifecycle

The audio system must handle:
- Incoming calls, alarms, notifications, and audio focus loss.
- Headphone disconnect/reconnect.
- App background/foreground and process termination.
- Device silent mode and system volume.
- Bluetooth route changes and latency.
- Network loss for streamed or remotely delivered assets.
- Scene/world transitions and cinematic skip/replay.
- User changes to mute/volume during playback.

On interruption, pause, duck, or stop according to the audio category and platform policy. Restore only when safe and expected; never unexpectedly resume loud audio after an interruption. Release native players and decoded resources when no longer needed.

Offline availability must be explicit for required dialogue and story audio. A missing optional asset should fall back gracefully; a missing essential voice line should not make the experience impossible to understand.

## 11. Performance and content delivery

- Set per-device memory and simultaneous voice budgets after engine/device tests.
- Stream long ambience/music where appropriate; preload short critical cues.
- Avoid downloading all world audio on first launch.
- Use location/world bundles and predictable cache eviction.
- Validate codec, sample rate, channel layout, loudness, duration, and loop points at import.
- Use mono where spatial stereo is not needed; reserve high channel counts for intentional cases.
- Support compressed mobile delivery with quality checks.
- Preload cinematic voice/dialogue and critical cues before sequence start.
- Avoid audio pop/click on crossfade and scene transition.
- Profile CPU, memory, storage, network, and audio latency on target Android hardware.

## 12. Production and review workflow

1. Write the world/location sound bible and cue list.
2. Identify cultural and language review needs.
3. Create temp cues with documented source and licence.
4. Approve voice casting, pronunciation guide, scripts, and performer rights.
5. Record or compose source material.
6. Edit, clean, master, caption, localize, and bind semantic IDs.
7. Validate loudness, peaks, loop points, and technical format.
8. Test on device speakers, headphones, quiet mode, and interruptions.
9. Verify all dialogue and meaningful cues have captions or alternatives.
10. Version and archive source sessions, stems, scripts, rights, and runtime exports.

## 13. GoPAL-AI research findings

Selected source files reviewed:
- `src/engines/audio/audioEngine.ts`: small ambient-track list and mute preference; the inspected sound-effect method logs playback rather than producing an audible effect.
- `src/engines/world/worldAudioContract.ts`: categories for music, ambience, location, activity, interaction, transport, voice, and events; location profiles, priorities, mix values, and distance attenuation.
- `src/engines/world/worldAudioEngine.ts`: resolves cue gain, priority, distance attenuation, and cooldown/concurrency decisions in a lightweight in-memory resolver.
- `src/engines/world/worldAudioProfiles.ts`: example profiles for Emerald Valley, station, café, library, forest, airport, study room, and night street.
- `src/engines/world/worldAudioRuntime.ts`: thin player adapter imports `expo-audio`; this runtime is explicitly excluded because the new app must not use Expo.
- `src/engines/world/worldAnimationContract.ts` and `worldAssetAnimationRouter.ts`: semantic action vocabulary and clip alias resolution; useful as a conceptual separation between intent and art adapter, not as code to reuse.
- `src/features/cassidy/components/CassidyFirstMeetingCinematic.tsx`: first-meeting presentation combines animated UI, character rendering, dialogue, and completion side effects in one component.

### Recovered strengths
- Audio is considered across music, ambience, location, activity, interaction, transport, voice, and events.
- Location-specific profiles and priorities provide a useful design vocabulary.
- Distance attenuation, cue cooldowns, and mix categories are recognised.
- A semantic animation-action vocabulary illustrates the value of separating action intent from art clip names.
- First-meeting and arrival sequences demonstrate the intended emotional use of sound and presentation.

### Limitations and cautions
- The basic audio engine has a small fixed ambient catalogue and does not demonstrate a complete world soundscape.
- The inspected resolver tracks active cues in memory and uses runtime wall-clock time for cooldowns; it is not a durable content/runtime authority.
- The inspected playback adapter depends on Expo Audio and cannot be reused.
- Audio cue/profile coverage and final asset provenance are not proven complete.
- The reviewed first-meeting component combines presentation, UI, and completion side effects; the new system must separate cinematic playback from durable onboarding state.
- Voice capture, speech recognition, pronunciation assessment, retention, and consent are not established by these audio files.

These are selected-source observations, not a complete audit of all audio, voice, or localization content in the reference repository.

## 14. Open decisions

- Engine/middleware and final runtime adapter.
- Supported voice languages/locales at launch.
- Cassidy voice identity and localization/performance plan.
- Voice capture/transcription providers, if any, and data-processing policy.
- Music commissioning and world-specific sound bible scope.
- Offline dialogue/audio bundle policy and storage budget.
- Target loudness, true-peak, codec, and device concurrency budgets.
- Required caption languages and caption style.
- Whether adaptive music/stems are in the first release.
- Accessibility review and audio testing plan.

---

**Current status:** World sound identity, semantic cue contracts, mix architecture, adaptive soundscape, original music, character voice, language-learning audio integrity, captions/accessibility, interruption handling, delivery, and open decisions documented as a working specification. Runtime technology and launch scope remain open. No implementation is authorized.
