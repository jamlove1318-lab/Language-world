# Language-world — UX, Navigation, and Accessibility Specification

**Status:** Working specification v0.1 — product-owner review required  
**Date:** 26 November 2026  
**Depends on:** Master Blueprint, Experience Catalogue, Learning Design, Travel, Cinematics, Creative Archive, Persistence/Privacy/Sync, Technical Architecture  
**Purpose:** Define how a learner moves through Language-world and how the world remains understandable, accessible, calm, and usable without becoming a dashboard.

---

## 1. Experience promise

The interface should help the learner inhabit the universe, not constantly remind them that they are operating an app.

The world is the primary experience. Navigation, settings, archive, focused study, help, and account controls exist to support it. The learner must always be able to understand:
- Where they are.
- What they can do here.
- How to begin, pause, leave, or resume.
- Whether progress has been saved.
- How to get help or change accessibility settings.
- How to control character presence, audio, motion, privacy, and recommendations.

The interface must never make a learner feel trapped, behind, guilty, or forced to complete a sequence before leaving.

## 2. UX principles

1. **World-first, not dashboard-first:** use the environment as the primary navigation context where it helps, with clear conventional navigation as a reliable alternative.
2. **Discoverable, not hidden:** important functions must not depend on noticing tiny environmental clues or remembering obscure gestures.
3. **Progressive disclosure:** show the next useful layer of information, not every system at once.
4. **Always an exit:** any activity, conversation, cinematic, or journey must have a clear skip/leave/recovery policy.
5. **Consistent interaction grammar:** similar objects, controls, menus, and states behave consistently across worlds.
6. **Respect attention:** no constant popups, unsolicited interruption, or excessive HUD.
7. **Learner control:** recommendations, companion presence, audio, motion, captions, language support, and notifications remain controllable.
8. **Accessible alternatives:** spatial interaction is never the only route to an essential action.
9. **Honest state:** distinguish saved, saving, offline-pending, synced, unavailable, and failed.
10. **Re-entry without punishment:** return after absence with optional context, never a backlog or guilt message.

## 3. Audience and accessibility assumptions

The primary audience, age policy, learner proficiency range, and exact accessibility target are open product decisions. This specification therefore establishes inclusive requirements without assuming age or ability.

Before implementation, define:
- Primary learner profile and age range.
- Supported languages and proficiency range.
- Target Android device tiers and input modes.
- Accessibility conformance target and test protocol.
- Whether classroom/family/managed accounts are in scope.
- Whether external keyboard, controller, switch access, or other input is supported.

If children or teens are in scope, onboarding, account, social, voice, AI, analytics, notifications, and parental controls require a separate age-appropriate policy before launch.

## 4. Information architecture

The product should be organized around a small number of understandable destinations, not a grid of every subsystem.

### 4.1 Primary experience spaces

Candidate top-level destinations:
- **World:** current location, nearby places, visible activities, people, environmental discoveries.
- **Journey:** universe map, world travel, route status, visited places and travel context.
- **Experiences:** focused learning, games, stories, culture and creative activities when the learner wants a direct entry point.
- **Personal archive:** learner-owned journal, phrasebook, creations, discoveries and saved moments.
- **Cassidy/People:** companion and resident interactions, only where contextually useful and with clear access to character boundaries.
- **Settings and support:** accessibility, audio, language, privacy, account, help, data controls and service information.

This is a conceptual taxonomy, not an approved tab bar. Final navigation should be selected after journey mapping and a prototype usability study. Do not copy GoPAL-AI's old tab layout.

### 4.2 World navigation

A learner should be able to:
- Orient to the current world and region.
- See nearby destinations and meaningful routes.
- Open a map or directory without leaving the world permanently.
- Understand visited, discovered, known, locked, unavailable, and story-relevant states.
- Find essential services such as home, station, library, study space, and settings.
- Navigate using touch-friendly alternatives to spatial movement.

Map state should not reveal spoilers or expose sensitive learner information. Hidden places may remain hidden, but essential navigation must not.

### 4.3 Navigation layers

Use a hierarchy:
1. Current world/location.
2. Region and nearby place.
3. Activity/interaction.
4. Detail or supporting panel.
5. System-level destinations/settings.

