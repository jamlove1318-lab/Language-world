# Engine Evaluation — Android-First Living Universe

**Status:** Preliminary research; no engine selected  
**Date:** 2026-11-18  
**Decision rule:** Do not select an engine until the same representative vertical slice has been built, packaged, and measured on the intended Android device class.

## 1. Product requirements that drive this decision

Language-world is an explorable, multi-world universe. Cassidy is its emotional heart, but the product also needs authored stories, mysteries, games, cultural experiences, creative tools, exploration, residents, world events, audio, and durable personal history.

The engine must support:
- A real-time explorable 3D or carefully art-directed 2.5D world on Android.
- A human character with expressive animation, locomotion, facial performance, gestures, and dialogue staging.
- Many distinct locations and language worlds without forcing every world into one art or scene template.
- A broad set of interactive game mechanics and story delivery formats.
- Reliable audio, UI overlays, accessibility, save/recovery, and offline behaviour.
- Asset production from a completely new pipeline. No GoPAL-AI 3D models, rigs, animations, renderers, scripts, asset factories, export tools, registries, or runtime contracts may be reused.
- A sustainable workflow with automated builds, profiling, repeatable tests, and Android device iteration.
- No Expo.

## 2. Shortlist

### Godot 4.x

**Why it is a serious candidate**
- Open-source under the MIT license; commercial use is allowed, with license-notice obligations.
- Provides distinct Forward+, Mobile, and Compatibility renderers. The Mobile renderer is designed for simpler mobile scenes; Compatibility provides a lower-end OpenGL path.
- Official Android export workflow is documented and uses Android SDK tooling and OpenJDK 17.
- Scene/node composition and scripting can suit a world assembled from reusable authored scenes, interaction components, and data-driven content.

**Risks and questions**
- The target device's Vulkan/OpenGL driver quality must be tested; minimum published requirements do not guarantee good performance on a specific phone.
- C# Android export is documented as experimental/limited; GDScript or carefully tested native extensions may be safer for the first prototype.
- Third-party plugins, character animation tooling, speech/audio integrations, and production asset workflows need a compatibility audit.
- We must measure memory, frame pacing, shader compilation/stutter, build size, load time, and thermal behaviour on actual hardware.

