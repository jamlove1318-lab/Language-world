# GoPAL-AI Archive → Language-world: Product Gap Audit

**Date:** 18 November 2026  
**Source repository:** `jamlove1318-lab/GoPAL-AI` (read-only)  
**Destination repository:** `jamlove1318-lab/Language-world`  
**Purpose:** Recover the product ideas, experience requirements, and lessons in GoPAL-AI that must not be lost during the clean rebuild.

## 1. Executive conclusion

GoPAL-AI is not just an old implementation. It is a large archive of product thinking, character design, world-building, narrative ideas, learning experiences, interaction concepts, audio direction, asset experiments, production workflows, and implementation attempts.

The clean rebuild must therefore be **implementation-new, but idea-informed**. We should not copy the old architecture, renderer, runtime, asset factory, or code. We should recover the valuable experience requirements, decide which are still right, simplify them, and give each one a clear owner in Language-world.

The central product was broader than the first implementation made it appear:

- A living, explorable universe with Emerald Valley as the home world—not the entire universe.
- Language worlds that are genuinely distinct places, not course folders or reskinned scenes.
- Cassidy as the emotional heart and a fully embodied human companion with her own life, stories, initiative, and boundaries.
- Residents and characters with their own identities, relationships, routines, stories, and introductions.
- Adventures, mysteries, games, creative activities, cultural experiences, discovery, travel, and learning that can happen with or without Cassidy or another resident.
- Cinematic presentation: first meeting, world tours, world-to-world travel, resident reveals, story moments, discoveries, festivals, and special adventures.
- A world that remembers meaningful changes and offers a welcoming return without guilt or artificial urgency.
- A flexible art system that can start with attractive temporary assets and later accept bespoke, high-quality assets without rewriting gameplay.

The most important correction for Language-world is to build the **whole experience platform**, not just a companion simulator, a language lesson app, or a 3D exploration demo.

## 2. Repository inventory and evidence boundary

The latest recursive Git tree was fetched from the GoPAL-AI `main` branch. GitHub reported `truncated: false`, with **709 tree entries: 608 files and 101 directories**.

The 608 files include:
- 223 TypeScript files and 104 TSX files.
- 77 Markdown documents.
- 65 GLB files, plus other image, video, HDRI, Blender archive, and JSON assets.
- 42 Python files, 13 MJS files, build scripts, validation scripts, and automation.
- Application entry/build configuration, Supabase schema/migration, CI workflows, production reports, manifests, and contracts.

Major areas include `src/` (324 files), `assets/` (108), `docs/` (61), `factory/` (34), `tools/` (16), `scripts/` (14), `.github/` (8), and `artifacts/` (5). The source tree includes learning, Cassidy, world simulation, world presentation, object/transport systems, mini-games, quests, memory, journey, audio, creation, and persistence.

**Evidence rule:** A design document proves an idea was specified. A source file proves code exists. A manifest or registry proves a record was declared. None of those alone proves a complete, reachable, persisted, accessible, tested player experience. This audit distinguishes product ideas from code-level foundations and from end-to-end verified behavior.

This is a repository-wide inventory and deep review of the major product specifications, architecture documents, and representative source systems. It is not yet a line-by-line behavioral verification of every one of the 608 files, nor a successful Android build/device test. Remaining source areas must continue to be traced before the audit can be called complete.

## 3. The full product vision recovered from GoPAL-AI

### 3.1 A universe, not a dashboard

The old blueprint repeatedly says the product should feel like a place to return to. The world is the primary experience surface; conventional screens should be reserved for utilities such as settings, privacy, account, accessibility, and archive management.

Emerald Valley is the home world. It has a defined geography, landmarks, routes, gathering places, interiors, atmosphere, time, weather, seasons, sound, events, and places that change through use. The valley's visual specification includes Mount Emerald, treelines, sky, clouds, mist, terrain, Suzu Stream, paths, café, market, library, station, sanctuary, garden, tunnel, and other locations.

**Carry forward:** authored geography and spatial continuity; discoverable places; environmental storytelling; meaningful interiors; world-specific identity; navigation that feels like moving through a place.