Avoid deep modal stacks. Provide a visible route back to the world or previous safe state.

## 5. Core user journeys

### 5.1 First launch

1. Explain the product simply and honestly.
2. Ask only for permissions/consent needed for the next chosen capability.
3. Establish language and accessibility preferences with a way to change them later.
4. Introduce Cassidy through the authored first-open sequence.
5. Reveal Emerald Valley as the home world.
6. Let the learner understand what is available without forcing every feature explanation.
7. Offer a first activity or free exploration.
8. Save onboarding progress and support interruption/re-entry.

Do not front-load a long questionnaire. Do not request microphone, camera, notifications, or account permissions before explaining their purpose and need.

### 5.2 Ordinary return

1. Restore the last safe world/place/session.
2. Present a concise optional "since you were here" note only when there is meaningful, verified change.
3. Do not list missed days, expired streaks, or accumulated tasks.
4. Offer direct return to the world and a clear way to see recent journey notes.
5. Do not force Cassidy to greet or interrupt every return.

### 5.3 Explore

1. Show the learner where they are and a small number of contextual possibilities.
2. Support free movement and accessible place selection.
3. Make inspectable objects and points of interest discoverable.
4. Allow observation without requiring interaction or a lesson.
5. Preserve discoveries when they are meaningful and explain what was recorded.
6. Let the learner stop at any time.

### 5.4 Start a learning experience

1. Provide a clear reason/context for the activity.
2. State the skill focus and approximate commitment where useful.
3. Offer language support and hint preferences.
4. Allow practice without a score when appropriate.
5. Give specific feedback grounded in the evidence available.
6. Offer replay, another explanation, or exit.
7. Record only meaningful learning evidence and show save/sync state.

### 5.5 Story or investigation

1. Make story entry optional and understandable.
2. Provide a recap if the learner has an unfinished thread.
3. Distinguish discovered evidence from speculation.
4. Support pause, journal review and re-entry.
5. Do not require a time-limited daily return to preserve progress.
6. Keep spoilers controlled but do not make the interface cryptic.

### 5.6 Creative activity and archive

1. Make it clear whether the learner is creating a new item or editing an existing one.
2. Preserve a recoverable draft.
3. Distinguish learner-authored content from AI suggestions or generated decoration.
4. Preview before publishing/sharing/export.
5. Default to private.
6. Provide edit, revision history where appropriate, delete, export and accessibility support.

### 5.7 Travel

1. Explain destination and transport choice.
2. Make departure/boarding actions clear and skippable where appropriate.
3. Offer journey controls and optional activities.
4. Show travel state if interrupted.
5. Make arrival and destination orientation clear.
6. Provide a direct route back to map/world navigation.

### 5.8 Account, privacy and settings

Settings must be reachable from any major product context. The learner can:
- Change language, text, audio, captions, motion and interaction preferences.
- Review microphone/camera/AI consent.
- Control memory and personalization where applicable.
- Export or delete personal data.
- Sign out or switch account safely.
- Find support, privacy information and current service status.

## 6. Activity lifecycle and navigation contract

Every activity must define:
- Entry conditions and origin.
- Whether it pauses the world or remains in-world.
- Input/focus ownership.
- Save/checkpoint moments.
- Background and interruption behaviour.
- Exit confirmation only when unsaved work could be lost.
- Resume/restart/replay policy.
- What durable state changes on completion.
- Return destination and focus restoration.

Never make a cinematic or modal the only path to an important state transition. The domain operation must survive if the presentation is skipped, closed, or fails.

## 7. World interface and HUD

Keep the persistent HUD minimal. Candidate elements:
- Current place/region when orientation is needed.
- Contextual interaction prompt.
- Optional map/compass access.
- Activity or travel state when active.
- Clear system controls and accessibility access.

Avoid:
- Persistent XP bars or streak countdowns.
- Constant quest arrows and glowing markers.
- Excessive floating labels.
- Unsolicited character chat bubbles.
- Multiple competing notification badges.
- Reward popups after every interaction.

Important information should remain available through a pause/menu or accessible list, not only floating in 3D space.

## 8. Touch and spatial interaction

