# Contributing

We welcome contributions! Please follow these guidelines to ensure a smooth collaboration.

## Getting Help

Before opening an issue, please check our [SUPPORT](SUPPORT.md) guide for resources and contact channels.

## Security

If you discover a security vulnerability, please follow the instructions in [SECURITY](SECURITY.md). Do not open public issues for security concerns.

## Development Workflow

### Versioning

This project follows [Semantic Versioning](https://semver.org). Each release increases the version number according to the MAJOR.MINOR.PATCH format. For the available versions, see the tags on this repository.

### Branching Model

This project uses [git-flow-next](https://git-flow.sh) for branching and release strategy.

- **`main`**: Production-ready code.
- **`develop`**: Integration branch for features.
- **`feature/*`**: New features (branch off `develop`).
- **`bugfix/*`**: Bug fixes for the upcoming release (branch off `develop`).
- **`hotfix/*`**: Quick fixes for production (branch off `main`).
- **`release/*`**: Release preparation (branch off `develop`).
- **`support/*`**: Maintenance for older versions (branch off `main`).

### Getting Started with git-flow-next

1. **Install**: Follow instructions at [git-flow-next](https://git-flow.sh).
2. **Initialize**: Run `git flow init` in the repo root.
3. **Start a Feature**: `git flow feature start my-feature`
4. **Finish a Feature**: `git flow feature finish my-feature`

## Monorepo Management

Managed by [NX](https://nx.dev) and [Projen](https://projen.io). Configuration is centralized in [.projenrc.ts](.projenrc.ts).

### Package & Dependency Management

All changes (new packages, dependencies, settings) start in [.projenrc.ts](.projenrc.ts).

- **Add Package**: Define the package in [.projenrc.ts](.projenrc.ts), then run `projen`.
- **Manage Dependencies**: Add/remove in [.projenrc.ts](.projenrc.ts), then run `projen`.
- **Upgrade**: Run `projen upgrade-deps`.
- **Visualize**: Run `projen graph`.

### Cache

Nx automatically caches build outputs. If you run a build and nothing has changed, it will restore the output from the cache, significantly speeding up execution.

- **Clear Cache**: If you run into issues, you can force a rebuild by passing `--skip-nx-cache` to Nx commands or manually deleting `.nx/cache` and `node_modules/`.

### Test

Run tests across all packages.

```sh
projen test
```

### Build

Perform a full build of the codebase in dependency order.

```sh
projen build
```

### Synth & Deploy

Synthesize and deploy infrastructure via AWS CDK.

```sh
projen synth
projen deploy
```

### Extra

Advanced commands for targeting specific packages or tasks.

- **Run task in specific package**:

    ```sh
    nx run <package>:<task>
    ```

- **Run task in all packages**:

    ```sh
    projen run-many --targets=<task> --output-style=stream --nx-bail
    ```

## Code Standards

- **Commits**: Follow [Conventional Commits](https://www.conventionalcommits.org).
- **Style**: Prettier and ESLint are enforced. Run `projen eslint` to fix formatting.
- **Documentation**: Update `README.md` and `AGENTS.md` in the relevant packages if you change behavior.
- **Diagrams**: We use [D2](https://d2lang.com) as the preferred language for diagrams (architecture, sequence, etc.). Store source files in `docs/` or alongside documentation.

## Pull Requests

1. Ensure all tests pass (`projen test`).
2. Update documentation if needed.
3. Open a PR against `develop` (for features) or `main` (for hotfixes).
4. Link relevant issues.

## License

By contributing to this repository, you agree that your contributions will be licensed under the [License](LICENSE).

## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.