**Do not carry forward literally:** old screen layout, map coordinates, renderer assumptions, React Native world composition, old scene runtime, or any existing GoPAL 3D implementation.

### 3.2 Cassidy: emotional anchor and independent person

The old project contains a substantial Cassidy identity and character bible, a first-meeting script, personality, perception, autonomy, life activity, dreams, stories, adventures, memory, world presence, interaction lifecycle, and visual production specifications.

Cassidy is a **human female character**, not an animal, mascot, or generic chatbot. Her approved visual identity is a creative reference; her new model, rig, animation set, expressions, and runtime must be created independently.

The first-meeting script already has a short welcome and a persistent first-meeting memory. A dedicated cinematic component exists, but the inspected script does not itself tour Emerald Valley, explain the home-world geography, demonstrate the passport/world system, or stage a full guided opening journey.

The Cassidy completion checklist also calls for:
- persistent identity and personality separate from temporary mood;
- preferences and favorites that evolve gradually and consistently;
- embodied presence, facing, movement, waiting, leaving, and restoration;
- independent life activities such as wandering, reading, café visits, rain-watching, stargazing, dreaming, storytelling, helping, resting, discovering, and celebrating;
- bounded initiative and the ability to remain quiet;
- memory of meaningful interactions, places, stories, and shared experiences;
- dreams, stories, adventures, conversation, relationship expression, world consequences, and safe AI/provider failure behavior.

**Carry forward:** Cassidy has a life beyond the learner and should sometimes invite, accompany, surprise, disagree, joke, discover, or simply be present. Her relationship is expressed through continuity and shared experiences, never a visible affection meter or manipulative dependency.

**Important balance:** Cassidy is the heart of the universe, but she is not the universe's only source of content. The world must remain compelling when she is absent, elsewhere, quiet, or not involved.

### 3.3 Residents and character society

GoPAL-AI has resident/NPC roles, character registries, routines, behavior, presentation, animation, relationship and memory engines, encounter systems, story threads, and destination-specific characters.

The world specification gives individual residents roles and locations, including named characters around the café, market, library, station, sanctuary, and garden. The wider blueprint describes interconnected character lives, shared events, differing perspectives, familiarity progression, character webs, and evidence-based observations.

**Carry forward:** residents should be recognizable people with authored identities, purposes, routines, relationships, and story continuity. Introductions and reveals can be staged as cinematic experiences. Some residents should have their own lives and stories that do not require Cassidy.

**Not yet established:** a complete, durable, world-wide social simulation with coherent causal relationships among every character. Treat this as a design direction, not an already solved system.

### 3.4 Stories, mysteries, and adventures

The archive describes multiple narrative scales:
- micro-stories lasting minutes;
- local stories spanning several visits;
- resident/character arcs spanning weeks;
- seasonal stories;
- long world arcs;
- personal arcs based only on verified learner history.

It also describes rumors and hints, secrets, hidden places, recurring symbols, objects with provenance, environmental evidence, story choices, mysteries with planned resolutions, and adventures that lead to persistent world changes.

Cassidy's own story/adventure ideas include dreams, invitations, discoveries, hidden paths, unusual objects, and places that appear at the right moment. But stories must also arise independently from locations, history, objects, creatures, cultures, and the learner's own curiosity.

**Carry forward:** a real narrative system with authored canon, stable story IDs, prerequisites, branching, durable evidence, recap/re-entry, and planned resolution. Never use endless vague mysteries solely to keep people opening the app.

**Audit caution:** the inspected story-choice engine is a small state/choice primitive; resident story threads are narrow and fixed; a story catalogue or runtime registry is not proof of a fully playable narrative platform. Full narrative orchestration, authored-content validation, persistence, interruption recovery, and story-to-world consequence remain requirements to design and verify.

### 3.5 Games, activities, and creative experiences

GoPAL-AI's mini-game catalogue specifies 60 mechanics across discovery/search, building/puzzles, arcade/reflex, social/communication, listening/audio, story/adventure, and creative/construction. Examples include Word Hunt, Sign Spotter, Phrase Builder, Logic Lanterns, Word Dash, Market Rush, Train Counter, Dialogue Detective, Audio Map, Announcement Alert, Mystery Room, Detective Case, Treasure Map, Dream Theatre, Story Composer, Recipe Creator, and World Builder.

