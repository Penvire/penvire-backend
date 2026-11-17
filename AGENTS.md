# Penvire backend

All backend services of Penvire, from tenants and engagements to evidence, findings and reporting. Authentication uses Keycloak or another OpenID provider; Penvire never ships hand-written authentication.

## Repository map

```text
build-logic/            Gradle convention plugins shared by all services
services/<service>/     one Quarkus service each, hexagonal:
  src/main/java/.../<service>/
    domain/             entities and rules, no framework code
    application/        use cases and ports
    adapter/in/         REST
    adapter/out/        database, Kafka, other services
infrastructure/local/   local Traefik, TLS and compose files
docs/agents/            agent instructions
```

## Development environment

Enter the environment with `devenv shell`, or run `direnv allow` once. It provides Java 25 and Gradle 9 (running on JDK 25). Always run tools through it.

Git hooks run automatically: a commit-msg hook rejects messages that are not Conventional Commits (the same rule as CI), and actionlint checks workflow files.

There is no Gradle build yet. Once the wrapper exists, use `./gradlew build` and `./gradlew test`; never a global `gradle`.

## Rules

- Never push to `main`. Create a branch (`feat/`, `fix/` or `chore/`), push it and open a pull request. The maintainer merges.
- Pull requests are squash-merged. The PR title becomes the commit on `main`, so it must be a Conventional Commit; mark breaking changes with `!`.
- Commits are GPG-signed; `main` rejects unsigned commits.
- PR body: a one-paragraph summary, then a `## Test plan` section.
- Releases are managed by release-please. Do not bump versions or edit `CHANGELOG.md` by hand.
- The PR title becomes the changelog entry. Keep one user-facing change per PR. If a PR contains several, list every `feat` and `fix` on its own line in the PR description, between `BEGIN_COMMIT_OVERRIDE` and `END_COMMIT_OVERRIDE`; release-please uses that block instead of the title.
- Penvire never ships hand-written authentication.

## Agent docs

- [Issue tracker](docs/agents/issue-tracker.md): GitHub Issues for `Penvire/penvire-backend`
- [Triage labels](docs/agents/triage-labels.md)
- [Domain docs](docs/agents/domain.md): where the glossary and ADRs live

## Related repositories

- `~/Projects/penvire/prod/contracts`: [penvire-contracts](https://github.com/Penvire/penvire-contracts)
- `~/Projects/penvire/prod/clients`: [penvire-clients](https://github.com/Penvire/penvire-clients)
- `~/Projects/penvire/prod/docs`: [penvire-docs](https://github.com/Penvire/penvire-docs), the product documentation
