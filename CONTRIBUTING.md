# Contributing

Use this guide for workflow, commands, and contribution expectations.

## Getting Help

Before opening an issue, check [SUPPORT](SUPPORT.md) for support channels and
escalation paths.

## Security

If you discover a security issue, follow [SECURITY](SECURITY.md). Do not file
public issues for security-sensitive problems.

## Development Workflow

### Versioning

This project follows [Semantic Versioning](https://semver.org).

### Branching Model

This project uses [git-flow-next](https://git-flow.sh):

- **`main`**: production-ready releases
- **`develop`**: integration and alpha releases
- **`feature/*`** and **`bugfix/*`**: work targeting `develop`
- **`release/*`**: release preparation from `develop`
- **`hotfix/*`**: production fixes from `main`
- **`support/*`**: maintenance for older releases

### Git Worktrees

Use [Git worktrees](https://git-scm.com/docs/git-worktree) for parallel feature
work without switching the main checkout.

## Style Guide

- **TypeScript**:
  [Google TypeScript](https://google.github.io/styleguide/tsguide)
- **Python**: [Google Python](https://google.github.io/styleguide/pyguide)
- **Go**: [Google Go](https://google.github.io/styleguide/go/guide)
- **Web**: [Google HTML/CSS](https://google.github.io/styleguide/htmlcssguide)
- **Documentation**:
  [Google Markdown](https://google.github.io/styleguide/docguide/style)

Local formatters and package constraints take precedence. Keep related
statements and their error handling together; separate logical blocks with a
blank line. Use highlighted **NOTE**, **INFO**, **TODO**, **FIXME**, and
**WARNING** comment prefixes for useful sections, context, follow-ups, defects,
and hazards, using the language's comment syntax. Explain what the code cannot
show.

## Code Standards

Prefer existing capabilities and clear responsibilities. Use
[Refactoring.Guru](https://refactoring.guru/refactoring/smells) to identify code
smells and improve affected code without speculative abstractions. Preserve
validation, error handling, compatibility, and observable behavior. Document
public APIs with the language's docstrings, using TSDoc for TypeScript; explain
contracts and material defaults or side effects without repeating types. Update
the owning docs when behavior changes.

## Review

Follow
[Google's review guidance](https://google.github.io/eng-practices/review/reviewer)
for correctness, design, simplicity, tests, readability, and documentation.

## Pull Requests

- **Commits**: follow
  [Conventional Commits](https://www.conventionalcommits.org).
- **Scope**: keep each PR focused; explain its intent and link relevant issues.
- **Verification**: run the affected `AGENTS.md` commands and include evidence.
- **Documentation**: update durable guidance when commands, behavior, or package
  boundaries change.
- **Target**: use `develop` for feature work and `main` for hotfixes.

## License

By contributing to this repository, you agree that your contributions will be
licensed under the [LICENSE](LICENSE).

## Code of Conduct

This project is released with a
[Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this
project you agree to abide by its terms.
