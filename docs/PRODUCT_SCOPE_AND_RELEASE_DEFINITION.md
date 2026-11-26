# Product Scope and Release Definition

**Status:** Working draft v0.1 — product-owner review required; not approved for implementation  
**Purpose:** Define the product promise, the distinction between home and learning worlds, the progression/building-upgrade model, the breadth of learning choices, and a coherent first-release boundary.

## 1. Product promise

Language-world is a living universe where people learn languages by participating in meaningful experiences across distinct worlds. It combines exploration, everyday life, characters, stories, games, puzzles, culture, creativity, travel, and structured learning opportunities.

The product is not a linear course disguised as a game. Nor is it only a resident simulator, a chatbot, a collection of quizzes, or a building game. Its identity comes from the way these experiences connect.

**Core promise:** There is always more than one worthwhile way to spend time, learn, discover, create, and make progress in the universe.

The long-term vision is intentionally broad. A first release must be smaller, but it must still feel like a coherent and satisfying version of this promise.

## 2. Emerald Valley is home — not the learning goal

This is an explicit product rule.

Emerald Valley is the learner's home world and familiar place of return. It is not itself a course, a curriculum destination, or the singular goal that the learner must complete before being allowed to learn elsewhere.

Home-world experiences include:
- Everyday conversations with Cassidy and residents.
- Familiar routines, visits, casual encounters, and social situations.
- Exploring neighbourhoods, paths, nature, buildings, interiors, and hidden places.
- Relaxing, observing the environment, enjoying weather, seasons, festivals, and daily life.
- Visiting the market, café, library, station, harbour, gardens, and other locations as they are authored.
- Participating in local stories, games, puzzles, discoveries, creative activities, and optional learning moments.
- Improving and personalizing buildings and locations over time.

Language learning can happen naturally in Emerald Valley, especially through everyday conversation and environmental interaction. However, the learner must not be made to feel that completing Emerald Valley is the learning objective. The valley is a home and a living place, not a gatekeeping course.

Other language worlds are distinct destinations with their own identities. They should provide additional everyday life, culture, stories, locations, activities, and focused learning opportunities. The learner's learning journey is universe-wide, not confined to Emerald Valley.

## 3. Many ways to learn across the universe

Language-world must offer a broad, discoverable catalogue. No single activity type should define the entire learning experience.

### 3.1 Learning and practice formats

The catalogue should include, subject to quality and scope:
- Everyday conversations with Cassidy, residents, and characters.
- Guided conversational scenarios and role-play.
- Listening experiences, audio comprehension, and sound/meaning activities.
- Reading, signs, notes, letters, stories, menus, clues, and practical texts.
- Vocabulary and phrase practice in meaningful contexts.
- Grammar and sentence-pattern discovery.
- Speaking and response practice, with honest capability claims.
- Writing, composition, and creative language use.
- Quizzes and knowledge checks.
- Puzzles, riddles, logic challenges, word puzzles, and clue-based challenges.
- Mini-games across memory, listening, observation, matching, construction, strategy, reflex, and problem-solving.
- Story-based learning, interactive fiction, mysteries, investigations, and branching choices.
- Cultural activities involving food, music, customs, celebrations, everyday etiquette, and local context.
- Review and recall activities that revisit material without making the world feel like a repetitive worksheet.
- Optional focused learning spaces or structured sessions for learners who want a more deliberate study experience.

### 3.2 Locations as learning contexts

Different locations can offer different kinds of experience. Candidate examples include:
- Market: shopping, quantities, preferences, prices, requests, and polite exchanges.
- Café or restaurant: ordering, conversation, listening, menus, and social language.
- Library: reading, research, stories, vocabulary discovery, and puzzles.
- School, studio, or learning centre: focused practice, guided instruction, quizzes, and skill review.
- Theatre or cultural venue: listening, performance, storytelling, and cultural context.
- Workshop: instructions, tools, sequencing, collaboration, and problem-solving.
- Station, port, airport, and transport interiors: directions, announcements, travel conversations, and practical language.
- Parks, gardens, trails, museums, and landmarks: observation, descriptions, discovery, nature vocabulary, and environmental storytelling.
- Dedicated game or challenge venues: curated puzzles, quizzes, competitions against authored challenges, and mini-games.

