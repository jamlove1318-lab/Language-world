# Language-world — Learning Design

**Status:** Working specification v0.1; not approved for implementation.  
**Purpose:** Define how language learning works inside the living universe, how progress is evidenced, and how support adapts without reducing the product to a conventional lesson path.  
**Source boundary:** GoPAL-AI is a read-only research archive. Its learning concepts inform requirements only; its code, storage keys, evaluators, engines, UI, and pipelines are not reusable dependencies.

---

## 1. Learning philosophy

The learner should feel that they are using a language to do meaningful things in a world—not repeatedly leaving the world to complete disconnected exercises.

The central learning experience is contextual, human, varied, and cumulative:
- Language appears where it belongs: in conversations, signs, shops, journeys, stories, games, messages, books, public announcements, creative work, and everyday life.
- Learners encounter language in context before, during, and after deliberate practice.
- The product supports different learning modes: guided discovery, focused practice, natural interaction, listening, reading, speaking, writing, reflection, and playful experimentation.
- Mistakes are expected parts of learning, not punishments.
- The learner can choose to explore without studying. Learning opportunities should be available, not compulsory.
- Progress should reflect evidence of growing capability, not time spent, streaks, clicks, or reward accumulation.
- The product must be honest about what it can and cannot measure.

The product is not a replacement for human teachers, formal certification, or real-world immersion unless those claims are separately validated. It should not imply that success in a scripted scenario proves broad fluency.

## 2. Learning experience model

Learning is a set of related but distinct layers. They should cooperate without becoming one monolithic lesson engine.

### 2.1 Encounter
The learner meets language naturally in a place, story, activity, object, conversation, announcement, or environmental detail. Encounters can be optional and low-pressure.

### 2.2 Understand
The learner can inspect meaning, context, speaker intent, vocabulary, grammar, register, cultural notes, and examples. Explanations should answer why a phrase fits this situation, not merely provide a translation.

### 2.3 Practise
The learner can rehearse through listening, recognition, retrieval, guided construction, writing, speaking, roleplay, games, or repeated exposure. Practice should vary format and context while preserving the target skill.

### 2.4 Use
The learner applies language to achieve a meaningful outcome: order something, ask a question, understand an announcement, help a resident, interpret a clue, write a message, or continue a conversation.

### 2.5 Reflect and revisit
The learner can review what they encountered, understand feedback, revisit a phrase or skill, and see how capability develops over time. Review should be timely and useful, not a daily obligation.

## 3. Capability model: skills are not one mastery number

Do not represent language ability as one global percentage or a single scenario score. Track separate dimensions with appropriate evidence and confidence.

### Core skill dimensions
- Listening comprehension.
- Spoken interaction and response construction.
- Pronunciation/phonological production, only where measured with suitable evidence.
- Reading comprehension.
- Writing and written production.
- Vocabulary knowledge and retrieval.
- Grammar and sentence construction.
- Pragmatic competence: politeness, register, intent, turn-taking, repair, and appropriateness.
- Discourse and conversation: connecting ideas, maintaining context, clarifying, and responding across turns.
- Cultural/contextual interpretation, without reducing culture to trivia.

### Evidence dimensions
For each skill or learning objective, distinguish:
- Exposure: encountered the language/content.
- Recognition: identified or understood it with support.
- Retrieval: recalled it without seeing the answer.
- Guided production: produced a response with scaffolding.
- Independent production: produced a suitable response with limited support.
- Transfer: used the capability in a new context or scenario.
- Retention: demonstrated the capability again after a meaningful delay.
- Confidence: how strong the evidence is, not how confident the learner says they feel.
- Support dependence: what hints, examples, translations, or prompts were needed.

A capability record should include objective/skill ID, language and variety, proficiency assumptions, evidence type, attempt context, result, support used, confidence, timestamp, source experience, and review status. Keep the raw event/evidence separate from any derived summary.

Do not promote a learner to “independent” merely because they succeeded a fixed number of times in the same repeated prompt. Independence needs varied evidence and transfer.

