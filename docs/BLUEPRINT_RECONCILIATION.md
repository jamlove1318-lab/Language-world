# Master Blueprint Reconciliation — GoPAL Ideas to Language-world

**Status:** Working reconciliation — design research, not approved for implementation  
**Date:** 26 November 2026  
**Inputs:** Master Blueprint, current supporting specifications, GoPAL-AI Idea Recovery Audit, Architecture Decisions, Roadmap, and Blueprint Work Register  
**Purpose:** Identify what the recovered ideas add, what the current blueprint already covers, what remains missing, and which contradictions must be resolved before approval.

## 1. Executive finding

The current Language-world document set captures most major GoPAL-AI idea families and has improved them in important ways: distinct worlds, contextual learning, Cassidy's independent agency, stories and mysteries, ecology, durable travel, world audio, personal creative archives, persistence/privacy, and replaceable production assets.

The central risk is no longer a lack of ideas. It is **blueprint coherence and decision closure**.

The project has many strong system specifications, but several product-level decisions remain open, the Master Blueprint contains stale work-order text and mismatched supporting-document names, and critical cross-system contracts have not yet been consolidated into one technical architecture and production/quality plan.

**Conclusion:** The research is sufficiently broad to stop mining GoPAL-AI indiscriminately. Further reference research should be driven by a specific unresolved question. The next work should reconcile, decide, and author the missing Language-world design—not keep expanding a feature list.

## 2. What is already represented well

The following idea families are present in the Master Blueprint and/or dedicated working specifications. They should be treated as captured, not rediscovered.

| Idea family | Current home | Assessment |
|---|---|---|
| A place worth returning to; no punitive absence | Master Blueprint, Foundation, Experience Catalogue | Captured as a product principle |
| Emerald Valley as home; other language worlds distinct | Master Blueprint, World & Universe Bible | Captured as a rule; actual world canon remains incomplete |
| Cassidy as a human, independent central character | Master Blueprint, Cassidy Character Bible | Captured; final canon approval remains open |
| Resident communities and world-specific ecology | Master Blueprint, World Simulation Spec | Captured at system level; cast/species content remains open |
| Broad activities beyond lessons and chat | Experience Catalogue | Captured as taxonomy and research seeds; first portfolio unapproved |
| Contextual learning and honest skill evidence | Learning Design | Captured at design level; target language/curriculum/evaluation decisions remain open |
| Stories, mysteries, clue fairness, narrative canon | Narrative and Story Continuity Spec | Captured at system level; initial story portfolio remains open |
| Time, weather, seasons, routines, ecology and bounded offline simulation | World Simulation Spec | Captured; canonical clock/profile choices remain open |
| Objects, buildings, interiors, interactions and personal spaces | World Objects and Spaces | Captured; launch subset and technical integration remain open |
| First-open and cinematic storytelling | Cinematic Experience Blueprint | Captured as sequence requirements; final script and staging remain open |
| Inter-world travel and contextual transport | Travel Experience Spec | Captured as a durable lifecycle; route/world canon remains open |
| Audio, voice, ambience, learning audio and accessibility | Audio/Voice/Soundscape Spec | Captured; voice, language and delivery decisions remain open |
| Personal archive and creative work | Creative Experiences and Personal Archive | Captured; launch scope and sharing policy remain open |
| Learner identity, local-first persistence, sync, privacy and recovery | Persistence/Privacy/Sync | Captured as requirements; account/backend/offline policy remains open |
| Replaceable assets and designer handoff | Asset Handoff and Asset/Cinematic Pipeline | Captured; engine-neutral and final import contracts still need architecture alignment |
| Healthy personalization and experience direction | Experience Catalogue and system specifications | Partially captured; one explicit cross-product Experience Director contract is still needed |
| Optional future social/shared experiences | Experience Catalogue and idea recovery audit | Captured as future/deferred, not launch commitment |

The 60 game ideas are research seeds, not a launch backlog. Creative/archive ideas are a family of experiences, not a requirement to ship every format. The same principle applies to social, AI, camera, real-world integrations, crafting, inventory, and world-radio concepts.

## 3. Missing product-level definitions

These are not solved merely because a system specification mentions them.