These are examples, not a final approved location list. Every location should have a reason to exist, a distinct atmosphere, meaningful interactions, accessibility, and a content plan. Not every location needs to be a formal learning facility.

### 3.3 Learning choice and recommendation

Learners should be able to choose an activity or follow a suggestion. The Experience Director may recommend a suitable next experience based on permitted context, but it must not force a single path.

Provide variety and learner controls: choose another activity, continue, practise a skill, explore freely, save for later, or take a break. Recommendations should explain their relevance where useful and must not create guilt, artificial urgency, or hidden pressure.

## 4. Building and location upgrades

**Established by the product owner:** Buildings in Emerald Valley should be upgradable. The upgrade concept also applies to scenarios and the experiences available within locations.

This is a core progression pillar to design, not a decorative afterthought.

### 4.1 What can be upgraded

Depending on the location and its purpose, upgrades may affect:
- Exterior appearance, materials, architectural details, signage, lighting, landscaping, and decoration.
- Interior rooms, layout variants, furniture, equipment, facilities, and interactive objects.
- Functional capacity: additional stations, rooms, activity spaces, collections, exhibits, or services.
- Scenario presentation: visual staging, props, context, environmental details, characters/roles where authored, and available scenario variants.
- Scenario depth: additional dialogue branches, challenge variations, difficulty options, clues, tasks, or replayable situations.
- Location identity: atmosphere, soundscape, seasonal decoration, accessibility features, and quality-of-life improvements.

An upgrade must be reflected in the world in a way the learner can notice. It should not be only a number, a badge, or a hidden stat.

### 4.2 Example upgrade paths

Illustrative examples to develop during world design:
- **Café:** begin as a small, simple café; add seating, a counter, kitchen equipment, menu variety, an outdoor terrace, and new conversation/ordering scenarios.
- **Library:** begin with a modest reading room; add shelves, themed collections, study spaces, an archive room, a puzzle corner, and story/research activities.
- **Market:** add stalls, product variety, signage, facilities, vendors, and more complex shopping and negotiation scenarios.
- **Station or harbour:** improve waiting areas, information boards, passenger facilities, routes, and travel-related scenarios. Transport access itself must still follow world and travel rules.
- **Community or learning venue:** add practice rooms, listening booths, reading spaces, workshops, quiz rooms, puzzle spaces, and guided activities.

These examples do not establish the final building list, costs, levels, art direction, or upgrade sequence.

### 4.3 Scenarios are upgradeable content spaces

A scenario is not merely a static dialogue prompt. It is an authored situation with a location/context, participants or roles, objectives, language opportunities, interaction rules, difficulty/support options, and outcomes.

Scenarios may gain new variants or richer staging as a place develops. For example, a basic café visit might later support a wider menu, more participants, a special event, a reservation problem, or a more demanding conversation. A library might unlock a research mystery, a themed puzzle trail, or a group activity.

Upgrades should expand meaningful options and replay variety, not make the original scenario obsolete or require the learner to grind through harder content. A learner should be able to choose an accessible difficulty and revisit familiar scenarios.

### 4.4 Upgrade architecture and content ownership

Separate:
1. **Building definition:** authored identity, function, upgrade graph, prerequisites, and allowed variants.
2. **Building instance:** the learner's current upgrade state and selected appearance/configuration.
3. **Scenario definition:** authored scenario content, learning objectives, difficulty variants, roles, and outcomes.
4. **Scenario availability/state:** which variants are available, what the learner has discovered, and any local completion state.
5. **Presentation bindings:** replaceable art, audio, animation, props, and scene composition.

Persistent progress must reference stable semantic IDs and versioned upgrade definitions, not filenames, scene nodes, or engine-specific objects. Content updates must migrate or preserve existing learner investments safely.

## 5. Points and progression

