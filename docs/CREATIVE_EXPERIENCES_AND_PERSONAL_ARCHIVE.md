# Creative Experiences and Personal Archive Specification

**Status:** Working draft v0.1 — research-informed, not approved for implementation  
**Project:** Language-world  
**Reference boundary:** GoPAL-AI is read-only research. Its code, UI, schemas, templates, and asset pipeline are not implementation dependencies.

## 1. Product promise

The learner should be able to make, collect, revisit, develop, and share (when they choose) meaningful things that emerge from living in the worlds. The archive is not a trophy cabinet, a reward screen, or a dump of generated text. It is a personal creative space and a record of experiences that the learner considers worth keeping.

Creative experiences should:
- feel native to the world and its cultures rather than generic form templates;
- support personal expression, learning, play, storytelling, and collecting;
- preserve editable source material, not only flattened previews;
- remain available across sessions and supported devices;
- be optional and welcoming, never a required chore;
- allow private, local-only, account-synced, or deliberately shared visibility where the feature supports it;
- remain useful even when Cassidy is absent;
- respect the learner's ownership, privacy, and right to revise or delete.

The archive is a place to return to: a shelf of postcards, a field journal, a phrase collection, a comic studio, a curiosity cabinet, a personal museum, or letters to one's future self. These are distinct experiences with shared infrastructure, not one generic editor with different labels.

## 2. Experience families

The following are product families, not a promise that every item ships in the first release.

### 2.1 Personal journal and Journey Book
A learner-authored and system-assisted chronicle of experiences:
- dated entries written by the learner;
- optional prompts to reflect on a discovery, conversation, place, story, or challenge;
- selected world events and milestones the learner chooses to keep;
- before/after language samples with context and evidence, not simplistic scores;
- sketches, photographs or permitted media, collected objects, maps, and links to related stories;
- searchable, filterable timeline and themed collections;
- private notes that are not automatically exposed to characters or AI services.

System-generated entries must be clearly attributed as generated/suggested and editable before becoming part of the personal journal. Do not silently turn every action, mistake, or conversation into a permanent autobiographical claim.

### 2.2 Postcards and travel keepsakes
Postcards should be composed as designed objects tied to a real in-world place or journey:
- choose a scene or location the learner has actually visited or a clearly labelled authored scene;
- choose from culturally and visually appropriate layouts;
- add a title, message, language practice, date, recipient (optional), and personal signature;
- include optional vocabulary notes, pronunciation audio, or a short caption;
- save editable source and a rendered print/share version;
- create a private collection or deliberately send/share through an explicit action.

A postcard must not claim the learner visited a location they did not visit. Generated scene imagery must be identified as an illustration when it is not a captured world view.

### 2.3 Phrasebook and language collections
A personal phrasebook is a usable learning tool, not merely a decorative card:
- save phrases from lessons, conversations, stories, or manual entry;
- retain language, script, transliteration (if useful), meaning, context, register, speaker/source, audio provenance, and examples;
- group by learner-created collections, topic, world, situation, or grammar pattern;
- add personal mnemonic, note, and example;
- practice through listening, recall, dialogue, and spaced review where appropriate;
- track the source and date of edits so corrected translations do not silently overwrite the learner's own note;
- distinguish verified authored translations from machine suggestions and learner-entered content.

Do not imply that one phrase is universally appropriate across dialect, region, age, politeness, or social context. Show register/context where it materially changes meaning.

### 2.4 Comics, storyboards, and dialogue scenes
Creative storytelling should let learners compose short scenes using:
- panels, characters, locations, backgrounds, props, speech bubbles, narration, and sound/effect cues;
- editable dialogue in target language, translation, transliteration, and optional pronunciation support;
- original learner-authored characters and text;
- reusable scene layouts without locking the learner to pre-written story outcomes;
- panel ordering, revisions, alternate versions, and preview;
- optional export as image/PDF/video only where the required render pipeline is available.

Use of Cassidy, residents, licensed performers, or recognizable authored characters must follow canon and content rights. Learners can create fan-like scenes within the product only under a clearly defined permitted-use policy; they cannot redefine canonical character facts through an editable comic.