### 3.1 Audience, age policy, and learning audience — blocking

Still undefined:
- Primary audience and age range.
- Whether children/teens are in scope at launch.
- Supported learner proficiency range and language-learning goals.
- Accessibility assumptions and supported needs.
- Whether the product is designed for individual self-study, family use, classroom use, or a combination.

Why it matters: it changes character interaction boundaries, content ratings, account/consent design, voice recording, AI use, analytics, social features, moderation, monetization, and legal/privacy obligations.

**Required output:** a product audience and age-policy decision, with an explicit initial learner profile. Do not infer an age range.

### 3.2 Product promise and first-release boundary — blocking

The vision is broad, but there is no approved statement of what the first complete release must let a learner do from first launch through repeat visits.

Need to define:
- The smallest coherent universe experience that still feels like Language-world.
- Which world(s), regions, characters, stories, learning contexts, games, creative tools, and travel experiences are in the first release.
- Which capabilities are launch-critical versus later expansions.
- What is deliberately not included in the first release.
- What a satisfying short session, long session, and return session look like.

**Required output:** a first-release product definition and a deliberately bounded content portfolio—not a feature-count target.

### 3.3 Core experience loops and navigation — high priority

The Experience Catalogue lists families, but the product still needs one coherent journey across them:
- First launch and consent/onboarding.
- Entering the world and choosing an intention.
- Discovering an activity naturally.
- Starting, pausing, leaving, and resuming an experience.
- Switching between exploration, focused learning, story, creativity, and calm presence.
- Travel between worlds.
- Returning after absence and understanding relevant changes.
- Accessing settings, archive, accessibility, account, help, and privacy without turning the world into a dashboard.

**Required output:** user journeys, navigation model, information architecture, and state/route lifecycle. Do not copy GoPAL-AI's tab layout.

### 3.4 Experience Director and recommendation policy — high priority

Personalization concepts exist, but a single product-wide contract is not yet explicit.

Define:
- Inputs it may use and their privacy classification.
- Approved catalogue and eligibility rules.
- Learner intent and session-length preferences.
- Diversity/familiarity balance and repetition limits.
- Explanation of "why this suggestion".
- User controls: decline, quiet, different suggestion, less like this, save for later.
- No coercion, hidden urgency, or automatic AI-generated unreviewed content.
- Fallback when no suitable recommendation exists.
- Clear boundary: director recommends/orchestrates; domain systems own state.

**Required output:** bounded Experience Director specification integrated with learning, story, world, Cassidy, and archive domains.

### 3.5 Universe canon and actual world authorship — high priority

The World & Universe Bible is currently a framework, not complete world canon. Emerald Valley is not yet approved as definitive geography. Spanish world is still an example/first-route candidate, not a completed world. Japanese/French seeds are not launch commitments.

Need:
- Universe premise and rules for why/how worlds connect.
- Whether language worlds represent real places, fictional places, or deliberate hybrids.
- A coherent geography for Emerald Valley.
- The first destination decision and its world bible.
- Cultural research/review process, dialect/register policy, and source provenance.
- A world-by-world distinction matrix that proves each world has a unique identity.

**Required output:** approved first-world pair and a small but complete authored region in each.

### 3.6 Cassidy canon approval and performance boundaries — high priority

The Cassidy Character Bible is detailed but still has open written-source conflicts and approval questions. The user owns her canonical design; GoPAL-AI files are not a source of assets for the new repository.

Need:
- Product-owner confirmation of the canonical design source when ready to begin independent production.
- Resolve age presentation, voice direction, backstory, outfit/variant rules and conflicting written descriptions.
- Define what Cassidy can know, remember, infer, promise, and say.
- Define autonomy limits and how the character behaves when the app is closed.
- Establish what is authored dialogue versus generated dialogue and the review/guardrail policy.
- Define how Cassidy's own stories fit into the wider universe without making every activity about her.

**Required output:** approved character canon and a character performance/AI boundary spec. No redesign or asset extraction is implied.

### 3.7 AI policy and capability honesty — high priority

Privacy and learning specs mention AI, but a unified AI product policy is missing.

