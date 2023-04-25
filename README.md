# Release on Push Test

This repository is to test https://github.com/marketplace/actions/tag-release-on-push-action

[Example Release](https://github.com/ld-codes/release-on-push-test/releases/tag/v1.0.7)

## Workflows

### assign-label

Assigns a label to each pull request:

- If the PR title starts with "feat", the `feat` label is assigned.

  PRs with the `feat` label will be included in the "Exciting New Features" section of the release note.

- If the PR title starts with "fix", the `fix` label is assigned.

  PRs with the `fix` label will be included in the "Bugfixes" section of the release note.

- If the PR title or body contains "BREAKING CHANGE", the `breaking-change` label is assigned.

  PRs with the` breaking-change` label will be included in the "Breaking Changes" section of the release note.

- Other PRs will be included in the "Other Changes" section

- PRs with `release` or `norelease` labels will not be included in the release note.

### release-on-push

Creates a new GitHub release on every push to the main branch.

The default bump version scheme is patch, i.e. if the latest tag version is v1.0.0, then a push to the main branch will create a new release v1.0.1.

## FAQs

- So what does release process look like?

  - Developers create PRs to `develop` branch
  - These PRs will be automatically labeled by `assign-label` workflow
  - Once all of the PRs are merged, the release manager creates a PR from `develop` to `main`
  - The release PR will be labeled `release` by `assign-label` workflow
  - Based on the release version, the release manager may assign the following label to the release PR:
    - `norelease`, to skip the release
    - `release:patch`, to bump the version to the next patch
    - `release:minor`, to bump the version to the next minor
    - `release:major`, to bump the version to the next major
  - The release PR is merged, and the new release will be created by `release-on-push` workflow
  - The PR titles will be included in the relevant Release Notes sections according to their labels

- How to directly push to main without PR and skip the release process?

  - Add [norelease] to the commit message and directly push to the `main` branch

- Can I release individual commits?

  - No, it is not possible. You should push to `develop` branch first and create a PR from `develop` to `main`