## 4. Learning objective and content design

Every authored learning objective must specify:
1. Language, script, region/variety, register, and context.
2. Target capability and observable action.
3. Prerequisites and assumed prior knowledge.
4. Example language, acceptable variants, and common learner difficulties.
5. How meaning and intent are established.
6. What counts as adequate evidence and what cannot be inferred.
7. Feedback, hint, retry, and review design.
8. Accessibility and alternative input.
9. Cultural/language review status.
10. How the objective connects to other experiences without forcing a linear path.

Avoid teaching decontextualised fragments without showing when and why someone would use them. A phrase may have multiple valid forms depending on relationship, region, register, situation, and tone. Content must not treat one scripted answer as the only possible natural response unless the task is genuinely constrained.

## 5. Adaptive support

Adapt support to evidence, not to a single opaque mastery score.

Possible support levels:
- **Demonstration:** show meaning, context, pronunciation audio where available, and a worked example.
- **Guided:** break the task into smaller steps and provide selectable or highlighted cues.
- **Supported:** provide a vocabulary bank, partial sentence, transcript, or limited choices.
- **Open practice:** let the learner respond without a prewritten answer, with optional hints.
- **Natural interaction:** remove most scaffolding and let the learner handle a realistic exchange.
- **Transfer/stretch:** present a new context, speaker intention, or variation that tests flexible use.

Adaptation may consider:
- Evidence by skill and objective.
- Recency and spacing since last practice.
- Hint and translation dependence.
- Repeated error patterns and partial understanding.
- Variety of contexts and transfer evidence.
- Learner-selected difficulty, goals, and accessibility preferences.
- Session intent and available time.

Guardrails:
- Never infer a fixed ability from one attempt.
- Do not silently remove useful content or lower quality.
- Explain why support is being offered when it helps the learner.
- Let learners request more or less support.
- Do not make advanced learners repeat beginner content without reason.
- Avoid creating a permanently narrow profile from early mistakes.
- Treat uncertain or conflicting evidence as uncertain.

## 6. Feedback and evaluation

Feedback should be specific, constructive, and tied to the task's real communicative goal.

A useful response can distinguish:
- Meaning understood.
- Communicative intent achieved.
- Grammatical or lexical fit.
- Register and politeness.
- Comprehensibility.
- Pronunciation evidence, if actually measured.
- Missing information or a useful next improvement.

Do not collapse all these into one score. A response can communicate successfully while containing a small grammar error; a phrase can match a reference string while being inappropriate for the social context.

### Evaluation methods and limits

| Method | What it can support | What it cannot establish alone |
|---|---|---|
| Multiple choice | Recognition among presented options | Independent recall or production |
| Word/phrase matching | Presence of expected content or a close reference match | Full semantic understanding or naturalness |
| Word-bank construction | Ordering/selection skill within the supplied set | Independent writing |
| Typed free response | Written production evidence, if evaluated appropriately | Pronunciation or spoken fluency |
| Audio playback/shadowing | Listening exposure and rehearsal | Independent speech assessment |
| Microphone recording | Captured audio exists | Correctness, intelligibility, or pronunciation without analysis |
| Speech-to-text transcript | A recognizer's interpretation of speech | A ground-truth transcript or complete pronunciation diagnosis |
| Validated speech analysis | Specific measured phonetic/phonological features within its limits | Overall fluency, communicative competence, or accent quality |
| Multi-turn scenario | Contextual interaction evidence within that scenario | Broad real-world conversational ability |

The product must label capabilities honestly. If it has no speech recognizer, it must not claim to assess speaking. If it only receives a transcript, it must not claim to have heard or evaluated pronunciation. If an ASR system is used, disclose that recognition can be wrong and allow correction or alternate assessment.