The wider experience catalogue includes:
- focus, adventure, conversation, relax, challenge, creative, and surprise modes;
- creative studio, personal phrasebooks, stories, dialogue scenes, postcards, collections, and room displays;
- calligraphy, soundscape mixing, crafting, listening, pronunciation, and cultural activities;
- museums, gardens, markets, workshops, fictional challenge spaces, mystery rooms, dream theatres, and arcades;
- games that can be played independently of residents and Cassidy.

**Carry forward:** mechanics should be reusable, but the content, art, context, sound, difficulty, and narrative consequence should be authored for each world. Avoid turning every activity into a multiple-choice modal. Activities must have a real interaction loop, clear learning purpose where relevant, and persistence only where it adds meaning.

**Current evidence:** the catalogue and selection foundation exist. The archive itself labels many actual playable implementations, cross-world reuse, variety selection, and world-reactive outcomes as future work. Several inspected game/runtime registrations are declarations, not proof of complete mechanics.

### 3.6 Learning and language mastery

The archive contains contextual learning, adaptive conversation, Socratic roleplay, tutor experiences, learning needs, vocabulary/word banks, spaced recall ideas, skill/capability evidence, evaluation, listening, writing, calligraphy, pitch/prosody practice, and real-world mission preparation.

Important ideas to preserve:
- language is used in meaningful situations rather than isolated drills only;
- learner intent and session energy influence activity choice;
- hints and correction intensity should be adjustable;
- comprehension, productive use, recall, fluency, confidence, and mastery should not collapse into one opaque score;
- mistakes are part of learning and should not be punished;
- pronunciation features must honestly distinguish playback, shadowing, microphone capture, transcription, speech recognition, and measured pronunciation;
- review should emerge through stories, activities, and useful context;
- real-world practice bridges are optional, privacy-conscious, and never require unsafe behavior or sharing sensitive information.

**Current evidence:** learning scenarios and evaluation primitives exist, but inspected evaluation is largely rule/concept matching and does not prove robust semantic understanding, speech recognition, or pronunciation assessment. The new project must make explicit claims only for capabilities actually implemented and tested.

### 3.7 Travel and distinct language worlds

The archive has a passport/destination concept, Japanese and French destination catalogs, real and fictional places, travel preparation, world arrival/departure scene contracts, railway and airport infrastructure, and vehicle kinds including trains, buses, cars, bicycles, boats, and airplanes.

The user-defined direction for Language-world extends this: Emerald Valley is the home world; language worlds must have their own geography, climate, ecology, architecture, settlements, residents, culture, landmarks, stories, activities, and soundscape.

The inspected GoPAL code has a language-world list and location catalog, but physical construction can fall back to shared theme logic. That is not enough to establish genuinely distinct worlds.

**Carry forward:** a world passport and travel network, but travel must be an experience. The learner should see a station, approach/board a vehicle, experience departure, journey, arrival, and the new world's reveal. A train journey from Emerald Valley to a Spanish world is a full authored cinematic sequence, not a short title overlay or loading fade. Planes can serve longer inter-world routes; cars, buses, boats, bicycles, and walking can serve authored routes within worlds where appropriate.

**Critical gap:** the inspected old departure/arrival scene engines define beat/shot metadata, but no evidence yet proves a complete vehicle journey with a moving train/plane, camera choreography, station/terminal staging, sound/music transitions, interior/exterior shots, destination reveal, interruption handling, and return-to-world state restoration.

### 3.8 Cinematic direction and presentation

GoPAL-AI contains a world camera specification, tour concepts, arrival/departure scene contracts, a first-meeting cinematic, animation intent contracts, resident reveal shot types, and visual staging ideas.

The new project should have a dedicated **Cinematic Experience System** with:
- authored sequence timelines and reusable shot/beat primitives;
- camera rigs, cuts, pans, tracking, framing, depth of field where supported, lighting and environment cues;
- character blocking, gaze targets, gestures, facial expression, locomotion, anticipation, reaction, and settling;
- dialogue, subtitles, localization, voice, music, ambience, sound effects, and ducking;
- trigger conditions, scene preloading, streaming boundaries, save/checkpoint rules, skip and replay policies;
- safe interruption/resume behavior for calls, app backgrounding, low battery, or process death;
- reduced-motion and accessible alternatives;
- performance tiers and non-cinematic fallbacks.

