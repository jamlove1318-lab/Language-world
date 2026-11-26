# Language-world — Narrative, Stories, Mysteries, and Continuity

**Status:** Working specification v0.1; not approved for implementation.  
**Purpose:** Define how authored stories, mysteries, adventures, resident lives, world events, and learner choices create a coherent universe over time.  
**Related specifications:** [Experience Catalogue](EXPERIENCE_CATALOGUE.md), [World & Universe Bible](WORLD_UNIVERSE_BIBLE.md), [Cassidy Character Bible](CASSIDY_CHARACTER_BIBLE.md), [World Simulation Specification](WORLD_SIMULATION_SPEC.md), [World Objects and Spaces](WORLD_OBJECTS_AND_SPACES.md), [Travel Experience](TRAVEL_EXPERIENCE_SPEC.md), [Cinematic Experience Blueprint](CINEMATIC_EXPERIENCE_BLUEPRINT.md).  
**Source boundary:** GoPAL-AI is a read-only research archive. Its narrative, quest, clue, and event code is evidence only; none of its runtime, state, storage, or UI implementation is a dependency.

---

## 1. Narrative promise

Language-world must offer stories worth following even when the learner is not trying to complete a lesson. The universe should create curiosity, anticipation, emotion, humour, surprise, discovery, and a reason to return.

Narrative may appear through:
- Large world and universe mysteries.
- Multi-part adventures and expeditions.
- Local stories tied to places, objects, history, and communities.
- Resident character arcs and relationships.
- Cassidy's independent adventures and personal commitments.
- Creature/ecology discoveries.
- Festivals, seasons, and world events.
- Letters, journals, recordings, artifacts, rumours, environmental traces, and hidden spaces.
- Learner-created stories and memories.

Not every experience needs a story, and not every story needs a quest marker, dialogue tree, reward, or Cassidy appearance.

## 2. Narrative scales and story portfolio

Author content across distinct scales:

1. **Moment:** a brief surprising, funny, beautiful, or meaningful occurrence.
2. **Micro-story:** a small discovery or interaction resolved in one visit.
3. **Local story:** a multi-step story tied to a place, object, or small group of characters.
4. **Character arc:** a resident or Cassidy's evolving motives, choices, and commitments.
5. **Regional arc:** a mystery or conflict spanning multiple places.
6. **World arc:** a major story that reveals the history, culture, ecology, or present tensions of a world.
7. **Universe arc:** a long-term mystery connecting worlds, history, and the larger universe.

The portfolio must mix lengths, tones, genres, and levels of intensity. Avoid making every story a hidden-object puzzle or every resident a quest giver.

A story bible should state its scale, intended duration, entry points, optionality, dependencies, emotional tone, content suitability, and how the learner can re-enter after a break.

## 3. Story canon and continuity

Each world has canon managed through versioned content, not improvised runtime text.

Every narrative fact should have:
- Stable fact/story/entity IDs.
- Canonical statement and allowed uncertainty.
- Source/provenance within the fiction (witness, document, rumour, artifact, observation).
- Reliability: confirmed, disputed, mistaken, unknown, or intentionally ambiguous.
- Who knows it and under what conditions.
- When/where it is true, including world-time constraints if relevant.
- Content version and dependencies.
- Whether learner choices can change it, reveal it, or only change interpretation.

Separate:
- **World canon:** facts that are true regardless of one learner's save.
- **Learner knowledge:** facts the learner has discovered or been told.
- **Learner choices:** decisions and consequences belonging to that learner's story.
- **Character knowledge:** what each character plausibly knows, remembers, suspects, or misunderstands.
- **Presentation:** what a scene currently shows or says.

A character must not know a secret simply because the learner discovered it unless the story establishes how the information is shared.

## 4. Story structure and authoring contract

A story definition should include:
- Stable story ID, title, summary, scale, genre, tone, suitability and content notes.
- World/region/place dependencies and canonical time/calendar context.
- Characters, factions, creatures, and their motivations.
- Entry conditions and multiple possible discovery routes where appropriate.
- Chapters/beats, scenes, clues, evidence, dialogue, choices, and outcomes.
- Prerequisite facts and optional branches.
- State transitions and durable consequences.
- Failure, retreat, pause, skip, and re-entry behaviour.
- Recap and journal/archive records.
- Localization, language level, cultural review, captions, and audio requirements.
- Replayability, repeatable moments, and one-time outcomes.
- Content version, migration rules, and retirement policy.

Story logic should be data-authored and testable. Presentation components should not own the story state machine.

## 5. Mysteries and investigations

Mysteries should reward observation, reasoning, interpretation, and curiosity—not arbitrary tapping or guessing a hidden answer.

A mystery can include:
- A question that creates curiosity.
- Initial signs: unusual sound, changed object, missing person/item, strange behaviour, environmental inconsistency, or conflicting account.
- Evidence with provenance and reliability.
- Leads that can be discovered in different orders.
- Connections between clues.
- Alternative interpretations and plausible red herrings.
- Character perspectives and motives.
- A reveal that recontextualizes earlier evidence.
- Consequences or a new question that opens the next arc.