### 2.5 Memory boards and collections
A board is a flexible arrangement of meaningful items:
- learner-selected photos/illustrations, postcards, phrases, journal excerpts, maps, discoveries, story clues, and creations;
- freeform or guided layouts, captions, labels, grouping, and ordering;
- links back to source objects and their context;
- multiple boards with clear privacy and ownership;
- edit, duplicate, archive, export, and delete.

Boards should not be auto-filled with private conversations or inferred emotional facts. The learner chooses what belongs.

### 2.6 World discoveries, cultural artifacts, and museum exhibits
Collecting should represent curiosity and understanding, not a compulsory checklist:
- discoveries can be recorded as a place, object, story, natural phenomenon, craft, food, custom, language insight, or historical clue;
- a collectible should have an authored cultural/ecological context and a source/provenance record;
- the learner can revisit an exhibit, hear or read its story, inspect related places, and add a personal observation;
- collections may form a curated museum, cabinet, field guide, or world-specific archive;
- sensitive cultural objects and sacred/ceremonial material require expert review and may not be appropriate collectibles.

Avoid presenting living cultures as loot, exotic curiosities, or interchangeable decorative skins. Some experiences should be observed, learned about, or respectfully participated in rather than collected.

### 2.7 Time capsules and future letters
A learner may write a private message, goal, reflection, or question for their future self:
- choose a date or meaningful milestone unlock condition;
- preview the exact unlock rule and time zone;
- edit or cancel before sealing if the feature's design allows;
- preserve a sealed message without letting Cassidy or other characters read it by default;
- unlock when the declared condition is genuinely met;
- explain device/offline clock uncertainty and account migration behavior;
- allow deletion at any time, with clear explanation if a sealed capsule is intended to be immutable only as a playful design metaphor.

A time capsule must never become a coercive promise, guilt device, or artificial attendance reward. No demo/administrator bypass may appear in the learner-facing product.

### 2.8 Conversation and activity archive
A conversation archive may preserve selected sessions for learning and personal reference:
- explicit session title, date, world/place, participants, language, and learning context;
- separate user turns, character turns, system prompts, corrections, translations, and generated feedback;
- optional saved vocabulary and user-selected highlights;
- replay/listen only when audio is actually retained or can be regenerated with disclosure;
- search and filter, continue practice from a selected excerpt, and delete/export;
- clear distinction between a faithful transcript, a summarized recap, and reconstructed/generated material.

Do not silently archive every voice recording or send archived conversation text to character memory. The learner controls retention and whether a selected excerpt can be used as a personal memory.

### 2.9 Other future creative experiences
The shared platform may later support recipe notebooks, travel maps, nature field guides, music/rhythm compositions, craft journals, photo stories, personal museums, collaborative projects, and in-world exhibitions. Each requires its own experience design, cultural review, data model, accessibility plan, and rights review. Do not add them merely to inflate a feature list.

## 3. A coherent archive, not one overloaded screen

The archive should feel like a set of connected places and tools:
- **Journey Book:** chronology and reflection.
- **Studio:** create and edit original work.
- **Phrasebook:** collect and practice language.
- **Museum/Cabinet:** curate discoveries and artifacts.
- **Collections/Boards:** arrange selected items around a theme.
- **Capsules/Letters:** private future-facing messages.
- **Conversation Archive:** revisit selected learning interactions.

The product may present these as rooms, shelves, books, desks, or world objects, but navigation must remain clear and accessible. Avoid burying essential edit/delete/privacy actions inside decorative metaphors.

A shared archive index can connect objects across experiences. It must not erase their distinct workflows or turn all content into the same generic card type.

## 4. Canonical creative-object model

Every durable user-created object must have, as appropriate:

- stable opaque object ID;
- explicit learner owner ID;
- object type and schema version;
- title and optional description;
- created, updated, and last-opened timestamps;
- source content in an editable structured representation;
- version/revision history or a deliberate single-version policy;
- world/place/language references where relevant;
- links to source events, learning sessions, story nodes, or authored content;
- media references with ownership, rights, and lifecycle metadata;
- tags and learner-defined collections;
- visibility and sharing state;
- sync state and conflict status;
- archive/trash/deletion state;
- export representation and renderer compatibility metadata.

