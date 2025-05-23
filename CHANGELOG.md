# `big-brain` Release Changelog

<a name="0.22.0"></a>
## 0.22.0 (2024-11-30)

### Features

* **picker:** add HighestToScore Picker (#105) ([ab0385d5](https://github.com/zkat/big-brain/commit/ab0385d543a764f8a06013dbb69ef2193e1ef8ab))
* **bevy:** Upgrade to bevy 0.15 (#106) ([868ebdb4](https://github.com/zkat/big-brain/commit/868ebdb4fc3116af095dcd1ea0685fa6c517ddfe))

<a name="0.21.1"></a>
## 0.21.1 (2024-07-09)

This is just a patch release because of a hiccup during the release process for 0.21.1, but is otherwise identical.

<a name="0.21.0"></a>
## 0.21.0 (2024-07-09)

### Features

* **bevy:** Upgrade to bevy 0.14.0 (#101) ([3a952a24](https://github.com/zkat/big-brain/commit/3a952a244b01a09fa6157ae9349575935d159c91))

<a name="0.20.0"></a>
## 0.20.0 (2024-05-17)

### Features

* **bevy:** Update for bevy 0.13 (#93) ([50415e55](https://github.com/zkat/big-brain/commit/50415e55f0a9937dc99cb8f0b0906e47cb390082))
* **scorers:** Add support for generic types in ScorerBuilder (#96) ([98337faa](https://github.com/zkat/big-brain/commit/98337faacd5eb720cc820628fd1bfa07e6c8effa))

### Bug Fixes

* **derive:** using prelude rather than ecs::xyz in derive (#99) ([128f55e0](https://github.com/zkat/big-brain/commit/128f55e008c933a3eae1df44de0455f56acfdff7))

<a name="0.19.0"></a>
## 0.19.0 (2024-01-19)

### Features

* **set_unchecked:** Add `set_unchecked` method to `Score` (#78) ([e179cb53](https://github.com/zkat/big-brain/commit/e179cb53fa981a0cf08352590ce36799f7ee0235))
* **bevy:** Migrated to Bevy 0.12 (#86) ([69c3a4a5](https://github.com/zkat/big-brain/commit/69c3a4a506fb5bcb94e26d87cccdb27cc180429a))
* **bevy:** Update to bevy 0.12.1 (#87) ([6befa384](https://github.com/zkat/big-brain/commit/6befa3844aec54b31886ff52f3e9f596ea57e088))
* **thinker:** make ThinkerBuilder be Clone ([2e493d6b](https://github.com/zkat/big-brain/commit/2e493d6bb7339bd278a597555b707aa379eebbcb))
* **generics:** support generic actions (#88) ([7f5a3845](https://github.com/zkat/big-brain/commit/7f5a3845947e40f5a2c6460060eaef3ec5649804))

### Bug Fixes

* **despawn:** don't try to despawn if an entity doesn't exist ([bdf51c32](https://github.com/zkat/big-brain/commit/bdf51c3206e9afa6b35c1f5a199c6465c3086217))

<a name="0.18.0"></a>
## 0.18.0 (2023-07-16)

### Features

* **bevy:** Update to bevy 0.11 (#79) ([72bb861f](https://github.com/zkat/big-brain/commit/72bb861f9b17f7bc052ff33bf4e4a3ab2876775a))

<a name="0.17.0"></a>
## 0.17.0 (2023-03-06)

### Features

* **bevy:** Update to bevy 0.10 (#72) ([66ece025](https://github.com/zkat/big-brain/commit/66ece025a0b296decf8a0fe4c301b78bd0971d77))

<a name="0.16.0"></a>
## 0.16.0 (2023-01-30)

Probably the biggest change in this release is removal of the blanket
`ActionBuilder` and `ScorerBuilder` implementations for `Clone` types. This is
a fairly significant breaking change, but one that is fairly easy to resolve:
simply use the new `#[derive(ActionBuilder)]` and `#[derive(ScorerBuilder)]`
macros to derive the necessary implementations for your Action and Scorer
Components and you should be good to go.

### Features

* **derive:** Add derive macros for Action and Scorer (#65) ([359bccef](https://github.com/zkat/big-brain/commit/359bccef46f67d286c7f89cbe1b93b7b37b46588))
    * **BREAKING CHANGE**: This gets rid of the blanket implementation for Action/ScorerBuilder on Clone things, and instead requires that people use derive macros (or manually implement the traits), if they want to go the clone-to-instantiate route.
* **concurrenty:** Add ConcurrentMode configuration to Concurrently Action (#68) ([f6d04feb](https://github.com/zkat/big-brain/commit/f6d04feb18927250304554467da2cb1c6583fc2d))
* **reflection:** Implement Reflect trait for all relevant types (#69) ([31543c78](https://github.com/zkat/big-brain/commit/31543c78bd398e7781ced90701e73691b265a6ce))

### Bug Fixes

* **typo:** fix scorer argument name (#63) ([5be71335](https://github.com/zkat/big-brain/commit/5be71335b3a4429ed05c1d3e0969dc521400df09))
* **derive:** some tweaks to new derive macros ([4a622a90](https://github.com/zkat/big-brain/commit/4a622a90bf895d35ec255971b5ca7d1c5c95b120))

<a name="0.15.0"></a>
## 0.15.0 (2022-11-13)

### Features

* **deps:** Update to Bevy 0.9 (#59) ([8ce5cd1b](https://github.com/zkat/big-brain/commit/8ce5cd1b57a2de0c10bcbc1c1686187d680134d9))

### Bug Fixes

* **spans:** Make ActionSpan::new() private ([4486af1d](https://github.com/zkat/big-brain/commit/4486af1db83fc4fdf50acd2eacfa7d96e64501f3))
    * **BREAKING CHANGE**: This function was previously public, but it was never meant to be used.

<a name="0.14.0"></a>
## 0.14.0 (2022-09-25)

This is a fairly beefy release. The two main changes are the addition of
significant new observability features, which let you debug/trace both
big-brain and your own Scorers and Actions more easily in an integrated
manner. Additionally, a new advanced composite Scorer was added,
MeasuredScorer, which can be used to create some interesting behaviors when
you have want to factor in multiple scorers when adding cases to Thinker.

Besides that, there's several bugfixes to long-standing bugs and a couple of
other features.

Enjoy!

### Features

* **entities:** Rename ActionEnt and ScorerEnt to Action and Scorer ([43f37959](https://github.com/zkat/big-brain/commit/43f3795929a4a67806a3a50113e9573d7dc95895))
    * **BREAKING CHANGE**: These are externally-exported, so you'll have to rename them yourself, too
* **tracing:** add tracing support for Thinker/Action/Scorer (#55) ([a32bc01d](https://github.com/zkat/big-brain/commit/a32bc01d4280bad060f998782f03cbf82ce481cf))
    * **BREAKING CHANGE**: In the process of doing this, `spawn_action` and `spawn_scorer` were moved out of `ActionBuilder` and `ScorerBuilder` traits, respectively. This will likely affect any user-side composite actions and scorers. Use `scorers::spawn_scorer` and `actions::spawn_action` instead.
* **thinker:** Add support for scheduling one-off Actions on a Thinker (#57) ([382d2014](https://github.com/zkat/big-brain/commit/382d20148d654ac65027e4ec68d964eb37364cac))
* **measures:** Implement MeasuredScorer and some initial measures (#54) ([c6a6c5c9](https://github.com/zkat/big-brain/commit/c6a6c5c9d685c14f13b3906097a7231a3d648718))

### Bug Fixes

* **actions,scorers:** Transform/GlobalTransform are no longer needed for hierarchies. ([df10f034](https://github.com/zkat/big-brain/commit/df10f034595d2f8800e4c68473c6039e4754a1ec))
* **tracing:** fix warnings and wrong cfg feature name ([5ff39632](https://github.com/zkat/big-brain/commit/5ff396326e236aa4b408503696cf46121183e520))
* **thinker:** `otherwise` clause no longer overrides running action (#56) ([849ab346](https://github.com/zkat/big-brain/commit/849ab3460e17c47796d2f5948b002973867411a1))
    * **BREAKING CHANGE**: This patch changes the behavior for `otherwise` such that it won't override an existing action if it's still running, but it'll still execute as soon as that action finishes. I think this is really what people expect this to do, so let's give it a shot!
* **tracing:** drop action span scope before spawning next action ([ee899e4a](https://github.com/zkat/big-brain/commit/ee899e4a841fbfaf3c1e3541171a7533cd339ec2))

<a name="0.13.0"></a>
## 0.13.0 (2022-09-21)

### Features

* **scorers:** make ScorerEnt public (#50) ([9e6d7f63](https://github.com/zkat/big-brain/commit/9e6d7f63f52f66ad6e80914913aad37c00570bb3))
* **scorers:** make FixedScore members pub (#49) ([f0ddb9e5](https://github.com/zkat/big-brain/commit/f0ddb9e51cf96956b73ca2d7fc25812def676fef))
* **picker:** Implement a Highest Picker (#52) ([4b48f94d](https://github.com/zkat/big-brain/commit/4b48f94d7221eedcaa1a64a6d2f100022f79164b))
* **scorers:** Add ProductOfScorers composite scorer (#51) ([e425e234](https://github.com/zkat/big-brain/commit/e425e2348a53cd675070b4f2a3e7076242012c8b))
* **actions:** make ActionEnt public, too ([fc30e752](https://github.com/zkat/big-brain/commit/fc30e752c66aa887f62a899827e5a8c9910eeec3))
* **prelude:** Add ScorerEnt and ActionEnt to the prelude ([08b0598b](https://github.com/zkat/big-brain/commit/08b0598b1cd1fa5cae68932012ff20d76d0acbf6))

<a name="0.12.0"></a>
## 0.12.0 (2022-08-01)

### Features

* **bevy:** Upgrade to Bevy 0.8. (#43) ([0f0c4479](https://github.com/zkat/big-brain/commit/0f0c4479ab84cc60dae3a8fdaab1d560807f0e3f))

<a name="0.11.0"></a>
## 0.11.0 (2022-05-05)

### Features

* **deps:** upgrade to Bevy 0.7. (#37) ([38688789](https://github.com/zkat/big-brain/commit/38688789d08547e1cbc0d2a373fc58af39dea360))

<a name="0.10.0"></a>
## 0.10.0 (2022-01-15)

This is my first pass at a significant API improvement. I iterated on it for a
while and this is what I settled on. I look forward to continuing to evolve
this API as I get more feedback and experience with it! Please let me know
what you think!

### Breaking Changes

* **thinker:** stop cancelling actions when they go under Picker thresholds ([4c72b3d1](https://github.com/zkat/big-brain/commit/4c72b3d11eaa42af4b99ccf9ea729306e589ada8))
* **stages:** Strongly typed stages for BigBrainPlugin ([65ca646e](https://github.com/zkat/big-brain/commit/65ca646e3b92b178025591878e2df6a08714880f))
* **builders:** Blanket impls for ActionBuilder and ScorerBuilder when Clone ([8bed75b5](https://github.com/zkat/big-brain/commit/8bed75b54a43c72b53fbf9e2605b942cb2c53214))
* **api:** rename attach and hide it from docs ([6c64df4f](https://github.com/zkat/big-brain/commit/6c64df4fc1211abe19919a3628476b930b6e9919))
* **choice:** return &Choice instead of cloning ([a76dcbb6](https://github.com/zkat/big-brain/commit/a76dcbb67d4f6ae402f03d22e8d526408d8d875f))

### Features

* **example:** update thirst example ([edecc4c9](https://github.com/zkat/big-brain/commit/edecc4c95f76bcd69c042372140486f744f4ccea))

### Bug Fixes

* **hierarchy:** make sure all the hierarchy stuff is set up properly ([372c13e2](https://github.com/zkat/big-brain/commit/372c13e207523ec919c6490682f628f7d21cebea))
* **tests:** update tests ([94e1b1f6](https://github.com/zkat/big-brain/commit/94e1b1f685e6ab0be9d90bae5dfbd648ba87f1de))

<a name="0.9.0"></a>
## 0.9.0 (2022-01-09)

### Features

* **deps:** update for bevy 0.6 (#31) ([b97f9273](https://github.com/zkat/big-brain/commit/b97f9273c5f5eceb010d8fa2b23abb534fb2cee1))
* **perf:** Use SparseSet for ActionState ([5fc08176](https://github.com/zkat/big-brain/commit/5fc081765c1ed8788a7a5d1e940efbc66dc8aa8f))

<a name="0.8.0"></a>
## 0.8.0 (2021-09-19)

### Bug Fixes

* **systems:** Fix steps, add a test and explicit systems ordering (#27) ([f33315c9](https://github.com/zkat/big-brain/commit/f33315c9b7b769a94baab17e3a9df9f5ebe924d2)) (credit: [@payload](https://github.com/payload))

<a name="0.7.0"></a>
## 0.7.0 (2021-09-16)

### Bug Fixes

* **deps:** Don't include Bevy default features when used as a dependency. (#25) ([61558137](https://github.com/zkat/big-brain/commit/615581370a165645795966ac7c878ff492630ba2))

### Features

* **license:** change license to Apache-2.0 ([d7d17772](https://github.com/zkat/big-brain/commit/d7d177729476af8ec1463d8957a35092a336098a))
    * **BREAKING CHANGE**: This is a significant licensing change. Please review.

<a name="0.6.0"></a>
## 0.6.0 (2021-05-20)

#### Features

* **pickers:**  Make choices mod public (#23) ([92034cd0](https://github.com/zkat/big-brain/commit/92034cd04e629723893cfcd7730ce597083da9e7))
* **scorers:**  Added EvaluatingScorer (#24) ([1a1d5b3d](https://github.com/zkat/big-brain/commit/1a1d5b3d17d96a51084418128f0bfebe0ad8c702))

#### Bug Fixes

* **actions:**  Concurrently was not setting its state to Failure ([d4a689f6](https://github.com/zkat/big-brain/commit/d4a689f6c60f509a71fb3a9ae4ca49dad263acab))


<a name="0.5.0"></a>
## 0.5.0 (2021-04-27)

Got a few goodies in this release, mainly focused around composite actions and
scorers, which were apparently broken.

Shout out again to [@piedoomy](https://github.com/piedoomy) for some of these
contributions!

#### Features

* **actions:**  Add new Concurrently composite action ([6c736374](https://github.com/zkat/big-brain/commit/6c736374b4afd60af592a357ad2403304d3638d1))
* **evaluators:**  added inversed linear evaluator helper (#19) ([f871d19e](https://github.com/zkat/big-brain/commit/f871d19e93b6764088d6db5db1947fcb37143868))
* **scorers:**  Added WinningScorer composite scorer (#20) ([748b30ae](https://github.com/zkat/big-brain/commit/748b30aedcb0711f4180a8e24b457f01f0b84f6a))

#### Breaking Changes

* **scorers:** Composite Scorers now all use `.push()` instead of a mixture of `.push()` and `.when()`. Please update any usages of composite scorers ([63bad1fd](https://github.com/zkat/big-brain/commit/63bad1fd2c82eadc88107003dd819f3cfa7530a2)

#### Bug Fixes

* **scorers:**
  *  Scorer builders now properly return themselves ([63bad1fd](https://github.com/zkat/big-brain/commit/63bad1fd2c82eadc88107003dd819f3cfa7530a2)
  *  Fixed error where wrong component for `SumOfScorers` was attached (#21) ([71fd05a6](https://github.com/zkat/big-brain/commit/71fd05a64912b2cc88c76439543ea00a00267303))



<a name="0.4.0"></a>
## 0.4.0 (2021-04-26)

#### Breaking Changes

* **score:**  scores are now 0.0..=1.0, not 0.0..=100.0 ([71f5122e](https://github.com/zkat/big-brain/commit/71f5122e9f5aa5b5965ad67f53ae9850f487d167), breaks [#](https://github.com/zkat/big-brain/issues/))

#### Features

* **evaluators:**  Make all evaluators Clone ([4d5a5121](https://github.com/zkat/big-brain/commit/4d5a512171bf6f850893424c5baad03b0e686c26))


<a name="0.3.5"></a>
## 0.3.5 (2021-04-24)

Previously, if a `Picker` re-picked the same action, and that action had been
set to `Success` or `Failure`, it would just keep running the action in that
state until it was time to switch to a different one.

With this version, that behavior is changed, and `Failure` and `Success`
actions that are re-picked will be respawned entirely (not even reused).

Cheers to [@piedoomy](https://github.com/piedoomy) on Discord for pointing out
this weird behavior!

#### Bug Fixes

* **thinker:**  launch a new action when the current action is in an end state ([80d23f2f](https://github.com/zkat/big-brain/commit/80d23f2f2337a863c9cc3afbf944b25e3911db8c))


<a name="0.3.4"></a>
## 0.3.4 (2021-04-23)

Welp. Turns out Thinkers were completely broken? This should work better :)

#### Bug Fixes

* **prelude:**  Export ThinkerBuilder from prelude ([06cc03e1](https://github.com/zkat/big-brain/commit/06cc03e1dd563c708bff276f7a194c8c81a00a5a))
* **thinker:**
  *  disposed of ActiveThinker and circular state-setting ([7f8ed12b](https://github.com/zkat/big-brain/commit/7f8ed12b112152c3f8d548d0a2208cefdb1581af))
  *  Need to do proper ptr_eq comparison here ([037a7c0d](https://github.com/zkat/big-brain/commit/037a7c0d0da065ea4cb5642047302d6bda13c670))


<a name="0.3.3"></a>
## 0.3.3 (2021-04-18)

This fixes an issue with more children being added to an Actor causing Thinkers to get clobbered in really annoying ways.

#### Bug Fixes

* **thinker:**  stop using the child/parent system for toplevel thinkers ([db16e2f6](https://github.com/zkat/big-brain/commit/db16e2f6ee97777b4df12e4ae435bf27b8012c7c))


<a name="0.3.2"></a>
## 0.3.2 (2021-04-17)

This is a quick bugfix. Shoutout to [@ndarilek](https://github.com/ndarilek)
for finding this one and giving me a chance to debug it!

tl;dr: Bevy's hierarchy system *requires* that all children have `Transform`
and `GlobalTransform` also attached, otherwise it just... kills them.

#### Bug Fixes

* **scorer:**  stop attaching duplicate scorers ([10a6d022](https://github.com/zkat/big-brain/commit/10a6d022ec682e33b98309318020c9068be4cea2))
* **thinker:**  add Transform and GlobalTransform ([ed3a7cb3](https://github.com/zkat/big-brain/commit/ed3a7cb3c03e27b76b374f75ac179f29c979e4cf))

<a name="0.3.1"></a>
## 0.3.1 (2021-04-14)

Just a quick release because I broke docs.rs :)

#### Bug Fixes

* **build:**  remove .cargo/config.toml to make docs.rs happy ([393d9807](https://github.com/zkat/big-brain/commit/393d9807576d21c7234667b1f9914f1886579bd0))


<a name="0.3.0"></a>
## 0.3.0 (2021-04-14)

This is a major overhaul of the Bevy API. It removes `.ron` support
altogether, in favor of plain old Rust builders.

#### Breaking Changes

* The `.ron` Thinker definition API is gone. Use the ThinkerBuilder API instead.
* The `Action` and `Scorer` derive macros are gone, including all of `big_brain_derive`.
* Measures and Weights are gone.
* `big-brain` no longer exports everything from the toplevel. Use `big_brain::prelude::*` instead.

#### Bug Fixes

Probably.

#### Features

* New builder-based Thinker API!
* Composite Scorers: `FixedScore`, `AllOrNothing`, and `SumOfScorers`.
* Composite Action: `Steps`, for sequential Action execution.
