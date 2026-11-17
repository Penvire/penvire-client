# Penvire clients

User-facing apps of Penvire: a React web UI, an Electron desktop app, an iOS app and an Android app, plus shared packages.

## Repository map

```text
apps/web/          React web UI
apps/desktop/      Electron app, reuses the web UI's React code
apps/ios/          Swift, Xcode project
apps/android/      Kotlin, Gradle
packages/ui/       React components shared by web and desktop
packages/theme/    design tokens, also exported for iOS and Android
packages/login-theme/  Keycloakify login theme
```

## Development environment

Enter the environment with `devenv shell`, or run `direnv allow` once. It provides Node 24 and pnpm. Android SDK and iOS tooling are added with the first mobile app; iOS builds need macOS and Xcode. Always run tools through it.

Git hooks run automatically: a commit-msg hook rejects messages that are not Conventional Commits (the same rule as CI), and actionlint checks workflow files.

No workspace yet. Once `pnpm-workspace.yaml` exists: `pnpm install`, then `pnpm --filter <app> <script>`.

## Rules

- Never push to `main`. Create a branch (`feat/`, `fix/` or `chore/`), push it and open a pull request. The maintainer merges.
- Pull requests are squash-merged. The PR title becomes the commit on `main`, so it must be a Conventional Commit; mark breaking changes with `!`.
- Commits are GPG-signed; `main` rejects unsigned commits.
- PR body: a one-paragraph summary, then a `## Test plan` section.
- Releases are managed by release-please. Do not bump versions or edit `CHANGELOG.md` by hand.
- The PR title becomes the changelog entry. Keep one user-facing change per PR. If a PR contains several, list every `feat` and `fix` on its own line in the PR description, between `BEGIN_COMMIT_OVERRIDE` and `END_COMMIT_OVERRIDE`; release-please uses that block instead of the title.
- Penvire never ships hand-written authentication.

## Agent docs

- [Issue tracker](docs/agents/issue-tracker.md): GitHub Issues for `Penvire/penvire-clients`
- [Triage labels](docs/agents/triage-labels.md)
- [Domain docs](docs/agents/domain.md): where the glossary and ADRs live

## Related repositories

- `~/Projects/penvire/prod/contracts`: [penvire-contracts](https://github.com/Penvire/penvire-contracts)
- `~/Projects/penvire/prod/backend`: [penvire-backend](https://github.com/Penvire/penvire-backend)
- `~/Projects/penvire/prod/docs`: [penvire-docs](https://github.com/Penvire/penvire-docs), the product documentation