Not every object needs every field, but ownership, stable identity, schema version, and lifecycle state are mandatory for durable personal objects.

### 4.1 Structured source versus rendered output

Keep source and presentation separate:
- source document: semantic text, panels, blocks, positions, references, annotations, language metadata;
- presentation: theme, typography, layout, illustration, page dimensions, animation and rendering rules;
- generated output: preview image, print file, share image, audio, or other derivative.

The source document is authoritative. Rendered outputs are reproducible derivatives where feasible. If a renderer changes, old creations should remain interpretable through versioned rendering rules or a stable export snapshot.

Never use a screenshot or flattened image as the only copy of an editable comic, phrasebook, board, or journal entry.

### 4.2 Versioning and revision

Define whether each object supports:
- automatic draft saves;
- explicit save/publish;
- undo/redo during editing;
- revision history;
- restore previous version;
- duplicate/fork;
- archive and trash;
- permanent deletion.

Autosave must communicate whether changes are local, synced, or pending. Concurrent edits must produce recoverable versions, not silent overwrite. For initial releases, a simpler revision model is acceptable if it protects the source and offers a conflict copy.

## 5. Asset and media handling

Media types may include world screenshots, authored illustrations, learner uploads, voice clips, generated audio, thumbnails, comic panel art, and export files.

Each media object needs:
- stable media ID and owning learner or product content owner;
- MIME type, dimensions/duration, byte size, checksum;
- source/provenance and rights/consent status;
- creation/import time;
- storage location and availability state;
- thumbnail/derivative references;
- access policy and expiration for signed links;
- moderation/safety status where applicable;
- deletion and backup lifecycle.

Requirements:
- validate file types and size before processing;
- use resumable uploads and checksum verification when remote;
- make offline drafts safe and visible;
- generate derivatives asynchronously and idempotently;
- avoid exposing private media through public URLs;
- allow the learner to remove media without corrupting the surrounding creation;
- define cache eviction separately from source deletion;
- clean orphaned derivatives without deleting referenced originals;
- preserve media in export or include an explicit manifest of unavailable files;
- never treat a generated preview as evidence of an actual learner visit.

Media storage and deletion must follow the Persistence, Privacy, and Synchronization Specification.

## 6. Discovery and archive event model

Creation and collection events should reference domain facts rather than duplicate or invent them. Examples:
- learner creates a postcard from a visited location;
- learner saves a phrase from a conversation turn;
- learner pins a story clue to a board;
- learner adds a discovered artifact to a museum;
- learner writes a journal reflection about a journey;
- learner seals a private future letter.

Every event needs stable identity, learner scope, causal source, timestamp semantics, and idempotency. A generated suggestion is not a learner-authored object until accepted. A discovered world artifact is not automatically a personal memory. A completed activity is not automatically permission to retain its transcript.

Archive indexes and search data are derived from source objects and must be rebuildable. Deleting a source object must remove or update dependent previews, indexes, board references, and share links according to declared policy.

## 7. Privacy, sharing, and ownership

Default to private. Sharing is a separate intentional action, never a side effect of creation.

Define visibility states per feature:
- private on this device;
- private and synced to the learner's account;
- shared with named collaborators (only if collaboration exists);
- published/shared by link (only if explicitly supported);
- deleted/trashed.

Before sharing, show exactly what will be shared, with whom, and whether a link is public or revocable. Never include private notes, transcripts, hidden metadata, or location details unless the learner explicitly selects them.

The learner owns their original text, notes, arrangements, and uploaded media subject to applicable terms. Product-authored world assets, character designs, music, fonts, and templates remain under their respective licenses. Export must not imply the learner owns underlying licensed assets.

Do not use personal creations to train external models or public models without a separate, informed opt-in and clear scope. Do not use private creations for promotional material without explicit permission.

## 8. AI-assisted creation boundaries

AI may help brainstorm, translate, suggest layouts, explain a phrase, or offer optional prompts, but:
- label generated content and preserve provenance;
- distinguish model suggestions from verified language/cultural guidance;
- let the learner edit, reject, or delete suggestions;
- do not overwrite original text or canonical world lore;
- avoid sending unrelated personal memories, private transcripts, or media to a model;
- explain when content is processed by an external provider;
- provide age-appropriate safety and moderation;
- avoid falsely attributing AI-generated words to Cassidy or residents as actual dialogue/memory;
- do not invent a learner's experiences, achievements, visits, or personal history.