### Feedback principles
- Show what worked before explaining what to improve.
- Explain the meaning and context behind corrections.
- Accept valid alternatives where the content allows them.
- Distinguish a language error from a speech-recognition or input error.
- Avoid humiliating, sarcastic, or infantilising feedback.
- Allow replay, slower playback, transcript, examples, and retry.
- Preserve the learner's intended meaning where possible.
- Never present a heuristic match as an authoritative linguistic judgement.

## 7. Listening and audio learning

Listening must be a real learning mode, not merely a sound file attached to a multiple-choice question.

Support a progression such as:
- Listen for the overall situation and speaker intent.
- Listen again for key information.
- Replay a phrase or segment.
- Adjust playback speed where appropriate without distorting meaning beyond usefulness.
- View transcript, translation, vocabulary, or speaker context according to chosen support.
- Distinguish voices, announcements, ambient sound, and meaningful audio clues.
- Respond through selection, navigation, summary, or a spoken/written answer.

Audio content must identify language, speaker, region/variety where relevant, context, transcript availability, and rights/provenance. Provide captions/transcripts for accessibility. Do not make a task impossible for someone who cannot hear or use audio; provide an equivalent text or visual route where feasible.

## 8. Speaking, pronunciation, and conversation

Separate the following capabilities in product design and user-facing language:
1. Hearing a model pronunciation.
2. Repeating or shadowing audio for practice.
3. Recording a voice sample.
4. Transcribing speech to text.
5. Evaluating spoken meaning/intent.
6. Evaluating pronunciation features.
7. Supporting multi-turn spoken conversation.

These are different capabilities and may depend on different providers, permissions, device conditions, and network access. A microphone permission is not evidence of speech recognition. A transcript is not pronunciation scoring. A conversational model response is not proof of language accuracy.

Conversation design should include:
- Clear role and situation.
- Speaker intent and relationship.
- Turn-taking and natural pauses.
- Clarification and repair strategies.
- Multiple valid ways to respond.
- Contextual register and politeness.
- Ability to ask for help or repeat.
- A graceful path when input is not understood.
- No requirement to speak aloud if the learner prefers text.

## 9. Reading and writing

Reading content should vary across signs, menus, maps, messages, letters, stories, books, forms, instructions, and public announcements. Teach learners to infer meaning from context while allowing lookup and explanation.

Writing can include short messages, replies, descriptions, notes, letters, journals, captions, and creative work. Evaluate according to the task: meaning, completeness, clarity, grammar, vocabulary, register, and audience. Avoid forcing every response into one canonical phrase. Preserve user-created writing as private by default and follow the creation/archive privacy contract.

For languages with different scripts or writing systems, specify:
- Script and orthographic conventions.
- Input method support.
- Reading aids and transliteration policy.
- Font and glyph coverage.
- Text direction and layout needs.
- Handwriting support only if the product can genuinely capture/evaluate it.
- Accessibility for script learning and visual complexity.

## 10. Vocabulary, grammar, and retrieval

Vocabulary records should include lemma/word form, meaning, pronunciation/audio reference where available, script/transliteration, part of speech, usage, collocations, register, region, example context, and source provenance.

Grammar learning should connect patterns to meaning and communicative purpose. Avoid teaching rules as arbitrary puzzles detached from use. Learners should see examples, contrast, practise, and apply patterns in new contexts.

Retrieval practice should:
- Revisit items after useful intervals rather than on a rigid universal schedule.
- Consider recent evidence, difficulty, confidence, and context variety.
- Mix recognition and production.
- Avoid overexposure to the same exact prompt.
- Let the learner defer or disable review reminders.
- Not punish missed sessions or create streak loss.

The detailed scheduling algorithm is an implementation decision for later, after learning requirements and privacy rules are approved.

## 11. Cultural and pragmatic competence

Language is inseparable from context, but culture must not become a set of simplistic facts or stereotypes.

Experiences should help learners understand:
- How relationships affect register and word choice.
- How requests, refusals, thanks, apologies, and invitations vary by context.
- Regional language variation and contemporary usage.
- Cultural practices as lived, diverse, and changing.
- When a phrase is literal, idiomatic, humorous, formal, or sensitive.
- How to ask for clarification respectfully when unsure.