Cinematics must be data/content-driven where practical, so the designer can create new resident reveals, tours, travel scenes, and story moments without requiring bespoke gameplay code each time.

### 3.9 Living world, objects, and consequences

The old product specifications describe:
- persistent object placement and personalized environments;
- object memory and provenance (where found, who gave it, why it matters, when it entered the story);
- plants and a companion plant;
- inventory, crafting, collections, cultural rooms, discoveries, and postcards;
- world map layers for visited places, unknown places, stories, rumors, events, memories, and environmental changes;
- physical evidence after events (photographs, books, decorations, repaired objects, changed rooms);
- time capsules, memory museum, world photo album, inspiration boards, and personal notes;
- natural routines, weather/time/season, festivals, world news, and asynchronous letters or objects.

**Carry forward:** world changes should be observable and attributable to meaningful events. Keep canonical world state separate from rendering. A visual object must not be the only record of a durable event.

**Current evidence:** object schemas/catalogs and interaction primitives exist, but inspected action execution and in-memory event/quest paths do not prove robust, durable object consequences. Interiors, inventory provenance, personalized placement, plant lifecycle, and full map overlays need dedicated verification/design.

### 3.10 Audio and atmosphere

The archive's audio direction includes location acoustic profiles, music, ambience, location, activity, interaction, transport, voice, and event layers; spatial attenuation; cooldowns and active one-shot limits; crossfades; quiet mode; weather/time/activity influence; and provenance/licensing gates.

**Carry forward:** audio is a world system, not a collection of unrelated screen sounds. World transitions should carry and crossfade audio intentionally. Train platforms, station interiors, carriage ambience, announcements, rail movement, aircraft cabins, local street ambience, festivals, and resident voices should have distinct authored sound identities. Provide independent controls, mute/quiet mode, interruption recovery, captions/transcripts, and hearing-accessible alternatives.

**Current evidence:** semantic audio contracts and mix logic exist in GoPAL, but the old playback runtime is Expo-specific and is explicitly excluded. The new audio backend must be chosen and tested with the new engine on Android.

### 3.11 Return experience and healthy motivation

The archive emphasizes:
- welcoming re-entry and concise recaps;
- no guilt for absence, punitive streak debt, forced catch-up, or artificial urgency;
- meaningful reasons to return: a story continuation, changed place, personal creation, new discovery, a letter, a festival, a resident's update, or a self-chosen goal;
- personal journey stories and then-vs-now comparisons;
- personal best moments and mastery moments;
- sanctuary/quiet modes and adjustable companion initiative.

**Carry forward:** user agency, calm pacing, honest memory, meaningful continuity, and opt-in notifications. Do not implement engagement loops that manufacture urgency or emotional dependence.

### 3.12 Future-facing possibilities

The master specification also records future ideas that should not be forgotten but should not block the first playable slice:
- shared co-op study, cultural exploration, mini-games, classroom experiences, and community checkpoints;
- optional camera/vision experiences;
- future AI-generated content with provenance, review, and safety;
- real-world observation missions and trip preparation;
- user-authored goals and personal notes;
- local-first exportable archive and understandable structured records;
- world radio/personal soundtrack and natural-language experience requests.

These belong in a future-opportunities register, not in the first prototype scope.

## 4. What GoPAL actually demonstrates versus what it only describes