**Established direction:** Learners should earn points through learning and use points to upgrade buildings and locations. This creates a visible connection between growing language capability and helping their home world develop.

### 5.1 Earning points

Points may be earned from meaningful participation such as:
- Completing learning activities and quizzes.
- Solving puzzles and investigations.
- Finishing stories or meaningful story milestones.
- Completing conversational scenarios.
- Demonstrating recall or improvement over time.
- Exploring and discovering authored places or content.
- Participating in selected games, cultural activities, and creative challenges.

Award rules must reward genuine participation and learning evidence, not repeated button presses, idle time, meaningless farming, or artificially inflated activity counts. Replaying an activity can remain worthwhile, but the point model should prevent trivial repetition from dominating progression.

### 5.2 Spending points

Points can contribute to building and scenario upgrades, location improvements, and selected expressive/personalization options. The precise economy, costs, reward amounts, upgrade tiers, caps, and earning balance remain open decisions for testing and product-owner approval.

The system should make costs and effects understandable before a learner commits points. Avoid surprise deductions and irreversible purchases without clear confirmation.

### 5.3 Healthy progression principles

- Points are motivational feedback, not a measure of a person's worth or language ability.
- Do not punish absence, missed days, slower learning, mistakes, or breaks.
- Do not make essential accessibility options or core learning capability paywalled behind points.
- Do not require grinding to access the basic universe or to continue a story.
- Avoid streak pressure, expiring rewards, loot-box mechanics, gambling-like randomness, and artificial scarcity.
- Make progress visible through the world changing, new options becoming available, and the learner's own growing capability.
- Provide more than one worthwhile way to earn points so different learner strengths and preferences are respected.
- Ensure upgrade costs and earning rates are balanced through usability and learning-quality tests.
- Keep any future monetization separate from earned progression; no pay-to-win or paid shortcut assumptions.

### 5.4 Separate kinds of progress

Do not collapse all progress into one score. Keep distinct records for:
- Language capability and evidence.
- Completed or discovered experiences.
- Story and investigation state.
- Building/location upgrade ownership.
- Personal creations and collections.
- Travel and world discovery.
- Earned and spent points, including transaction history.

A point balance must never be treated as proof of language mastery.

## 6. Core experience loops

The universe should support several loops that connect without forcing a fixed sequence.

### 6.1 Home-life loop
Return to Emerald Valley → notice changes and available opportunities → talk with Cassidy/residents or explore → participate in everyday life → optionally learn, play, or create → earn appropriate progress → improve a place → leave with continuity.

### 6.2 Learning-choice loop
Choose a skill, interest, or suggested activity → select a suitable format (conversation, game, quiz, puzzle, story, reading, listening, writing, or focused practice) → participate with adaptive support → receive honest feedback → record evidence → earn appropriate points → choose what to do next.

### 6.3 Building-development loop
Discover a location → use its activities → earn points through meaningful participation → review available upgrades → choose an upgrade → see the building/scenario change → discover new options → continue using the location.

### 6.4 Story and discovery loop
Notice a clue or invitation → explore and gather evidence → communicate or solve a challenge → make a meaningful choice → reveal a story outcome → preserve continuity → discover further opportunities.

### 6.5 Travel loop
Choose a destination → prepare → reach station/port/terminal → board train/ship/plane or local transport → experience the journey → arrive in a distinct world → explore its everyday life, learning options, stories, and locations.

## 7. First-release definition: decision framework

The first release should be the smallest complete experience that demonstrates the product's identity, not a miniature version of every long-term feature.

### 7.1 First-release must prove

- A memorable first arrival and introduction to Cassidy.
- Emerald Valley works as a home world, not a linear learning course.
- A believable, navigable, authored home region with several meaningfully different locations.
- Everyday conversations with Cassidy and a small set of residents.
- A real choice of learning formats, including a balanced selection from conversations, games, quizzes, puzzles, stories, and focused practice.
- At least one connected story or discovery experience.
- A functional point-earning and building-upgrade loop, with visible changes in at least a small number of locations.
- Scenario variants or scenario improvements that demonstrate the upgrade concept.
- Durable learner progress and safe return/re-entry.
- Accessibility, privacy, reliable persistence, and acceptable Android performance on the agreed test-device range.

