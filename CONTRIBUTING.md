# Contributing

We welcome contributions! Please follow these guidelines to ensure a smooth collaboration.

## Getting Help

Before opening an issue, please check our [SUPPORT](SUPPORT.md) guide for resources and contact channels.

## Security

If you discover a security vulnerability, please follow the instructions in [SECURITY](SECURITY.md). Do not open public issues for security concerns.

## Development Workflow

### Versioning

This project follows [Semantic Versioning](https://semver.org).

### Branching Model

This project uses [git-flow-next](https://git-flow.sh) for branching and release strategy.

We use a lightweight git-flow model with automated releases:

- **`main`**: Production-ready code. Every commit triggers a **release** workflow and publish a new version.
- **`develop`**: Integration branch for features. Every commit triggers an **alpha release** workflow and publishes an `-alpha` version.
- **`feature/*`**: New features (branch off `develop`).
- **`bugfix/*`**: Bug fixes for the upcoming release (branch off `develop`). Similar to `feature/*` but for fixes.
- **`hotfix/*`**: Quick fixes for production (branch off `main`).
- **`release/*`**: Release preparation (branch off `develop`). Often none is done here since releases are automated.
- **`support/*`**: Maintenance for older versions (branch off `main`).

### Git worktrees

Use [Git Worktrees](https://git-scm.com/docs/git-worktree) to work on multiple features in parallel without constantly switching branches in the main directory or invalidating caches.

```sh
# Create a worktree for a feature branch
git worktree add .worktrees/my-feature -b feature/my-feature
cd .worktrees/my-feature

# Fresh environment
pnpm install
pnpm exec projen

# When done
cd ../..
git worktree remove .worktrees/my-feature
```

## Monorepo Management

Managed by [NX](https://nx.dev) and [Projen](https://projen.io). Configuration is centralized in [.projenrc.ts](.projenrc.ts).

### Bootstrap

Bootstrap the development environment.

```sh
pnpm install
pnpm exec projen
```

### Package & Dependency Management

All changes (new packages, dependencies, settings) start in [.projenrc.ts](.projenrc.ts).

- **Add Package**: Define the package in [.projenrc.ts](.projenrc.ts), then run `pnpm exec projen`.
- **Manage Dependencies**: Add/remove in [.projenrc.ts](.projenrc.ts), then run `pnpm exec projen`.
- **Upgrade**: Run `pnpm exec projen upgrade`.
- **Visualize**: Run `pnpm exec projen graph`.

### Cache

Nx automatically caches build outputs. If you run a build and nothing has changed, it will restore the output from the cache, significantly speeding up execution.

- **Clear Cache**: If you run into issues, you can force a rebuild by passing `--skip-nx-cache` to Nx commands or manually deleting `.nx/cache` and `node_modules/`.

### Build

Perform a full build of the codebase in dependency order.

```sh
pnpm exec projen build
```

### Test

Run tests across all packages.

```sh
pnpm exec projen test
```

### Synth & Deploy

Synthesize and deploy infrastructure via AWS CDK.

```sh
pnpm exec projen synth
pnpm exec projen deploy
```

### Extra

Advanced commands for targeting specific packages or tasks.

- **Run task in specific package**:

    ```sh
    pnpm exec nx run <package>:<task>
    ```

- **Run task in all packages**:

    ```sh
    pnpm exec projen run-many --targets=<task> --output-style=stream --nx-bail
    ```

## Code Standards

- **Commits**: Follow [Conventional Commits](https://www.conventionalcommits.org).
- **Style**: Prettier and ESLint are enforced. Run `pnpm exec projen eslint` to fix formatting.
- **Documentation**: Update `README.md` and package docs if you change behavior.
- **Diagrams**: Use [Mermaid](https://mermaid.js.org) for diagrams embedded in Markdown. Use [D2](https://d2lang.com) for richer diagrams that you keep as source (store in `docs/` or alongside the related documentation).

## Pull Requests

1. Ensure all tests pass (`pnpm exec projen test`).
2. Update documentation if needed.
3. Open a PR against `develop` (for features) or `main` (for hotfixes).
4. Link relevant issues.

## License

By contributing to this repository, you agree that your contributions will be licensed under the [License](LICENSE).

## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.