AI assistance is optional. The creative experience must remain useful without it.

## 9. Cultural and editorial integrity

Every authored template, artifact, cultural explanation, translation, and world-linked creative prompt must have:
- source and author/editor provenance;
- language and locale;
- cultural review status;
- factual confidence and update date where appropriate;
- licensing/rights status for media;
- sensitivity notes and restrictions;
- a correction process.

Use qualified native-language and cultural reviewers for high-impact content. Avoid stereotypes, flattening regional differences, sacred-object gamification, inaccurate transliteration, and treating a single fictional resident as spokesperson for an entire culture.

Learner-generated content is personal expression and need not pass the same editorial review as official canon, but public sharing surfaces need moderation and safety rules.

## 10. Accessibility and usability

- Support screen readers with semantic labels and logical reading order.
- Provide keyboard/controller navigation where relevant.
- Support text scaling, contrast, reduced motion, captions, transcripts, and non-audio alternatives.
- Do not rely on color or visual arrangement alone to communicate object state.
- Make creation workflows recoverable after interruption.
- Provide undo for destructive edits where practical.
- Avoid precision gestures as the only way to arrange a board or comic.
- Ensure exported content remains legible and does not crop scripts or diacritics.
- Support right-to-left text and mixed-script layout if target languages require it.
- Keep privacy, export, duplicate, and delete controls discoverable.

## 11. Product quality principles

1. A small number of deeply considered creative tools is better than many empty templates.
2. Every tool should have a reason to exist in the world and a clear user outcome.
3. Never require creation to progress through the world or maintain a streak.
4. Do not award points for personal disclosure, sharing, or emotional content.
5. Never penalize a learner for not returning to a capsule or journal.
6. No character should guilt the learner about private writing or absence.
7. Empty states should invite, not shame.
8. A learner can keep a quiet, private archive without publishing anything.
9. Content should be findable years later, even if the original world scene or renderer changes.
10. The learner must be able to leave, return, revise, export, or delete without coercion.

## 12. GoPAL-AI reference research: inspected sources