Define:
- Which experiences use scripted content, retrieval, generation, speech services, or no AI.
- What is generated at runtime versus authored and reviewed.
- Truthfulness, hallucination handling, source grounding, and uncertainty.
- Character memory and learner data access permissions.
- Provider selection criteria, retention, training-use terms, data location, cost, latency, and offline fallback.
- Voice recording and speech assessment consent, retention, deletion, and explicit capability claims.
- Age-appropriate controls if minors are in scope.
- Safe fallback if a provider is unavailable or gives unsuitable output.

**Required output:** AI/voice service policy and decision record, not an assumption that every character is powered by an LLM.

### 3.8 Economy, progression, and monetization — medium/high priority

The blueprint rightly rejects manipulative XP/streak loops, but it does not yet explicitly define:
- Whether currency, collectibles, unlocks, levels, or progression exist at all.
- What progress means across language capability, world knowledge, stories, creative archive, and travel.
- Whether there is a commercial model (paid app, subscription, free tier, purchase, institutional licensing, or undecided).
- How monetization, if any, avoids pay-to-progress or emotional pressure.
- Whether any reward is cosmetic, expressive, practical, or content access.

**Required output:** a deliberate progression/economy/monetization policy. Do not add a shop or currency simply because the reference archive had one.

### 3.9 Operations, support, and live content — medium priority

A living universe may need content updates, events, service health, account recovery, support, and incident response. The current documents do not yet define:
- Content release and rollback policy.
- Offline-compatible content packs and version compatibility.
- Operational ownership for AI/voice services.
- Crash/diagnostic privacy and retention.
- User support, safety reporting, moderation (if applicable), and service status.
- Festival/event scheduling without punishing users in other time zones or absence periods.

**Required output:** operational readiness and live-content policy for the actual launch model.

## 4. Cross-document inconsistencies and cleanup required

1. **Stale Master Blueprint work order:** Sections 31–32 still say some work is upcoming even though supporting documents have since been created and the GoPAL idea-recovery audit is consolidated. Rewrite the work order as current status and remaining approval checklist.
2. **Supporting filename mismatch:** the Master Blueprint's supporting table names CINEMATIC_EXPERIENCE_SYSTEM.md, ASSET_AND_CREATIVE_PIPELINE.md, and AUDIO_EXPERIENCE_SPEC.md; actual files are CINEMATIC_EXPERIENCE_BLUEPRINT.md, ASSET_AND_CINEMATIC_PIPELINE.md, and AUDIO_VOICE_AND_SOUNDSCAPE_SPEC.md. The index must link to actual canonical files.
3. **Source-audit scope mismatch:** an older roadmap item calls for inventorying and reviewing legacy assets/manifests/licensing. The user has explicitly limited GoPAL-AI transfer to ideas only. Remove old-asset inspection from the GoPAL research plan. Language-world's own future asset pipeline remains in scope.
4. **Roadmap Phase 4 ambiguity:** "Transfer/locate canonical references" could be read as importing GoPAL-AI artwork. Clarify that only user-approved canonical design material may be supplied for new production; no GoPAL-AI assets are copied.
5. **Work Register formatting/status drift:** repair literal escaped newline artefacts and make section counts/document status consistent with current files.
6. **World Bible evidence wording:** distinguish recovered landmark seeds from approved Language-world canon. No source-derived place list should silently become final geography.
7. **Architecture decision numbering:** ARCHITECTURE_DECISIONS.md contains duplicate ADR-010 labels. Renumber the second decision and check references.
8. **Master Blueprint approval language:** preserve the hard gate: no implementation before explicit product-owner approval, regardless of how many supporting drafts are marked complete.

## 5. Required missing or expanded documents

