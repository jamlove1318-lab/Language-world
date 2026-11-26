# Language World

A living, explorable universe where people learn languages by inhabiting distinct worlds, meeting people, discovering places, and sharing meaningful experiences.

## Core vision

This is not a conventional language-learning dashboard with a world map attached. The world is the primary experience. Learning happens through exploration, stories and mysteries, games, conversations, creative work, cultural experiences, discovery, and everyday life. Cassidy is the heart of this universe; residents are one part of its much larger cast and world—not the whole experience.

## World structure

- **Emerald Valley** is the home world: the emotional anchor and place to return to.
- Every language has its own distinct world, with its own geography, climate, ecosystems, architecture, settlements, inhabitants, culture, soundscape, stories, landmarks, and learning experiences.
- Worlds may share underlying technology, but must not become reskinned copies of one generic map.
- Travel between worlds should feel meaningful and preserve continuity.

## Cassidy

Cassidy is a central **human female character** with physical presence in the world. She is not an animal, mascot, decorative reward, or chatbot widget.

Her canonical design and character details are maintained in the GoPAL-AI reference repository. Those references are the source of truth; do not redesign her. The new project will build an independent character runtime around her identity, personality, autonomy, movement, expressions, conversations, memory, relationships, and participation in world life.

## Technology principles

- **No Expo.** The engine/runtime is an explicit architecture decision and must be selected through Android proof-of-concept testing.
- Evaluate suitable candidates (including Godot, Unity, and Unreal) against real device performance, rendering, animation, interaction, scene transitions, loading, memory, battery/thermal behavior, build size, and low-end fallbacks.
- Use 2D, 2.5D, and 3D where each is appropriate.
- Start with replaceable low-poly/placeholders; establish asset manifests, dimensions, origins, collision, animation, and scene contracts before polishing content.
- Keep simulation/domain logic independent from rendering.
- Design for local-first persistence, versioned data, and explicit synchronization.

## Reference repository boundary

GoPAL-AI is a **read-only reference** for research: ideas, specifications, character canon, assets, and lessons learned. Do not modify it. Reimagine and improve selected ideas here; do not copy its implementation blindly.

## Project status

The project is in foundation and source-audit stage. No engine has been selected yet. The first implementation milestone is a measured Android vertical slice, not a large speculative scaffold.

See [Foundation](docs/FOUNDATION.md), [Architecture Decisions](docs/ARCHITECTURE_DECISIONS.md), [Source Audit](docs/SOURCE_AUDIT.md), and [Roadmap](docs/ROADMAP.md).

## Audit documents

- [Source repository audit](docs/SOURCE_AUDIT.md)
- [Product systems audit — Cassidy, living world, relationships, and learning](docs/PRODUCT_SYSTEMS_AUDIT.md)
- [Architecture decisions](docs/ARCHITECTURE_DECISIONS.md)
- [Project roadmap](docs/ROADMAP.md)
- [Android-first engine evaluation](docs/ENGINE_EVALUATION.md)
- [Cinematic experience blueprint](docs/CINEMATIC_EXPERIENCE_BLUEPRINT.md)
- [Graphics and asset handoff standard](docs/ASSET_HANDOFF_STANDARD.md)
- [Replaceable assets and cinematic pipeline](docs/ASSET_AND_CINEMATIC_PIPELINE.md)


## GoPAL-AI source archive review

The new build preserves the valuable product ideas from the original repository while rejecting its old implementation and 3D production pipeline. See the [GoPAL-AI Archive → Language-world Product Gap Audit](docs/GOPAL_ARCHIVE_TO_LANGUAGE_WORLD_GAP_AUDIT.md) for recovered requirements, evidence boundaries, missing systems, cinematic travel, and the placeholder-to-final asset strategy.

## Project documentation

- [Master Blueprint](docs/MASTER_BLUEPRINT.md) — central product specification (working draft; not approved for implementation).
- [Blueprint Work Register](docs/BLUEPRINT_WORK_REGISTER.md) — tracks research, supporting specifications, open decisions, and approval gates.
- [Cassidy Character Bible](docs/CASSIDY_CHARACTER_BIBLE.md) — independent working character specification, pending review.
- [World & Universe Bible](docs/WORLD_UNIVERSE_BIBLE.md) — universe structure, Emerald Valley foundation, and distinct world-authoring standard.
- [Experience Catalogue](docs/EXPERIENCE_CATALOGUE.md) — experience families, 60 research game seeds, learning integration, authoring, persistence, accessibility, and quality gates.
- [Learning Design](docs/LEARNING_DESIGN.md) — language capability evidence, adaptive practice, assessment limits, speech honesty, privacy, and accessibility.
- [World Simulation Specification](docs/WORLD_SIMULATION_SPEC.md) — world time, weather, seasons, resident life, ecology, plants, events, and offline continuity.
- [World Objects and Spaces](docs/WORLD_OBJECTS_AND_SPACES.md) — spatial hierarchy, buildings/interiors, object lifecycles, interactions, navigation, inventory, and replaceable assets.
- [Travel Experience Specification](docs/TRAVEL_EXPERIENCE_SPEC.md) — inter-world routes, transport, cinematic journeys, arrival, and interruption-safe handoff.
- [Audio, Voice, and Soundscape](docs/AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md) — world sound identity, music, character voice, learning audio, captions, and accessibility.
- [Narrative and Story Continuity](docs/NARRATIVE_AND_STORY_CONTINUITY_SPEC.md) — world canon, mysteries, clues, meaningful choices, resident stories, and long-term continuity.

- [Persistence, Privacy, and Synchronization](docs/PERSISTENCE_PRIVACY_AND_SYNC.md) — learner identity, offline-first data, sync/conflicts, memory provenance, privacy, security, export, deletion, and recovery.

- [Creative Experiences and Personal Archive](docs/CREATIVE_EXPERIENCES_AND_PERSONAL_ARCHIVE.md) — journal, phrasebook, postcards, comics, collections, museum, time capsules, transcript archive, editable source, media lifecycle, privacy, and cultural integrity.