Official references:
- [Android export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_android.html)
- [System requirements](https://docs.godotengine.org/en/latest/about/system_requirements.html)
- [Renderer overview](https://docs.godotengine.org/en/stable/tutorials/rendering/renderers.html)
- [License](https://godotengine.org/license)

### Unity 6

**Why it is a serious candidate**
- Mature Android build pipeline with documented Android Build Support, SDK, NDK, and OpenJDK dependencies.
- Broad ecosystem for animation, character production, profiling, audio, UI, asset import, and third-party integrations.
- URP is supported on Android; HDRP is not an Android target according to current Unity Android compatibility documentation.
- Unity Personal currently has a published eligibility threshold of less than USD 200,000 in revenue/funding over the relevant prior 12 months; eligibility and terms must be rechecked before commercial use.
- Unity's Runtime Fee was cancelled; current licensing should still be checked at the time of adoption.

**Risks and questions**
- The full editor/toolchain and ecosystem can introduce project complexity and package/version management.
- Must prove URP scene quality and performance on the actual device; feature availability varies by GPU/API.
- Plugin quality, package lock-in, long-term support and licensing need deliberate governance.
- Unity is not automatically faster or more efficient than Godot for this product; only a controlled test can answer that.

Official references:
- [Unity Android requirements and compatibility](https://docs.unity.com/en-us/engine/6000.7/manual/platform-specific/android/introducing/requirements-and-compatibility)
- [Android environment setup](https://docs.unity.com/en-us/engine/6000.7/manual/platform-specific/android/getting-started/sdksetup)
- [Supported SDK/NDK/JDK versions](https://docs.unity.com/en-us/engine/6000.6/manual/platform-specific/android/getting-started/sdksetup/supported-dependency-versions)
- [Unity Personal](https://unity.com/products/unity-personal)
- [Runtime Fee cancellation](https://activation.unity3d.com/products/pricing-updates)

### Unreal Engine 5.x

**Why it is a serious candidate**
- Strong high-end 3D, animation, cinematic, lighting, material, and large-world toolsets.
- Official Android workflows include on-device profiling and mobile rendering optimization guidance.
- Has a dedicated mobile rendering path and Android frame-pacing support.
- Licensing currently describes a 5% royalty on applicable lifetime gross revenue above USD 1 million for qualifying runtime products, with details and exceptions in the license.

**Risks and questions**
- The toolchain and content workflows are comparatively demanding; project scale and mobile constraints could make iteration slower.
- High-end rendering features cannot simply be assumed available or affordable on mid-range Android hardware.
- Android device compatibility, package size, memory pressure, shader/PSO preparation, thermal behaviour, and battery cost need early proof.
- It may be excessive if the desired art direction can be achieved with a lighter renderer and smaller asset budgets.

Official references:
- [Android development requirements](https://dev.epicgames.com/documentation/unreal-engine/android-development-requirements-for-unreal-engine)
- [Android support](https://dev.epicgames.com/documentation/unreal-engine/android-support-for-unreal-engine)
- [Mobile optimization](https://dev.epicgames.com/documentation/en-us/unreal-engine/optimization-and-development-best-practices-for-mobile-projects-in-unreal-engine)
- [Licensing](https://www.unrealengine.com/license)

## 3. Preliminary comparison (not a score or selection)

| Criterion | Godot | Unity 6 | Unreal 5 |
|---|---|---|---|
| Android export | Supported; documented SDK/JDK setup | Mature documented Android module/toolchain | Supported; dedicated Android workflow |
| Mobile rendering choices | Mobile + Compatibility | URP; graphics API/device constraints | Dedicated mobile renderer/scalability |
| High-end character/cinematic tooling | Capable, ecosystem smaller | Broad animation/character ecosystem | Strongest high-end native toolset |
| Workflow weight | Likely lightest of this shortlist | Medium-to-high | Highest |
| Licensing model | MIT open source | Subscription tiers/eligibility | Royalty terms for qualifying products |
| Main unknown | Device performance and tooling fit | Complexity, package and device performance | Practical mobile budget and workflow weight |
| Current status | Prototype candidate | Prototype candidate | Prototype candidate |

This table is directional only. It does not predict frame rate, battery use, memory, build size, or production speed.

## 4. First comparison prototype

Build the same small, representative scene independently in each shortlisted engine. Do not port old GoPAL code or assets.

The prototype must include:
1. One newly created environment with a small outdoor area and one interior transition.
2. One newly produced human character placeholder with skeletal animation, locomotion, idle variation, a gesture, and a short expression/voice staging test.
3. A handful of independently authored interactable objects with action feedback and a persistent state change.
4. One short story sequence with a choice and a recoverable saved outcome.
5. One small game mechanic with keyboard/editor test controls and Android touch controls.
6. Layered ambience, one positional cue, dialogue playback, mute/quiet mode, and audio interruption recovery.
7. A data-driven content/asset replacement test: replace a placeholder model, animation, sound, or interaction definition without changing gameplay code.
8. Save, close, relaunch, and verify world/story/game state recovery.

Do not build the entire universe in this prototype. It exists to test the engine's ability to support the universe.

## 5. Required Android measurements

Run release-like builds on the actual target phone and record:
- Average, 95th percentile, and worst frame time; dropped frames and frame pacing.
- CPU/GPU load and sustained performance after a 20–30 minute session.
- Memory use at launch, after scene load, after repeated transitions, and after returning from background.
- Initial install size, downloaded content size, and incremental update size.
- Cold start, warm start, scene transition, and asset-streaming times.
- Battery drain and device temperature over a repeatable session.
- Audio latency, interruptions, background/foreground behaviour, and resource cleanup.
- Crash rate, graphics-driver issues, and save recovery after forced process termination.

Test both the intended minimum device and a stronger reference device before choosing a production baseline. Record device model, SoC, GPU, RAM, Android version, display resolution, and graphics API.

## 6. Decision gates

An engine may be selected only when:
- The representative slice builds and installs on the target device.
- It meets agreed frame-time, memory, load-time, battery, and thermal budgets.
- Character animation and world interaction feel good enough for Cassidy's intended presence.
- Audio, touch UI, accessibility, persistence, and recovery are demonstrated.
- The fresh asset pipeline works end to end and does not depend on the legacy GoPAL pipeline.
- The development workflow is repeatable and maintainable.
- Licensing, third-party dependencies, export requirements, and long-term support are acceptable.

## 7. Current recommendation

**Do not commit to an engine yet.** Keep Godot and Unity as the first practical comparison candidates, with Unreal retained as a high-fidelity reference candidate until the actual target device and visual budget are known. This is a testing order, not a final ranking.

The next engineering task is to define the device/performance envelope and prepare the identical prototype specification. The engine decision follows measured results—not brand preference, feature-list size, or assumptions about performance.