### Clue contract

Each clue defines:
- Stable ID and story ID.
- Physical/digital source and location.
- What is directly observable versus inferred.
- Prerequisites and discovery methods.
- Who can perceive or understand it.
- Evidence reliability and provenance.
- Connections to other clues and hypotheses.
- Whether it is missable, recoverable, or repeatable.
- Learner knowledge record and recap representation.

Do not make a critical clue permanently missable because the learner walked past a scene once. Provide alternative discovery paths or a recoverable trace, unless missability is an explicit and fair narrative choice.

### Mystery fairness

- Establish the central question clearly enough for the learner to care.
- Do not conceal required evidence behind unrelated language proficiency.
- Give enough evidence to support the solution.
- Make red herrings fair and explainable.
- Do not require pixel-perfect taps or inaccessible visual details.
- Permit hint levels that clarify observation without spoiling the entire solution.
- Preserve mystery after a break with a concise recap and evidence board.

## 6. Choices and consequences

Choices should express meaningful preference, judgement, curiosity, kindness, courage, caution, humour, or priorities. They should not be cosmetic buttons that always lead to the same outcome.

Choice design should declare:
- What the learner understands at the moment of choice.
- What is intentionally uncertain.
- Immediate and delayed consequences.
- Whether the choice is reversible.
- Whether it affects world canon, learner-specific narrative, a relationship, access, or only dialogue.
- Whether a later scene acknowledges it.
- Whether alternate outcomes converge and why.
- Whether the choice can be replayed or reset.

Avoid morality meters and hidden numeric relationship scores as substitutes for authored consequence. A character may remember an important decision, but not every ordinary answer should become a permanent personality judgement.

Never punish the learner for choosing a less optimal dialogue option in a language-learning interaction. Language mistakes are learning evidence, not moral failures.

## 7. Resident stories and independent character lives

Residents need more than schedules and dialogue prompts. Each recurring character should have:
- Their own motives, responsibilities, relationships, interests, fears, skills, and boundaries.
- Knowledge and memory that reflect their actual experiences.
- Commitments and ongoing work beyond the learner.
- Personal story threads and optional invitations.
- Changes that can occur while the learner is elsewhere, within bounded simulation rules.
- Reasons to be in a location and plausible reactions to weather, events, and other people.
- A distinct voice and performance identity.

Resident stories must not all resolve through the learner. The learner may help, observe, decline, misunderstand, return later, or discover the outcome through the world.

Do not simulate every resident continuously at full fidelity. Use authored schedules, event-driven updates, and bounded offline progression from the world simulation model.

## 8. Cassidy's narrative role

Cassidy is a human character with her own life, not a quest interface or a universal narrator.

She may:
- Have independent adventures, plans, friendships, obligations, discoveries, and secrets.
- Invite the learner into something without making the learner responsible for her wellbeing.
- Tell stories, share observations, disagree, make mistakes, or choose not to explain.
- Appear in some stories and be absent from others.
- Remember meaningful shared experiences with provenance and appropriate privacy.
- Change her plans for credible story reasons, not because the learner has been inactive.

She must not:
- Guilt the learner for leaving, declining, or skipping.
- Claim false memories or invent shared history.
- Become lonely, distressed, or dependent as an engagement mechanic.
- Gate all mysteries, locations, or relationships.
- Know information she has not plausibly learned.
- Have every story redirect attention back to herself.

Her canon and performance must follow the Cassidy Character Bible.

## 9. Quests, objectives, and rewards

A quest is one possible structure for an experience, not the universal form of the product.

Use explicit objectives only when they help the learner understand a meaningful goal. Do not convert wandering, listening, reading, conversation, or curiosity into a constant checklist.

If a quest exists, define:
- Narrative purpose and story/experience relationship.
- Objective sequence, optional objectives, and alternative solutions.
- Start/availability/expiry rules and whether expiry is fair.
- Progress evidence and event sources.
- Completion authority and idempotency.
- Pause, abandon, resume, and recovery behaviour.
- Reward or consequence, if any, and why it exists.
- Repeatability and reset policy.

Do not use daily chores, streaks, XP, currency, or reward loops to manufacture story urgency. Never pre-complete seeded quests or ship sample progress as a new learner's history.

## 10. Story memory, journal, and re-entry

Important narrative information must be recoverable.

The learner's journal/archive may hold:
- Stories encountered and current stage.
- Key facts learned, with source and uncertainty.
- Clues discovered and hypotheses formed.
- Choices made and consequences known.
- Letters, artifacts, recordings, photographs, and created keepsakes.
- Character memories that were actually shared.
- Recaps and next meaningful leads.

Journal records are not a transcript of every interaction. Store concise, useful narrative continuity with clear provenance. The learner should be able to correct, hide, or delete personal creations and user-generated material according to archive/privacy policy.

When returning after a long break, offer a gentle recap rather than guilt or an avalanche of missed events. Essential story progress must not expire merely because the learner was absent.

## 11. Narrative events and durable state

Narrative events must be semantic and idempotent. Examples include story discovered/started/beat reached, clue discovered, hypothesis recorded, choice made, character fact shared, story resolved, and recap created.

