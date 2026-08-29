# LiteAd Logic Games — AI Project Context

## Instructions for AI assistants

Read this complete file before suggesting, generating or modifying code.

Also read:

* `README.md`
* `Start_Here.md`
* `pubspec.yaml`
* Relevant existing source files

Do not assume the project structure, packages, current implementation or completed functionality without inspecting them.

Preserve all working functionality unless the requested change explicitly requires modification.

## Project objective

LiteAd Logic Games is a Flutter game hub containing multiple lightweight logic and board games in one Android application.

Current planned games:

* Memory Match
* Dots and Boxes
* Connect Four
* Block Puzzle

The games share one home screen, theme and common services while retaining independent code and assets.

## Repository structure

```text
lib/
├── main.dart
├── app/
├── core/
├── shared/
└── features/
    ├── home/
    ├── memory_match/
    ├── dots_and_boxes/
    ├── connect_four/
    ├── block_puzzle/
    ├── payments/
    ├── progress/
    ├── parent_gate/
    └── updates/
```

Every game feature should follow:

```text
feature_name/
├── data/
├── logic/
├── models/
├── screens/
└── widgets/
```

Assets are separate from source code:

```text
assets/
├── common/
├── memory_match/
├── dots_and_boxes/
├── connect_four/
└── block_puzzle/
```

Rules:

* Dart code belongs under `lib/`.
* Images, audio and content files belong under `assets/`.
* Reusable functionality belongs under `core/` or `shared/`.
* Game-specific functionality must remain inside its feature folder.
* Avoid generic filenames such as `screen.dart`.
* Use descriptive names such as `memory_match_screen.dart`.
* Do not restructure the project without explicit approval.

## Git workflow

`main` is the stable branch.

Never make normal feature changes directly on `main`.

Required process:

```text
Switch to main
→ Pull latest main
→ Create a descriptive branch
→ Implement
→ Test
→ Commit
→ Push the feature branch
→ Create Pull Request
→ Review Files changed
→ Merge into main
```

Branch examples:

```text
feature/memory-match
feature/payment-system
feature/parent-gate
fix/progress-not-saved
hotfix/app-crash
```

Do not:

* Exchange individual source files manually
* Ask someone to copy a file into a particular folder
* Use ZIP files as normal version control
* Overwrite the complete project
* Force-add generated folders
* Commit passwords, secrets or signing files
* Rewrite shared Git history without explicit approval

## App-size requirements

Preferred release download/package target:

```text
Below 50 MB
```

Current absolute internal ceiling:

```text
100 MB
```

Before adding large images, audio, animations, fonts or packages, assess their impact on app size.

After meaningful additions, build the release AAB and review its size.

If one hub eventually becomes too large, create a separate, logically grouped app rather than allowing uncontrolled growth.

## Monetisation principles

The product should avoid advertisements, particularly intrusive advertising.

The preferred model is free access followed by an optional premium unlock.

Current direction:

* No mandatory LiteAd account
* No questionnaire before trying the app
* No fake AI assessment
* No forced seven-day trial
* No payment information required for free content
* Users must experience meaningful content before seeing a purchase requirement
* Free content remains replayable
* Purchase screens must clearly explain what is unlocked
* Include **Not now**
* Include **Restore purchase**
* Clearly disclose recurring billing and cancellation terms

Where level-based games are used, the current proposal is:

```text
Levels 1–10: Free
Level 11 onward: Premium
```

This rule must not be forced onto games that do not naturally use levels. Their free/premium boundary requires a separate product decision.

Provisional pricing direction:

```text
India monthly: approximately ₹99
Europe monthly: approximately €1.99
```

Possible options requiring final approval:

* Monthly subscription
* Annual subscription
* Lifetime purchase

Never hard-code displayed prices. Retrieve localized prices from Google Play Billing.

## Payment implementation

Use Google Play Billing for digital content sold through the Android app.

Do not introduce Stripe, Razorpay or another payment provider unless explicitly approved and legally/policy-compliant for the intended distribution.

Payment requirements include:

