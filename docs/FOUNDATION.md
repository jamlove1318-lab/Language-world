# Product Foundation

## 1. Product definition

Language World is a living, explorable language-learning universe. Learners do not primarily navigate menus, lesson cards, or dashboards. They inhabit places, meet people, take part in activities, solve problems, explore, and build relationships. Language is the medium through which they participate in that world.

The world is the experience, not a decorative background around a conventional course.

## 2. Experience principles

1. **A place worth returning to.** Familiar locations, people, rituals, and ongoing stories create continuity.
2. **Learning through life.** Vocabulary, listening, speaking, reading, writing, grammar, and cultural understanding arise from meaningful situations.
3. **Consequences and memory.** Important actions can change places, relationships, available stories, and future conversations.
4. **Human warmth.** Characters have presence, motives, habits, humour, limits, and agency.
5. **Discovery over checklists.** Progress is legible but should not reduce the experience to streak pressure or endless reward collection.
6. **A coherent universe.** Each world has a distinct identity; travel connects worlds without flattening their differences.
7. **Accessibility and respect.** Learning difficulty, sensory intensity, input methods, and performance must be adaptable.

## 3. Universe and world model

### Emerald Valley — home world

Emerald Valley is the home world and emotional anchor. It is where the learner can return, reconnect with familiar characters, reflect, prepare, and see the consequences of shared experiences. It is not the whole universe and must not become the template copied for every language.

### Language worlds

Each supported language receives a distinct world identity. A world specification must define, at minimum:

- Geography, terrain, scale, landmarks, routes, and spatial logic.
- Climate, seasons, weather patterns, daylight, and environmental sound.
- Ecosystems, plants, wildlife, and natural hazards where appropriate.
- Architecture, materials, settlements, interiors, and public spaces.
- Inhabitants, communities, social customs, and daily rhythms.
- Food, crafts, music, festivals, stories, and cultural context.
- Language-learning situations, activity design, and progression.
- Local history, mysteries, narrative threads, and discoveries.

Worlds must not be reskins. Shared technology is encouraged; shared identity is not.

### Travel

Travel should have context and meaning: preparation, route, transition, arrival, orientation, and continuity. It can introduce new people, customs, language registers, and stories. A travel transition must not erase the state of the place being left.

## 4. Cassidy — canonical human character

Cassidy is a central human female character. She is not a fox, animal, mascot, anthropomorphic character, floating assistant, or decorative reward.

Her canonical design and character details are in the GoPAL-AI reference repository. Those materials are the authority for her appearance and established character facts. Do not invent a replacement design or casually change canon.

The new implementation is independent and should treat Cassidy as a complete character:
- Canonical identity and visual consistency.
- Human model, skeleton, facial rig, expressions, and body animation.
- Locomotion, navigation, interaction, and world participation.
- Personality, values, opinions, humour, curiosity, strengths, and flaws.
- Perception of the learner and the surrounding world.
- Dialogue, voice, conversational context, and emotional expression.
- Episodic and semantic memory with consent-aware controls.
- Relationship development grounded in shared experiences, not a visible score.
- Routines, personal goals, and autonomy that remain bounded and respectful.

Cassidy's character intelligence and relationship state must never be owned by the renderer. Rendering presents her; it does not define who she is.

## 5. Visual and world technology

Use 2D, 2.5D, and 3D intentionally. A location may use layered 2D composition, 2.5D depth, or full 3D depending on interaction and performance needs. The project does not require every object to be 3D.

Begin with simple, replaceable assets. Before large-scale asset production, establish:
- World coordinate conventions and scale.
- Camera projection, framing, and movement.
- Scene composition, depth ordering, and occlusion.
- Character placement, navigation, interaction anchors, and collision.
- Lighting, shadows, weather, day/night, and environmental effects.
- Asset dimensions, origins, pivots, materials, skeletons, and animation naming.
- Level-of-detail and mobile fallback policies.
- Asset manifests, versioning, validation, and replacement rules.
- Scene loading, transitions, pooling, and resource disposal.

A later high-quality tree, building, prop, or character should replace an early placeholder through its manifest/asset contract, not through rewrites of gameplay logic.

## 6. Living-world simulation

The environment should feel alive without requiring expensive continuous simulation of everything. Candidate systems include:
- Time of day, seasons, weather, lighting, and ambience.
- Wind and vegetation motion, moving water, clouds, and particles.
- Character schedules, idles, social encounters, and location-specific routines.
- Wildlife and ecosystem behaviors.
- Location state, object state, and environmental storytelling.
- Discoveries, activities, quests, and story events.
- Persistence of meaningful changes.

Simulation should use bounded update rates, relevance/visibility tiers, deterministic or seeded behavior where useful, and explicit pause/background policies. Rendering must not trigger domain mutations merely because a frame was drawn.

## 7. Learning philosophy

Learning should be contextual and multi-modal:
- Listening and comprehension in real situations.
- Speaking through conversations and purposeful interactions.
- Reading signs, letters, menus, books, maps, and messages.
- Writing through notes, forms, creative tasks, and correspondence.
- Vocabulary and grammar introduced in context, then revisited naturally.
- Pronunciation and listening practice with useful feedback.
- Cultural understanding without reducing cultures to stereotypes.
- Practice spaces and focused study tools available when the learner wants them.

The learner should be able to move between immersive experiences and focused practice without losing context.

## 8. Persistence and privacy

Use local-first domain repositories and versioned schemas. Separate learner progress, world state, character memory, relationship history, settings, and content metadata. Define what is local, what is synchronized, how conflicts resolve, and what can be exported or deleted. Never make a single unbounded store the owner of every domain.

## 9. Non-goals and guardrails

- No Expo.
- No engine selection by popularity alone.
- No giant scaffold before an Android proof of concept.
- No generic reskinned maps for each language.
- No Cassidy redesign.
- No fake production-ready character asset when the canonical asset is unavailable.
- No card-grid-first main experience.
- No renderer-owned personality, memory, or learning outcomes.
- No copying GoPAL-AI source code as the new architecture.
- No silent deletion of useful ideas during the source audit.

## 10. First vertical slice

The first playable slice should be small but representative: one explorable home-world location, a controllable character, one human Cassidy presence or validated placeholder pipeline, a few interactive objects, one meaningful contextual learning activity, a small living-environment loop, save/restore, and a measured Android build. Its purpose is to validate the runtime and architecture before content scale expands.