| Area | Evidence found in GoPAL-AI | What remains unproven / incomplete |
|---|---|---|
| First meeting | Versioned welcome state, persistent first-meeting memory, dedicated animated component | Full home-world guided tour, world passport explanation, polished staged character performance, interruption recovery |
| Cassidy life | Multiple autonomy, perception, life, narrative, memory, and presence engines | One authoritative lifecycle, coherent long-term causal memory, complete verified autonomous behavior |
| Cassidy stories | Seeded story/dream/adventure templates and life moments | Authored branching narrative platform with durable world-wide continuity |
| Residents | Character registries, schedules, routines, encounter and presentation engines | Complete character web, consistent cross-world identity and durable multi-character story consequences |
| World locations | Emerald Valley spec, Japanese/French locations, physical catalogs | Distinct fully authored language worlds rather than shared-theme fallback |
| Travel | Transport types, routes, arrival/departure metadata, world entrance overlay | Full cinematic train/plane travel, vehicle boarding, continuous route, arrival reveal, save/recovery |
| Mini-games | 60-game design catalogue, engine and selector foundations | Verified end-to-end implementation for each advertised mechanic and cross-world content packs |
| Learning | Contextual scenarios, hints, feedback, skill/evidence concepts | Reliable semantic/speech/pronunciation capability, full accessibility and offline verification |
| Stories/quests | Choice primitive, resident story threads, quest engines | Durable authored story graph, non-resident stories, causal event log and restart-safe progression |
| Objects | Catalogs, schemas, action types, object interactions | Persistent action consequences, interiors, provenance, personalized placements, full object lifecycle |
| Audio | Semantic categories, profiles, mix/attenuation/cooldown logic | New-engine Android playback, cinematic audio routing, interruption/focus and device validation |
| Environment | Time/weather/season and world runtime concepts | Explicit simulation clock policy, world-specific climate, bounded offline simulation, causal history |
| Creativity/museum | Creation service and Museum UI foundations | Full edit/reopen/delete/export/asset lifecycle and account-scoped durable archive |
| Asset production | Large old art pipeline, source policies, contracts, validators, real asset experiments | The old pipeline is rejected; new pipeline must support placeholder-to-final replacement and be proven on Android |
| Persistence | Local storage, memory, journey, event and database systems | One canonical owner per domain, transactional/outbox recovery, account isolation, export/delete and offline conflict handling |

This table is deliberately conservative. It does not downgrade an idea because its old implementation was incomplete; it separates the value of the idea from the reliability of the previous implementation.

## 5. High-priority requirements missing or not explicit enough in Language-world

The following requirements should be added to the new project's foundation and roadmap.

### P0 — Required before the first production-quality content wave

1. **Replaceable asset contracts:** every visual/audio asset has a stable semantic ID, version, type, representation, scale/unit convention, origin/license, dependencies, checksums, LOD/texture/audio variants, rig/skeleton compatibility, animation bindings, fallback, and quality/performance tier. Gameplay references semantic IDs, never hardcoded filenames or artist-specific node paths.
2. **Placeholder-to-final swap test:** ship the first slice with attractive temporary assets; replace a character, building, train, prop, environment, and animation with designer-made assets without rewriting gameplay or world-state code.
3. **Cinematic sequence runtime:** authored timelines, camera/shot control, actor blocking, animation cues, dialogue/subtitles/voice, audio mix, lighting/environment cues, triggers, preloading, checkpoints, skip/replay, and resume.
4. **Opening experience specification:** Cassidy's first meeting must include a staged introduction and a guided Emerald Valley tour, explain the home world, show what can be explored/done, and introduce how the learner travels to language worlds. The experience must remain skippable and re-enter safely.
5. **World travel sequence:** station/terminal approach, timetable/route context, boarding, departure, travel montage/interior, transition through world boundary, arrival, destination reveal, and playable handoff. Train and plane sequences must be reusable but allow world-specific staging.
6. **Local transport experiences:** authored cars, buses, boats, bicycles, and walking routes where suitable; vehicles need boarding/alighting, seat/interior staging when relevant, camera and sound, route progress, and interruption recovery.
7. **Resident introduction/reveal framework:** anticipation before direct reveal, environmental/audio clues, reveal shot, character-specific entrance, first interaction, and durable memory/continuity.
8. **Performance tiers:** placeholder and production assets must have device tiers, LODs, texture/audio budgets, animation complexity limits, and graceful lower-end fallbacks from the beginning.
9. **Cinematic accessibility:** subtitles/captions, language selection, voice controls, reduced motion, skip, replay, and non-timed alternatives.
10. **Authored world identity:** every language world needs a world bible and measurable uniqueness across geography, climate, ecology, architecture, culture, residents, wildlife, transport, sound, story, and activity—not merely a palette or location list.