* Google Payments merchant profile
* Play Console subscription or one-time products
* Purchase acknowledgement
* Purchase verification
* Restore Purchase support
* Subscription expiry handling
* Cancellation handling
* Refund and revocation handling
* Regional pricing
* License-tester validation

A secure backend is preferred for verifying purchases and monitoring subscription status.

Never store premium access as an easily editable local boolean without verification.

## Parent protection

If the app is offered to children or includes children in its target audience:

* Follow Google Play Families requirements
* Complete an accurate Data Safety declaration
* Maintain a privacy policy
* Avoid unnecessary personal-data collection
* Place purchasing and external links behind a parent gate
* Avoid manipulative purchase prompts
* Ensure cancellation and pricing information is clear

A parent gate may use an adult-level action or question. It must not falsely claim to verify identity.

## Registration and progress

The current preference is no LiteAd registration.

Google Play can restore eligible purchases using the purchasing Google account.

Limitation:

* Purchase restoration and game-progress synchronization are different.
* Without LiteAd login or cloud-save functionality, progress may remain only on the device.
* Reinstalling or changing devices may restore the purchase but not completed levels.

Do not claim cross-device progress synchronization unless it has actually been implemented and tested.

## Update strategy

Google Play controls normal automatic updates according to the user’s device settings. The app cannot silently override those settings.

Planned approach:

* Optional update for cosmetic or minor releases
* Immediate in-app update for critical releases
* Minimum-supported-version control when old versions must no longer be used
* Offline grace period before enforcing a mandatory update
* Do not permanently deny paid users access to already-downloaded content solely because they are temporarily offline

The exact offline grace period is not yet finalized.

## Offline behaviour

Core downloaded games should work offline wherever practical.

Internet may still be required for:

* Initial purchase
* Purchase verification
* Restoring purchases
* Checking mandatory updates
* Downloading future online content, if introduced

Do not unexpectedly require a continuous internet connection for ordinary gameplay unless explicitly approved.

## Quality and testing

Each feature must be tested independently and as part of the complete hub.

Test:

* Game rules and win/lose conditions
* Level progression where applicable
* Saved progress
* Free/premium boundaries
* Purchase restoration
* Subscription expiry
* Parent gate
* Mandatory updates
* Offline behaviour
* Back navigation
* Sound controls
* Different Android screen sizes
* App restart and device restart
* Repeated tapping and invalid inputs
* Performance and app size

Do not mark a feature complete merely because it compiles.

## AI coding rules

Before producing code, an AI assistant must:

1. Inspect the relevant existing files.
2. Confirm the active feature and requested scope.
3. Identify files that will be created or modified.
4. Reuse established architecture and naming.
5. Avoid unrelated refactoring.
6. Preserve existing behaviour.
7. Provide or update tests where appropriate.
8. Run formatting and analysis.
9. Report remaining limitations honestly.

Minimum checks after code changes:

```bash
dart format .
flutter analyze
flutter test
```

Run the app or relevant build when the environment allows it.

Do not:

* Invent packages without checking compatibility
* Replace working code unnecessarily
* Place an entire game in `main.dart`
* Create duplicate services or models
* Mix unrelated games inside one feature folder
* Modify payment, signing or release configuration casually
* Claim that something was tested when it was not
* Commit generated build outputs
* Expose secrets in code, logs or documentation

## Decision status

Confirmed direction:

* Flutter-based modular game hub
* Standard feature-first folder structure
* Stable `main` plus feature branches
* No individual-file exchange workflow
* Preferred size below 50 MB
* No intrusive ads
* No unnecessary registration
* Google Play Billing for Android digital purchases
* Parent protection for child-facing purchase actions
* Immediate-update support for critical versions
* Honest, clearly explained free and premium access

Provisional decisions requiring confirmation before implementation:

* Exact premium boundary for every game
* Exact monthly, annualgit and lifetime prices
* Whether every plan will be offered
* Backend provider
* Offline update grace period
* Cloud progress synchronization
* Final target age groups
* Final list and order of launch games

When a requirement is unclear, do not silently decide it. Record the question and request a product decision.