Real-world cultural claims need traceable sources and review by qualified language/cultural reviewers. Fictional world customs must be clearly authored as fiction, not presented as facts about a real community.

## 12. Learning within the world

- Learning opportunities should arise naturally from places and activities.
- Residents may support language practice, but are not the only teachers or interaction mode.
- Real places should support believable everyday language and culture.
- Fictional places can host imaginative practice spaces and games.
- The same learning objective may appear in several contexts to support transfer.
- World changes must follow a meaningful outcome, not simply a score threshold.
- A learner may leave an unfinished activity and return without losing the place or narrative.
- Cassidy can support, model, reflect, or simply accompany; she is not a compulsory tutor in every experience.
- Learning feedback must not break cinematic or narrative flow unnecessarily.

## 13. Progress, motivation, and learner control

Progress should be understandable without becoming a pressure system.

Show:
- What the learner has encountered and practised.
- Which capabilities have stronger or weaker evidence.
- What they can currently do in familiar contexts.
- Where evidence is incomplete or uncertain.
- Which experiences can help them practise next.
- How to revisit content and manage goals.

Avoid:
- Mandatory daily streaks.
- Punitive hearts/lives.
- Artificial scarcity or expiring learning access.
- Leaderboards as a core learning driver.
- Rewarding speed over comprehension by default.
- Claiming mastery from repeated identical tasks.
- Emotional pressure from Cassidy or residents.
- Treating time in app as learning success.

The learner should control practice reminders, microphone use, audio playback, speech processing, difficulty, support level, and review preferences.

## 14. Persistence, privacy, and data boundaries

Learning records are sensitive personal data in practice even when they are not formally classified as special-category data. Collect only what is needed and explain why.

Requirements:
- Every learner record is scoped to an explicit stable learner/account identity.
- Never use one global storage key for multiple learners.
- Anonymous/local mode has a clear identity and upgrade/merge policy.
- Account switching cannot expose another learner's progress, voice recordings, writing, or archive.
- Separate raw attempts/evidence from derived capability summaries.
- Store only necessary audio; default to no long-term voice retention unless explicitly needed and clearly consented to.
- Provide clear controls for export, correction, deletion, and account closure.
- Define offline behaviour, sync conflicts, retries, deduplication, and schema migration.
- Learning completion, world consequence, and personal memory must be idempotent and recoverable across interrupted writes.
- Analytics must not collect unnecessary raw language, audio, or private content.

No vendor, speech model, backend, or retention period is selected by this document.

## 15. Accessibility and inclusion

- Captions, transcripts, repeat controls, speaker labels, and adjustable playback.
- Text size, contrast, line spacing, and script-specific font coverage.
- Alternative text input where speech is optional.
- Alternative visual/text route for audio tasks where feasible.
- No reliance on colour alone or rapid response for core learning.
- Support reduced motion and interruption recovery.
- Avoid assuming one dialect, accent, educational background, or literacy level.
- Do not penalise disability-related alternative input.
- Make hints and explanations available without stigma.

## 16. Research findings from GoPAL-AI

Selected source files reviewed:
- `docs/world-learning-variety-blueprint.md` and `docs/world-learning-variety-implementation.md`: contextual real-world learning, fictional learning spaces, reusable mechanics, and a desire to avoid card-only activity presentation.
- `src/engines/learning/contextualLanguageLearningEngine.ts`: place-based prompts for vocabulary, listening, speaking, reading, grammar, and writing.
- `adaptiveConversationEngine.ts`: conversation support derived from a single numeric mastery value.
- `languageCapabilityEngine.ts`: scenario/skill attempts and successes plus word/phrase counters; the inspected implementation uses one global AsyncStorage key, not explicit learner scoping.
- `learningEvaluationEngine.ts`: expected-concept and sample-response matching heuristics; useful as a narrow text-evaluation baseline, not proof of semantic or spoken-language evaluation.
- `learningNeedEngine.ts`: prioritises scenarios using scenario and skill capability states.
- `worldLearningScenarioEngine.ts`: authored place-specific scenarios with vocabulary, response options, cultural notes, world changes, and follow-ups.
- `worldLearningResponseEngine.ts` and `wordBankAnswerEngine.ts`: exact/approximate string matching and word-bank construction.
- `worldLearningFlowEngine.ts` and `worldLearningOutcomeEngine.ts`: multi-domain side effects across capability, memory/integration, relationship, Cassidy, and world consequences; inspected flow performs sequential side effects and uses local completion/in-flight guards.