| Document / output | Priority | Why |
|---|---|---|
| This reconciliation | Created | Central gap and contradiction register |
| TECHNICAL_ARCHITECTURE.md | Created — working draft v0.1 | Consolidates domain ownership, runtime, event/data, engine adapter and failure contracts; review required |
| UX_AND_ACCESSIBILITY_SPEC.md | Created — working draft v0.1 | End-to-end journeys, navigation, activity lifecycle, accessibility and re-entry; review required |
| AI_AND_VOICE_GOVERNANCE.md | High | AI/service boundaries, generated content, memory, consent, provider and capability honesty |
| PRODUCTION_AND_QUALITY_PLAN.md | High | Content production, roles, review, test strategy, device matrix, release gates |
| PRODUCT_SCOPE_AND_RELEASE_DEFINITION.md | Critical | Audience, first-release promise, scope and excluded features |
| World-specific bibles | High | Actual Emerald Valley and first destination authorship |
| Experience Director spec | High | Bounded cross-domain recommendation/orchestration policy |
| Operational/live-content plan | Medium | Updates, service operations, support, events and incident response |

These can be combined where that makes the document set clearer. Do not create documents merely to increase the count.

## 6. Architecture-wide contracts that must be made explicit

The technical architecture must resolve the following without selecting an engine or backend prematurely:

### 6.1 One owner per durable truth
Each domain owns its canonical state. Other domains request changes through explicit commands/contracts and consume versioned events. No UI component, cinematic, or recommendation director owns durable domain truth.

### 6.2 Separate state classes
- Authored content and canon.
- Learner-owned durable state.
- Session/transient state.
- Derived/read models.
- Cache/downloaded content.
- Operational telemetry.

Each class needs a storage, migration, privacy, and recovery rule.

### 6.3 Durable cross-domain operations
When an experience affects learning, world state, narrative, Cassidy memory, and archive, define a durable operation with stable identity, idempotency, causal links, retry/recovery, and visible partial-failure handling.

### 6.4 Time and lifecycle
Separate frame/render time, authored cinematic time, simulation time, learner-local time, and UTC event time. Define background/foreground, sleep, app termination, offline catch-up, and time-zone changes.

### 6.5 Content and asset independence
Domain and story logic reference semantic content IDs and events, never filenames, scene-node paths, clip names, or engine classes. Engine adapters own rendering, physics, input, audio playback, animation evaluation, and platform integration.

### 6.6 Experience orchestration is not ownership
The Experience Director may select an eligible experience and coordinate entry, but learning, story, travel, Cassidy, archive, and world systems remain authoritative for their own data.

## 7. Recommended order of work

1. [x] Reconcile the Master Blueprint and supporting-document links.
2. [x] Create the engine-neutral Technical Architecture working draft and ownership model.
3. [x] Create UX/Accessibility and end-to-end navigation working specification.
4. Define audience, age policy, first-release promise, and excluded scope.
5. Define AI/voice governance and Experience Director boundaries.
6. Complete actual world bibles and first experience portfolio.
7. Create Production/Quality/Operations Plan with test gates and measurable acceptance criteria.
8. Run a contradiction/dependency pass across every document.
9. Present the complete package for product-owner review.
10. Only after explicit approval begin implementation planning and Android engine evaluation/prototypes.

The order can be adjusted if a decision blocks another; it is not authorization to start prototypes.

## 8. Research stopping rule

GoPAL-AI research is now sufficiently broad for product-idea transfer. The repository tree inventory and selected source inspection have provided a useful picture of its product concepts and limitations. No need exists to inspect its visual assets, audio binaries, 3D models, Blender projects, or old production pipeline.

Further GoPAL-AI research is justified only when a concrete unresolved Language-world question would materially benefit from a specific source check. The goal is not to reproduce the old application or exhaustively inventory its implementation.

## 9. Approval checklist

- [ ] Product owner reviews the recovered idea transfer and this reconciliation.
- [ ] Missing product-level decisions are resolved or explicitly deferred.
- [ ] Master Blueprint links, statuses, and work orders are reconciled.
- [ ] Technical Architecture is reviewed.
- [ ] UX/Accessibility and navigation are reviewed.
- [ ] Audience, age policy, first-release scope, AI/voice policy, and progression/monetization boundaries are explicit.
- [ ] World canon and Cassidy canon are approved.
- [ ] Production, quality, security, privacy, and operational gates are defined.
- [ ] All supporting specifications agree and trace back to product requirements.
- [ ] Product owner explicitly approves the complete blueprint for implementation.

**Current decision:** design and research only. No implementation, engine prototype, asset production, or GoPAL-AI asset transfer is authorized.