### 7.2 Candidate first-release content slice

A candidate vertical slice for product-owner review:
- One fully authored starter region of Emerald Valley.
- A small cast including Cassidy and a deliberately selected set of residents.
- A few fully developed locations with different purposes (for example, café, market, library, and one outdoor discovery area).
- A curated activity set covering everyday conversation, focused learning, at least one game, quiz, puzzle, and story/investigation.
- One simple but satisfying upgrade path for multiple buildings, with visible exterior/interior changes.
- At least one scenario that gains a meaningful new variant through a location upgrade.
- A modest, transparent points economy tied to quality participation.
- A first travel preview or local transport experience only if it does not compromise the home-world quality bar.

This is a proposal, not an approved feature commitment. The exact number of locations, residents, activities, languages, upgrade tiers, and transport modes must be decided after audience, platform, budget, and production constraints are known.

### 7.3 Later expansion candidates

Potential later releases may add:
- Additional regions and fully distinct language worlds.
- Full inter-world journeys by train, ship, plane, and other context-appropriate transport.
- Larger world-specific stories, mysteries, festivals, and resident arcs.
- More building types, upgrade branches, scenario packs, interiors, and customization.
- Expanded game, quiz, puzzle, creative, cultural, and focused-learning catalogues.
- More advanced speech interaction after capability validation and consent design.
- Larger ecology, more creatures, more dynamic world events, and additional cinematic content.
- Social/shared experiences only after audience, safety, privacy, moderation, and product value are resolved.

### 7.4 Candidate exclusions until separately approved

Do not assume first release includes every world, every one of the 60 recovered game seeds, multiplayer/social systems, a large AI-driven resident population, unrestricted generative stories, a complex crafting/economy/shop system, broad automated pronunciation scoring, every transport type, or a huge open-world map.

These are scope controls, not rejections of the long-term vision.

## 8. Quality and acceptance gates

A first-release scope is acceptable only when:
- Home-world identity is clear in user testing: learners understand Emerald Valley is home, not the only learning goal.
- Learners can find multiple learning formats without being trapped in a single lesson route.
- Activities are genuinely playable and reviewed, not placeholder buttons or catalogue entries.
- Building upgrades produce visible, coherent, persistent changes.
- Scenario upgrades add meaningful options and remain accessible/replayable.
- Point awards are transparent, balanced, and resistant to trivial farming.
- Progress survives app interruption, relaunch, and supported offline conditions.
- The learner can decline recommendations and take breaks without penalty.
- Learning claims match measured evidence.
- Content has cultural, linguistic, accessibility, safety, and production review.
- Performance and asset replacement pass the agreed Android test matrix.

## 9. Decisions still open

Do not invent answers to these questions:
- Primary audience, age range, and age/safety policy.
- Initial language and proficiency scope.
- Which world beyond Emerald Valley is the first authored destination.
- Exact first-release location, resident, story, game, quiz, puzzle, and learning portfolio.
- Exact building upgrade trees, tiers, point names, award rules, costs, caps, and balancing.
- Whether scenario upgrades are primarily new content, new difficulty/role variants, environmental staging, or a combination (the proposed direction is a combination).
- Whether points are one universal currency or multiple clearly differentiated progress resources.
- Whether any non-point unlocks exist and how they are earned.
- Engine, backend, AI, speech, account, and offline choices.
- Commercial/monetization model.
- Release platform and minimum Android device/performance targets.

## 10. Approval and implementation boundary

This document records the product owner's explicit additions about Emerald Valley as home, broad learning choice, and point-funded building/scenario upgrades. The examples and proposed first-release slice are design proposals, not final commitments.

**No implementation, engine prototype, economy balancing experiment, or asset production is authorized by this document.** The complete blueprint and supporting specifications must be reviewed and explicitly approved first.
