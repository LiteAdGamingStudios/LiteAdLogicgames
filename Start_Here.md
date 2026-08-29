# LiteAd Logic Games — Team Instructions

Follow these instructions after accepting the GitHub collaborator invitation.

## 1. Required software

Install:

* Git
* Android Studio
* Flutter SDK
* Flutter and Dart plugins in Android Studio

Verify Flutter from a terminal:

```bash
flutter doctor
```

Resolve any major errors before continuing.

## 2. Copy the repository link

Open the GitHub repository:

```text
https://github.com/LiteAdGamingStudios/LiteAdLogicgames
```

Click:

```text
Code → HTTPS → Copy
```

Do not use Download ZIP.

## 3. Clone through Android Studio

Open Android Studio and select:

```text
Get from Version Control
```

If another project is already open:

```text
VCS → Get from Version Control
```

Enter:

```text
URL:
https://github.com/LiteAdGamingStudios/LiteAdLogicgames.git
```

Recommended local directory:

```text
C:\lite_ad_studios\games\litead_logic_games
```

Click **Clone**.

The local drive location may differ between computers. Git will still download the same internal project structure.

Do not run `flutter create`. The repository already contains the complete Flutter project.

## 4. Download project dependencies

Open Android Studio’s terminal inside the cloned project and run:

```bash
flutter pub get
```

Do not copy `.dart_tool` or `.idea` from another developer. Flutter and Android Studio create these folders locally.

## 5. Configure Flutter if Android Studio requests it

If Flutter SDK is not configured:

```text
Settings → Languages & Frameworks → Flutter
```

Select the Flutter SDK installation folder.

Example only:

```text
E:\Flutter
```

Do not copy this example blindly. Select the actual Flutter installation on your computer.

The Dart SDK should then be detected automatically from:

```text
<Flutter SDK>\bin\cache\dart-sdk
```

## 6. Confirm that the project opens correctly

Run:

```bash
git status
```

The expected result is:

```text
On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

Then run the app once before modifying anything.

## 7. Always update `main` before starting work

Run:

```bash
git switch main
git pull origin main
```

This downloads the latest approved project version.

Do not begin work using an outdated copy.

## 8. Create a branch for assigned work

Never develop directly on `main`.

Create a branch with a descriptive name:

```bash
git switch -c feature/memory-match
```

Examples:

```text
feature/memory-match
feature/dots-and-boxes
feature/parent-gate
feature/payment-system
fix/level-progress-error
fix/app-crash
```

The branch name should clearly describe the assigned work.

## 9. Work only in the correct feature folders

Example for Memory Match code:

```text
lib/features/memory_match/
├── data/
├── logic/
├── models/
├── screens/
└── widgets/
```

Example for Memory Match media:

```text
assets/memory_match/
├── audio/
├── data/
└── images/
```

Rules:

* Dart source code goes under `lib/`.
* Images, audio and content files go under `assets/`.
* Do not rename or restructure existing folders without approval.
* Do not send or upload individual files separately.
* Do not provide instructions asking others to manually place files.
* Never upload passwords, API secrets, keystores or signing passwords.

## 10. Check your changes

Run:

```bash
git status
```

Review all changed and new files before staging them.

Add all intended changes:

```bash
git add .
```

Check again:

```bash
git status
```

Green files are staged for the next commit.

## 11. Commit the work

Use a meaningful commit message:

```bash
git commit -m "Add Memory Match game screen"
```

Good examples:

```text
Add Memory Match level data
Add card-flip animation
Fix duplicate card selection
Add Memory Match sound assets
```

Avoid unclear messages such as:

```text
update
changes
final
new code
```

## 12. Push the feature branch

Push the current branch:

```bash
git push -u origin feature/memory-match
```

Replace `feature/memory-match` with the actual branch name.

Do not push feature work directly to `main`.

## 13. Create a Pull Request

After pushing:

1. Open the repository on GitHub.
2. Select **Pull requests**.
3. Click **New pull request**.
4. Set the base branch to `main`.
5. Select your feature branch for comparison.
6. Review **Files changed**.
7. Add a clear title and summary.
8. Create the Pull Request.
9. Wait for review before merging.

## 14. After the Pull Request is merged

Update the local project:

```bash
git switch main
git pull origin main
```

Delete the completed local branch:

```bash
git branch -d feature/memory-match
```

If GitHub did not delete the remote branch:

```bash
git push origin --delete feature/memory-match
```

## 15. Daily working rule

Always follow this sequence:

```text
Switch to main
→ Pull latest main
→ Create a feature branch
→ Develop
→ Test
→ Check git status
→ Git add
→ Commit
→ Push the feature branch
→ Create Pull Request
→ Review
→ Merge
```

## Important restrictions

* Do not work directly on `main`.
* Do not use Download ZIP for normal development.
* Do not manually replace the complete project folder.
* Do not upload files individually using GitHub’s Add file button.
* Do not force-add `.dart_tool`, `.idea`, build outputs or secrets.
* Do not merge an untested feature.
* Pull the latest `main` before starting any new assignment.
