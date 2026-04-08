# Renovate bot in this repository

## What Renovate is

Renovate bot is a tool for automatic dependency updates in a repository. It
scans project files, finds outdated package versions, container images, and
GitHub Actions, then creates pull requests with proposed updates.

## Main capabilities

- automatic dependency discovery across many ecosystems
- pull request creation for available updates
- separation of major, minor, and patch updates
- grouping related updates into a single pull request
- scheduling, labels, dashboard support, and approval rules
- support for Docker, GitHub Actions, npm, Maven, Gradle, pip, and many other managers

## How it is configured in this project

Renovate runs in this repository through [`.github/workflows/renovate.yml`](/c:/Users/eip10/docker_ubuntu/07.04-lab_01/.github/workflows/renovate.yml),
and the main rules are stored in [`renovate.json`](/c:/Users/eip10/docker_ubuntu/07.04-lab_01/renovate.json).

Current configuration:

- checks dependencies in `Dockerfile`
- checks GitHub Actions versions in `.github/workflows/*.yml`
- creates a `Dependency Dashboard`
- runs twice a week on schedule and also supports manual launch
- groups safe `minor`, `patch`, and `digest` updates separately for Docker and GitHub Actions
- requires manual approval for major updates through the dashboard
- adds `dependencies` and `renovate` labels to pull requests

## What will be updated here

- the base container image in [Dockerfile](/c:/Users/eip10/docker_ubuntu/07.04-lab_01/Dockerfile)
- GitHub Actions in [ci-cd.yml](/c:/Users/eip10/docker_ubuntu/07.04-lab_01/.github/workflows/ci-cd.yml)
- the Renovate GitHub Action version in [renovate.yml](/c:/Users/eip10/docker_ubuntu/07.04-lab_01/.github/workflows/renovate.yml)

## How to enable it on GitHub

1. Push the repository to GitHub.
2. Make sure GitHub Actions are enabled for the repository.
3. Optionally add a `RENOVATE_TOKEN` secret with a Personal Access Token.
4. Run the `Renovate` workflow manually from the Actions tab.

## Token note

If only `GITHUB_TOKEN` is used, most standard updates should still work. For
more reliable updates of GitHub workflow files, it is better to add a separate
`RENOVATE_TOKEN` with the required permissions.