Each event needs stable ID, learner/world scope, actor, target, causal event, content version, canonical timestamp where relevant, and idempotency key.

Persist the authoritative story state and required consequences before presentation claims completion. Consumers must tolerate retries, offline operation, duplicate delivery, and content-version migration.

Separate story state from quest presentation/progress views, UI component state, cinematic playback, reward economy, resident visual animation, and learning assessment.

A story choice may request consequences in another domain, but each domain owns its own state and validates the request.

## 12. Learning within narrative

Language learning should arise naturally from the world and story:
- Signs, letters, menus, maps, messages, conversations, songs, announcements, clues, and practical situations.
- Optional listening, speaking, reading, and writing opportunities.
- Vocabulary and grammar support appropriate to learner ability.
- Contextual hints and replay.
- Meaningful communication goals.

Narrative progression must not be blocked by an unvalidated pronunciation score or a single exact phrase. Allow meaning-equivalent responses, hints, alternative modalities, and story-preserving fallbacks.

Learning outcomes and evidence are owned by the Learning Design model. Stories should reference learning opportunities without pretending every narrative choice is a language assessment.

## 13. Quality, safety, and cultural review

Every story must be reviewed for canon and continuity, character agency, cultural/geographic/historical/language accuracy, age/audience suitability once policy is defined, stereotypes and harmful tropes, accessibility, localization, fair clue design, choice consequences, privacy, offline re-entry, and narrative coherence across updates.

Use cultural consultants or qualified reviewers for language, traditions, history, and culturally specific representations. Do not treat one real-world city, country, or language community as culturally uniform.

## 14. GoPAL-AI research findings

Selected source files reviewed:
- src/engines/quest/questEngine.ts: quest categories and seeded quests; inspected seed data includes pre-completed sample quests. Completion updates quest state, claims an economy reward, and writes a journey event in sequential side effects.
- src/engines/world/residentStoryEngine.ts: three fixed resident story-thread templates with seeded/waiting/ready/resolved stages; waiting-to-ready uses a five-minute elapsed-time threshold.
- src/engines/world/residentStoryOpportunityEngine.ts: derives resident story opportunity tone from a relationship tier and adds fixed text.
- src/engines/world/worldInvestigationEngine.ts: pure clue prerequisite/collection/reveal/completion state transitions.
- src/engines/world/worldStoryChoiceEngine.ts: small story-node/choice model with history and numeric flags.
- src/engines/world/worldEventDirectorEngine.ts: combines contextual ambient events and opportunities while leaving quests, festivals, inventory, and rewards to other owners.
- src/features/world/data/livingWorldQuestEngine.ts: in-memory quest state map, event-driven objective progress, and timestamp-based start/completion.
- src/features/learning/components/WorldInvestigationBoard.tsx: investigation progress is local component state; remounting loses progress unless a caller persists it.
- src/features/learning/components/WorldStoryChoiceBoard.tsx: story node/history/flags are local component state.
- src/features/world/components/WorldStoryTraceLayer.tsx: polls story threads and renders fixed-position traces for a small set of known thread IDs.

### Recovered strengths
- Stories can exist as resident threads and contextual opportunities.
- Clues can have prerequisites and reveal other clues.
- Story choices can preserve a basic choice history.
- Event direction is separated from quest/reward ownership in one orchestration layer.
- Narrative traces can be expressed spatially through the world.

### Limitations and cautions
- The inspected resident story engine has only a few fixed templates and uses a fixed five-minute waiting threshold, not a rich authored narrative scheduler.
- The story-choice and investigation UI components hold state locally; durable re-entry is not established by those components.
- The generic quest seed contains pre-completed sample progress.
- Quest completion performs sequential persistence, reward, and journey-event side effects; the inspected code does not prove a transactional outbox or crash-safe cross-domain completion.
- The in-memory world quest engine does not by itself establish durable progress or account scoping.
- Story relationship text is derived from broad relationship tiers, which should not replace authored character knowledge and nuanced memory.
- These selected files do not prove a complete world/universe mystery, long-running story arc, fair clue graph, or coherent narrative canon system.

These are selected-source observations, not a full audit of every narrative, quest, or story asset in the reference repository.

## 15. Open decisions

- First world/local stories and the first multi-world mystery arc.
- How many long-running storylines are active in the first release.
- Audience age policy and content-rating approach.
- Branch depth versus authored convergence and replay.
- How the journal represents uncertain, disputed, or conflicting evidence.
- Which resident stories progress offline and what limits apply.
- How learner-created narratives or shared stories are moderated and scoped.
- Whether any quest/reward economy exists and its ethical limits.
- Narrative localization, cultural review, and editorial tooling.
- Story migration and retirement policy across content versions.

---

**Current status:** Narrative scales, story canon, authored structure, mysteries/clues, choices/consequences, resident autonomy, Cassidy boundaries, quests, journal/re-entry, learning integration, durable events, quality review, and open decisions documented as a working specification. Initial story portfolio and canon remain to be authored and approved. No implementation is authorized.