### P1 — Required for a complete, coherent universe

11. Narrative canon, story graph, clue/evidence model, mystery resolution plan, and story-state migration.
12. Non-Cassidy/non-resident story and adventure delivery.
13. Creature and wildlife ecology, discovery/reveal, behavior, interaction, and world-specific audio/animation.
14. Character web, schedules, relationships, perspectives, and cross-character consequences.
15. Persistent object provenance, personal spaces, plant lifecycle, inventory/collections, and visible world evidence.
16. Map layers for visited/unknown places, stories, rumors, events, discoveries, and personal memories.
17. Events/festivals/seasonal arcs and fictional world news with durable outcomes.
18. Natural-language or intent-based activity request, plus explicit experience modes and session-length adaptation.
19. Creative studio, personal archive, journey book, museum, postcards, time capsules, photo album, and learning rewind as one coherent set of personal records.
20. World audio identity, radio/soundtrack, transition crossfades, and location acoustic zones.
21. Real-world bridges and travel-preparation learning with privacy and safety safeguards.

### P2 — Future opportunities, not first-slice blockers

22. Optional co-op/shared experiences and classroom activities.
23. Camera/vision learning and discovery.
24. AI-generated story/world content with safety, provenance, and editorial review.
25. Broader community features, always opt-in and privacy-first.

## 6. Asset strategy for the new project

The user's explicit production direction is:

- Do not wait for premium character/world art to start implementation.
- Use the best suitable temporary assets available or create lightweight placeholders.
- Build the world, scenes, interactions, animation hooks, cinematic staging, and content systems around stable semantic contracts.
- A graphics designer will create the high-quality assets later.
- Replace temporary assets with final assets without changing gameplay logic or world simulation.

This means **placeholder quality is temporary; architecture quality is not**.

### Required asset record (conceptual)

Each asset record should eventually carry:
- stable semantic asset ID and version;
- category and intended use;
- source URI, creator, license, attribution, and dependency information;
- runtime artifact and checksum;
- representation: 2D, 2.5D, 3D, video, audio, or other;
- dimensions, scale, coordinate convention, pivot/origin, units, orientation;
- material/texture/audio properties and compression;
- LODs and device/performance tiers;
- skeleton/rig identifier and compatibility version where animated;
- semantic animation/action bindings;
- scene/cinematic role and optional camera/lighting metadata;
- fallback asset and missing-asset behavior;
- review status: placeholder, candidate, validated, approved, deprecated.

Gameplay and narrative systems refer to semantic IDs and events. They must not depend on a specific mesh name, texture path, artist export folder, Blender collection, Unity prefab, Godot node path, or a particular character skeleton.

### Replacement acceptance test

A designer-produced final asset must be importable and bindable through the documented workflow. Replacing the placeholder must preserve:
- world entity identity and saved state;
- collision/interaction targets or an explicit compatible replacement;
- semantic actions and animation requests;
- cinematic cue references;
- camera framing and scale constraints;
- localization/audio/subtitle timing where relevant;
- LOD and low-end fallback;
- save compatibility and deterministic tests.

Do not create or reuse the old GoPAL factory, Blender scripts, exporter, validators, renderer, scene runtime, manifest contracts, or production assumptions. The new asset workflow is an independent design.

## 7. Proposed product architecture additions

These are responsibilities, not a commitment to a particular engine or programming language.

- **Cinematic Director:** sequence state, timeline, shot, camera, actor blocking, dialogue, sound, lighting, transitions, checkpoints, accessibility, interruption/resume.
- **Asset Catalog and Binding:** semantic asset identity, versioning, compatibility, variant selection, fallbacks, LOD/performance tiers, runtime promotion.
- **Travel Director:** route, transport mode, boarding, departure, in-transit sequence, arrival, destination reveal, world handoff.
- **World Identity Package:** authored geography, ecology, climate, culture, settlement, characters, creatures, transport, audio, stories, activities, and progression rules per world.
- **Narrative Canon and Story Runtime:** story graph, authored content validation, clues, evidence, branches, recaps, resolution, event consequences.
- **Character Presence and Performance:** identity, schedule, intent, movement, gaze, expression, voice, interactions, and scene performance separated from renderer-specific implementation.
- **Experience Director:** learner intent, available time, preferred energy, accessibility, learning needs, world context, novelty, and content validity.
- **Durable Event/Outbox:** stable event IDs, causal links, idempotency, retries, per-domain persistence, restart recovery, and derived-state rebuild.
- **Personal Archive:** learner-owned creations, notes, discoveries, learning evidence, memories, and export/retention controls.