Define large, reliable touch targets and forgiving interaction:
- Clear focus/selection feedback.
- No essential action requiring pixel-perfect tapping.
- Alternative list/map selection for small, moving, distant, or occluded objects.
- Adjustable camera sensitivity and movement mode.
- Optional auto-navigation for accessibility.
- Reversible actions where possible.
- Clear distinction between inspect, use, collect, talk, travel and exit.
- Prevent accidental purchase, deletion, sharing, or irreversible choices.

If external keyboard/controller is later supported, provide consistent focus navigation and remappable controls.

## 9. Accessibility requirements

### 9.1 Vision and reading
- Scalable text with layouts that reflow.
- Strong contrast and no colour-only meaning.
- Screen-reader labels and logical reading order.
- Text alternatives for visual-only clues and essential world information.
- Avoid tiny decorative text embedded in textures.
- Adjustable UI scale and legibility options.
- Dyslexia-friendly presentation options where feasible without making unsupported claims.

### 9.2 Hearing and audio
- Captions for dialogue and meaningful sound cues.
- Transcript access for spoken learning content.
- Independent controls for dialogue, ambience, music and effects.
- Visual alternatives for important audio-only events.
- No essential instruction communicated only through sound.
- Respect system audio focus and interruptions.

### 9.3 Motion and vestibular comfort
- Reduced-motion mode.
- Skip or simplify camera shake, rapid cuts, parallax, forced camera motion and intense effects.
- Provide non-cinematic alternatives for essential information.
- Avoid motion-dependent interaction as the only option.
- Respect user choice during travel and character reveals.

### 9.4 Motor and interaction
- Adjustable control sensitivity and input timing.
- Forgiving hit areas and alternatives to complex gestures.
- No mandatory rapid tapping or narrow reaction windows for essential progression.
- Pause/resume without penalty.
- Accessible alternatives to long movement sequences.

### 9.5 Cognitive and language accessibility
- Clear, consistent wording and predictable navigation.
- Adjustable hint/translation/subtitle support.
- Break complex tasks into understandable steps.
- Explain unfamiliar mechanics in context.
- Avoid unnecessary simultaneous objectives.
- Provide optional recaps and explicit progress states.
- Do not assume a learner can infer hidden conventions.

### 9.6 Sensory and stimulation control
- Quiet mode that reduces nonessential sound and visual effects.
- Control over character interruptions and ambient events.
- No flashing patterns or intense visual effects without safe alternatives.
- Ability to pause or leave overwhelming experiences immediately.

## 10. Localization and cultural usability

- All UI text must be externalized and versioned.
- Support text expansion, right-to-left layout if required by future languages, and font fallback.
- Avoid text embedded in images unless localized variants exist.
- Subtitles must accommodate longer translations and different reading speeds.
- Dialogue timing must adapt to localization, not force every language into the same fixed duration.
- Cultural conventions and forms of address must be reviewed for the relevant world and language.
- Keep language-learning content distinct from interface localization preferences.

## 11. Notifications and return policy

Notifications are optional and purpose-limited. Do not use them to simulate Cassidy distress, threaten loss, manufacture urgency, or punish absence.

Before notifications exist, define:
- User opt-in and per-category controls.
- Quiet hours and local-time handling.
- Maximum frequency and deduplication.
- No sensitive personal content on lock screens by default.
- No notification for every world event or character schedule.
- A clear disable path.

The world should remain meaningful when notifications are disabled.

## 12. Error, loading and recovery UX

Every loading, save, sync, permission and service state must be understandable:
- Loading with progress or an honest indeterminate state.
- Offline content availability and download size.
- Local save complete vs sync pending.
- Recoverable vs unrecoverable failure.
- Retry only when safe and idempotent.
- Missing content/asset fallback.
- AI/speech provider unavailable fallback.
- Permission denied path with a clear explanation and no repeated nagging.
- App interruption recovery and safe return to a known state.

Do not show "saved" before the durable write succeeds.

## 13. Usability and accessibility validation

Before release, test:
- First-open without prior product knowledge.
- Free exploration without guidance.
- Starting and exiting learning, story, creative and travel experiences.
- Returning after interruption and after a long absence.
- Finding settings, privacy and accessibility controls.
- Screen reader navigation of core surfaces.
- Text scaling and layout reflow.
- Captions/transcripts and audio controls.
- Reduced-motion travel/cinematic alternative.
- Low-end device responsiveness and loading feedback.
- Users with varied language proficiency and accessibility needs, based on the approved audience.

