# setup-kluctl-actions

Composite GitHub Action that downloads and caches the kluctl binary on Linux, macOS, and Windows.

## Verify

CI tests the composite action from the current checkout on Ubuntu and Windows, then runs actionlint, zizmor, and strict Renovate validation. The required gate is `check`.

## Stack

Follows https://github.com/BlackDark/agent-presets/blob/main/stack/core.md.

Deviation: the action's public `version` input still defaults to `latest` for compatibility. Callers that need reproducible builds must pass an exact kluctl version.

## Map

- `action.yml`: OS/architecture selection, version resolution, cache, download, and PATH setup.
- `.github/workflows/test.yml`: cross-platform action test and config linting.

## Git

- Conventional Commits, one topic per PR.
- Squash unless commits need separate review.
- Force-push only with `--force-with-lease` on own branches.

## Boundaries

- Do not publish action tags from a local session.
- Keep download URLs and versions away from direct expression interpolation in shell code.