The engine selection remains open. These responsibilities must be expressible without committing to Godot, Unity, Unreal, or a specific asset format.

## 8. What must not be inherited from GoPAL-AI

The following are explicitly excluded from reuse/adaptation:
- all GoPAL 3D models, meshes, rigs, skeletons, animation exports, and generated character assets;
- Cassidy's old model/rig/export and all other old production assets as runtime assets;
- GoPAL renderers, visual resolvers/controllers, scene runtime, runtime bridges, and world presentation implementation;
- Blender automation, character/world factories, export/conversion/normalization/validation scripts, production jobs and remote art pipeline;
- old pipeline manifests, registries, renderer contracts, asset contracts, package assumptions, and runtime-specific tooling;
- Expo/React Native application architecture and Expo audio integration;
- old coordinates, scene transforms, runtime state assumptions, and UI navigation structure.

Cassidy's approved identity and visual design references may inform the new character design. Product ideas, narrative concepts, world-building, and lessons from failed implementation may inform the new design. That is not permission to reuse the old production pipeline.

## 9. Next audit work and completion criteria

The next source-review passes should continue through:
1. all Cassidy engines, UI, event callers, and actual mounted/reachable paths;
2. all story, rumor, quest, mystery, clue, and persistence paths;
3. world catalogs, language-world physical data, creatures/wildlife, and actual world uniqueness;
4. transport/vehicle route simulation and all travel entry points;
5. object interactions, interiors, inventory, provenance, and personal spaces;
6. event/festival/environment simulation and offline recovery;
7. all learning mechanics and the 60-game catalogue versus actual runtime implementations;
8. creative/archive/museum/time capsule/journey features;
9. audio, voice, animation, cinematics, and accessibility;
10. account, sync, privacy, export/delete, offline, and failure behavior.

For each feature, record: source files, actual caller/reachability, owner, state model, persistence, happy path, interruption/restart behavior, accessibility, tests, status, and new-project decision.

**No claim of complete repository audit is made yet.** The tree inventory is complete for the fetched branch snapshot; the product-specification review is deep; the code-level trace and end-to-end verification remain ongoing.


## 10. Follow-up source trace: Cassidy and language-world integration

A deeper source pass confirms that Cassidy's old implementation contains valuable independent-life concepts but also multiple overlapping owners. Her activity selection, presence director, life-moment generator, narrative list, interaction lifecycle, personality, runtime snapshot, world presence, scene anchors, and UI are separate modules. The new project should consolidate these into one coherent domain with clear boundaries between identity, motives/plans, perception, memory, relationship, physical performance, dialogue, and presentation. Do not equate numeric personality traits or generated template moments with a complete evolving character.

The old life-state and narrative history are locally persisted under user keys, but interaction writes span memory, relationship, personality, and deduplication in sequence rather than a single recoverable transaction. Some APIs default to a shared-looking local user ID. Language-world must use explicit learner identity, durable idempotency, transaction/outbox recovery, and no shared fallback profile.

A concrete language-world registry mismatch was found: the primary physical world registry lists Emerald Valley, Japanese World, and French World, while a separate language-world engine describes Japanese, Spanish, French, and Korean. The two registries use different IDs and are not unified. Physical location data also generates generic guides, teachers, and city-local residents. This confirms that world identity and resident content need one canonical registry and fully authored world packages.

The old transport data contains useful rail/road/runway geometry and vehicle waypoint loops. It still does not establish the requested cinematic journey, vehicle boarding/alighting, route progression, departure/arrival reveal, or restart-safe handoff.

See sections 32–33 of `PRODUCT_SYSTEMS_AUDIT.md` for detailed source-level evidence and the resulting new-project requirements.