### Recovered strengths
- Learning attached to believable places and meaningful interactions.
- Multiple skills beyond vocabulary recall.
- Scenarios include context, target language, vocabulary, cultural notes, follow-ups, and possible world changes.
- Adaptive support and learning-need prioritisation are recognised.
- Learning can have narrative/world continuity rather than ending at a score screen.

### Limitations and cautions
- A single mastery scalar is too coarse for multidimensional language ability.
- Attempt/success counts and fixed thresholds do not prove transfer or long-term retention.
- A global capability key risks cross-learner leakage on a shared device.
- String matching and sample-response matching are not robust semantic assessment.
- A generated or stored transcript is not pronunciation evidence.
- Multi-service sequential side effects can leave partial outcomes if interrupted.
- The inspected files do not establish a complete spaced-repetition system, robust speech evaluation, dialect coverage, account isolation, or validated learning gains.

These findings are selected-source observations, not a full audit of every learning feature or a claim about the performance of an external AI/speech provider.

## 17. Open decisions

- Initial languages, regions, dialects, scripts, and proficiency range.
- Intended age range and learning support model.
- Curriculum alignment (if any) and whether CEFR or another framework is useful.
- Which speaking/speech capabilities are in scope for first release.
- Whether any audio is processed on-device or by a service.
- Voice/audio retention and consent model.
- Offline learning and sync guarantees.
- Qualified language/cultural review process.
- Accessibility standard and learner testing plan.
- How learning progress is explained without misleading scores.

---

**Current status:** Learning philosophy, capability/evidence model, adaptation, evaluation, speech honesty, contextual learning, persistence/privacy, accessibility, and review requirements documented as a working specification. Language scope, assessment validation, and implementation remain open. No implementation is authorized.


## 18. Fixed curriculum sequence with varied activity rhythm

**Product-owner requirement:** the core language-learning progression follows a fixed, authored sequence. It should not be an unordered feed of interchangeable activities. Curriculum authors define the next core experience, prerequisites, review timing, learning outcomes, and evidence expected.

The sequence must vary its format to sustain interest and support transfer. A representative cycle may introduce language through meeting a new character, develop context through a story, reinforce listening through an audio lesson, check understanding with a quiz, apply clues in a puzzle, practise through a game, and return to a resident interaction where the learner uses the language more naturally. A new cycle then introduces different characters, situations, language goals, and activity combinations. This is a rhythm example, not a fixed seven-item formula.

The curriculum path is fixed; the learner's whole world is not. Learners may pause, leave, review, retry, take breaks, or choose optional world activities without losing progress or being shamed. Optional exploration does not silently reorder the core path. Placement, skip, remediation, and accessibility policies must be explicit, evidence-informed, and reviewed. The path should avoid monotony by varying social/narrative/audio/game/puzzle/assessment modalities, emotional tone, duration, context, and cognitive demand.

**Acceptance checks:**
- The next core learning experience is authored and explainable.
- The sequence alternates formats intentionally and revisits characters/language in new contexts.
- Review and spaced recall are built into the path rather than left to arbitrary repetition.
- Optional world life remains available without becoming a hidden prerequisite.
- Learners can pause, resume, review, and receive accommodations without losing their place.
- Mistakes and retries do not create shame or punitive progression loss.
