# Release on Push Test

This repository is to test https://github.com/marketplace/actions/tag-release-on-push-action

[Example Release](https://github.com/ld-codes/release-on-push-test/releases/tag/v1.0.0)

## How-to

1. Create a PR from develop to main

2. Merge a PR

It will automatically bump a patch version and create a release in Github

NOTE:

- If you want to change bump version attach `release:major`/`release:minor`/`release:patch` label to the PR
- If you want to skip a release, attach `norelease` label to teh PR
