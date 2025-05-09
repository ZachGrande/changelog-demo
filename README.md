# Changelog Demo

This project demonstrates the automatic maintenance of `CHANGELOG.md` via GitHub Actions

## Changelog Generation

Changelogs are generated using [`github-changelog-generator`](https://github.com/github-changelog-generator/github-changelog-generator)

## Development Lifecycle

This project uses [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).

### Contribute to an issue

- Take an issue off the board: [Issues](https://github.com/ZachGrande/changelog-demo/issues)
- Make a new branch from `develop` with the convention `{name}-{issue #}-{short description}`
- Open a Pull Request against `develop`
  - Begin the PR description with "Closes `{issue #}`"
- Request a review

### Cutting a release

Updates are deployed from a release branch. The branch is automatically generated using an Action. Changelog updates will be generated during this process and added to the release branch.

- Merge desired Pull Requests into `develop`
- Run the [Cut a Release](https://github.com/ZachGrande/changelog-demo/actions/workflows/cut-release.yml) workflow
  - Suffix for the release branch: the current day's date
    - e.g., `20250509`
    - If multiple PRs in one day, append `-b`, `-c`, etc.
  - Tag for the release: follow [semantic versioning](https://semver.org/)
    - e.g., `v1.0.0`

### Deploy a Release

Not implemented

### Finalize a Release

After the release is deployed, make `main` and `develop` consistent.

- Run the [Finalize a Release](https://github.com/ZachGrande/changelog-demo/actions/workflows/finalize-release.yml) workflow
