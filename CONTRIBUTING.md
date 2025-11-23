# Contributing to Vestra

Thanks for your interest in contributing to Vestra — we appreciate any help, whether it's a bug fix, documentation improvement, or a new feature.

## How to contribute

- Discuss major features or breaking changes by opening an issue first so maintainers can provide feedback and avoid duplicated work.
- For small fixes or documentation changes, you can open a Pull Request directly.

## Getting started (local)

1. Fork the repository and clone your fork:

```bash
git clone https://github.com/TheFakeCreator/Vestra.git
cd vestra
```

2. Install dependencies (root and workspaces):

```powershell
pnpm -w install
```

3. Create a local env file from the example and update values:

```powershell
Copy-Item .env.example .env.local
# then edit .env.local
```

4. Run the apps you want to work on (examples):

```powershell
pnpm --filter ./packages/server dev
pnpm --filter ./packages/web dev
```

## Branching and pull requests

- Create a descriptive branch name: `feat/<short-description>` or `fix/<short-description>`.
- Keep changes focused — one logical change per PR.
- Write a clear PR title and description explaining the problem and your solution.
- Reference related issues in your PR description (e.g. `Closes #123`).

## Code style & tests

- Use TypeScript where possible. Keep code consistent with existing patterns.
- Run linters and formatters before opening a PR (we use ESLint + Prettier).
- Add tests for new functionality. Run tests with:

```powershell
pnpm -w test
```

## Commit messages

We follow Conventional Commits to keep history readable. Example:

```
feat(auth): add session refresh handler
fix(api): correct error handling for missing params
docs(readme): update deployment instructions
```

## Reviewing & merging

- PRs will be reviewed by maintainers. Please respond to review comments promptly.
- Squash or rebase commits as requested by maintainers.

## Reporting security issues

If you discover a security vulnerability, please do not open a public issue. Instead, contact the maintainers at `security@vestra.example.com` (replace with a real address later) so we can respond privately.

## Thank you

Thanks for helping Vestra — contributions are what make open source projects thrive.