Record observed task completion, confusion, recovery success, accessibility barriers and user feedback. Do not treat internal designer approval as usability evidence.

## 14. Open decisions

- Primary audience, age range and age policy.
- Supported learner proficiency levels and first learning language(s).
- Final top-level navigation and whether any destinations are tabs, world objects, or contextual panels.
- World movement model and accessible alternatives.
- Controller/keyboard/switch support.
- Notification policy and whether notifications exist in the first release.
- Accessibility conformance target and external review.
- First-launch permission/consent sequence.
- Session length choices and experience-intent entry point.
- How much of the world remains explorable in low-performance mode.

## 15. Approval checklist

- [ ] Audience and age policy are defined.
- [ ] First-launch and return journeys are reviewed.
- [ ] World, map, archive, experience and settings navigation is coherent.
- [ ] Activity lifecycle covers pause, exit, interruption, save and re-entry.
- [ ] Touch/spatial controls have accessible alternatives.
- [ ] Vision, hearing, motion, motor, cognitive and sensory requirements are accepted.
- [ ] Localization and subtitle timing are reviewed.
- [ ] Notifications and companion-presence rules are non-coercive.
- [ ] Loading, saving, sync, permissions and failure states are specified.
- [ ] Usability/accessibility test plan and target devices are approved.

**Current decision:** design only. This specification does not authorize implementation, UI prototyping, or a fixed navigation layout.


## 16. Emerald Valley navigation and mobile spatial layout

The home world is a large spatial map, not a static hub. The main Emerald Valley map should pan/scroll in both horizontal and vertical directions on mobile, revealing districts, paths, landmarks, public buildings, natural areas, and intentional empty plots. Navigation should preserve spatial orientation, show where the learner is, and provide accessible alternatives to fine camera gestures.

Each individual location should use a horizontal, landscape-oriented mobile scene composition. Where a location extends beyond the viewport, it should support horizontal exploration/scrolling with clear camera bounds and interaction focus. Do not confuse this with the two-axis world map. Whether the app rotates/locks the device to landscape or presents a landscape scene within another device orientation is still an open decision and must be tested on target devices before commitment.

Map and location controls must support touch, keyboard/controller if applicable, screen-reader semantics, zoom/scale alternatives, recentering, and reduced-motion camera movement. Scrolling must not make important actions unreachable or hide save/exit controls. Provide minimap/overview or location navigation where scale requires it, without turning the world into a dense dashboard.

## 17. Learner plots, personal homes, and build mode

Empty plots are intentional build opportunities in Emerald Valley. The learner can discover available spaces and, subject to clear rules, acquire houses, buildings, decorations, furniture, gardens, and other items. Build mode should make plot boundaries, footprint, placement, rotation, cost, ownership, accessibility, and confirmation clear. Provide undo/cancel or safe recovery before committing irreversible placement or spending.

Personal construction must preserve public routes, shared locations, readable navigation, and accessibility. The UX should distinguish learner-owned property from shared/public building upgrades and Cassidy's own home. Build mode must not be mandatory for learning progression, and essential learning access must not depend on owning a house or decorative items.

## 18. Animation and motion UX

Animation is a product-wide presentation requirement: characters, residents, world ambience, transitions, travel, building upgrades/construction, object interactions, stories, games, puzzles, learning feedback, and interface state changes should have intentional motion design. Animation must communicate rather than decorate every idle moment.

All important state changes need a non-motion cue. Support reduced motion, pause/skip for nonessential cinematics, predictable timing, no motion-only instructions, and stable interaction targets. Avoid forced camera movement, flashing, excessive parallax, or transitions that delay access. Gameplay and learning state must survive interruption even when an animation is skipped or cancelled.

## 19. Orientation and location behaviour — open decision

The required design direction is horizontal/landscape-oriented mobile locations with horizontal scrolling where needed, while Emerald Valley's map scrolls in both axes. Final device-orientation behaviour (orientation lock, rotation on entering a location, or landscape scene viewport) remains open until target-device usability, accessibility, and performance testing. Do not infer a final orientation lock from the visual design requirement alone.