Selected read-only files:
- `src/engines/creation/creationStudio.ts`
- `src/features/journey/screens/JourneyBookScreen.tsx`
- `src/features/journey/screens/MemoryMuseumScreen.tsx`
- `src/features/journey/components/TimeCapsuleModal.tsx`
- `src/features/journey/components/ConversationArchiveModal.tsx`
- selected interfaces and methods in `src/lib/localStore.ts)

### Useful ideas recovered

- Four initial creation types: cultural postcard, phrase card, memory board, and dialogue comic.
- A Journey Book concept with timeline, milestones, cultural artifacts, and before/after learning reflections.
- A Memory Museum grouping postcards, creations, artifacts, and personal memory.
- Time capsules for private messages to a future self.
- Conversation transcripts as material for later listening and practice.
- Links between creations and journey events.

These are useful experience seeds, not proof that the features are complete or durable.

### Limitations observed in selected source

- The CreationStudio creates only four simple text-oriented object types with title, subtitle, content, visual theme, tags, and creation timestamp; no edit/revision/delete lifecycle was observed in that engine.
- Creation creation and journey-event recording are sequential independent writes; failure between them can leave inconsistent history.
- Creation IDs, postcard IDs, and capsule IDs use Date.now()-derived identifiers.
- Postcards are simple records with a location, Cassidy note, and image theme; the inspected model does not establish editable composition or actual image/media ownership.
- Journey Book reads timelines, milestones, artifacts, and knowledge nodes, but this UI does not demonstrate a full learner-authored journal editor.
- The Museum combines several record families in one tabbed screen; its data loading is local and not visibly account-scoped in the component.
- ConversationArchiveModal contains hard-coded sample sessions and dialogue; its “listen” action displays a text toast rather than playing audio.
- The transcript sample includes a score and feedback but does not establish a real persistent transcript, audio provenance, or validated speech assessment.
- TimeCapsuleModal allows an “Inspect / Unlock Early (Demo)” action, which bypasses the intended unlock date.
- Time capsule records store message/date/unlocked/theme but do not express owner scope, privacy controls, revision policy, milestone rules, or reliable clock semantics.
- Several related LocalStore getters use seeded sample defaults; the archive may therefore appear populated before the learner has created or discovered anything.
- The selected local models lack consistent object versioning, structured source documents, media lifecycle, sharing permissions, export, deletion, and recoverable edit history.

These findings are limited to selected files and do not constitute a complete audit of every creative or archive feature. No GoPAL source is copied.

## 13. Recommended product sequencing (not implementation authorization)

A coherent first release should prove the archive foundation before expanding the catalogue:

1. **Personal Journal / Journey Book:** learner-authored entries, optional selected milestones, durable edits, privacy and export.
2. **Phrasebook:** saved phrases with context, source, translation status, personal notes, and useful practice.
3. **Postcards:** world-linked composition with editable source and robust media/export handling.
4. **Collections / Museum:** curate selected discoveries and creations into personal collections.
5. **Conversation Archive:** only after transcript truthfulness, consent, storage, and audio lifecycle are established.
6. **Comics / Storyboards:** after the structured document and rendering pipeline can support panel-based editing.
7. **Time Capsules:** after clock trust, privacy, deletion, and account lifecycle are reliable.

This is a proposed order based on shared foundations and user value, not a locked release plan. The product owner may change priorities.

## 14. Acceptance tests

1. A learner can create, edit, close, reopen, and delete each supported object without losing source content.
2. Every object is isolated to its owner across local storage, cloud, caches, and search.
3. Account switching never exposes the previous learner's archive or media.
4. A generated suggestion remains a draft until the learner accepts it.
5. Export preserves editable source and includes referenced media or a clear omission manifest.
6. A renderer update does not destroy old source documents or make them unreadable without a migration path.
7. Interrupted autosave recovers the last confirmed version and reports unsaved changes honestly.
8. Concurrent edits create a conflict copy or recoverable revision rather than silent overwrite.
9. Deleting a source removes stale thumbnails, indexes, board references, and public links according to policy.
10. Private journal notes and transcripts are not sent to AI or character memory without explicit consent.
11. A postcard accurately represents whether a location was visited or an illustration was generated.
12. Phrasebook entries preserve language, register, context, source, and learner corrections.
13. Cultural artifacts have provenance and reviewed context; sacred/sensitive items are not casually gamified.
14. Conversation archives distinguish actual transcript, summary, generated reconstruction, and available audio.
15. No fake audio playback, fake speech score, or demo unlock bypass is presented as real functionality.
16. Time capsules cannot be unlocked early through a learner-facing debug path.
17. Sharing shows the audience, exact content, and revocation model before publication.
18. Accessibility tests cover screen readers, text scaling, reduced motion, keyboard/controller navigation, and multilingual scripts.
19. A learner can keep a private archive without creating public content or engaging with reward systems.
20. Deletion/export behavior is consistent with the persistence and privacy specification.

## 15. Decisions still open

- Which archive experiences are essential to the first product release.
- Whether the Journey Book is primarily authored by the learner, system-assisted, or both.
- Whether sharing/collaboration exists at launch.
- Supported media types, file limits, and offline storage budgets.
- Revision-history depth and autosave model.
- AI assistance providers and consent model.
- Public/community moderation and creator-rights policy.
- Time-capsule unlock conditions and trusted clock policy.
- Cultural review ownership and correction workflow.
- Whether the archive is represented as a single navigable place, several in-world spaces, or both.

## 16. Approval checklist

- [ ] Experience families and first-release scope reviewed.
- [ ] Canonical creative-object model approved.
- [ ] Editable source and rendering/versioning policy approved.
- [ ] Media ownership and lifecycle approved.
- [ ] Privacy, sharing, AI, and consent rules approved.
- [ ] Cultural review and creator-rights model approved.
- [ ] Accessibility and export requirements approved.
- [ ] Sequencing and acceptance tests reviewed.
- [ ] Product owner approves this specification.

**Implementation remains blocked until the complete Language-world blueprint is reviewed and explicitly approved.**
