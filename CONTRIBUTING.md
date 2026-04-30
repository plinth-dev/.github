# Contributing to Plinth

Thanks for considering a contribution. Plinth is open source from day one and built to be modified — by you, by your team, by your regulator. This guide is the short version of how we work.

## Where to start

- **Bugs and feature requests**: file an issue on the relevant repo. Use the templates.
- **Questions and proposals**: open a [Discussion](https://github.com/plinth-dev/platform/discussions) — issues are for actionable work.
- **Security disclosures**: do **not** file an issue. Email `security@plinth.run`. See [SECURITY.md](./SECURITY.md).
- **Looking for a first issue?** Filter by the [`good first issue`](https://github.com/search?q=org%3Aplinth-dev+label%3A%22good+first+issue%22+state%3Aopen&type=issues) label across the org.

## Pull request norms

- **Small scope.** A PR should do one thing. If you find yourself writing "and also", split.
- **Tests included.** New behavior gets new tests. Bug fixes get a regression test.
- **No drive-by reformatting.** Format-only changes go in a separate PR labelled `chore: format`.
- **Conventional commit titles.** `fix:`, `feat:`, `docs:`, `chore:`, `refactor:`, `test:`, `perf:`, `build:`, `ci:`. The PR title is what lands in the squashed commit.
- **DCO sign-off.** Use `git commit -s`. Every commit must be signed off; CI enforces this.

## Local development

Each repo has its own `README.md` with the local commands. The umbrella expectations:

- **Go repos** target Go 1.23. `go test ./... -race` must pass.
- **TS repos** use pnpm 10. `pnpm install --frozen-lockfile && pnpm -r build && pnpm -r test` must pass.
- **`pre-commit`** is recommended; configs live in each repo.

## Review SLA

- A maintainer **acknowledges** every PR within **3 working days**.
- First substantive review within **5 working days** for PRs ≤ 200 lines, **10 working days** otherwise.
- We're a small team. If a PR is sitting, ping it in the relevant repo's Discussions thread.

## Decisions

We record non-obvious decisions as ADRs in [`plinth-dev/docs/src/content/docs/adr/`](https://github.com/plinth-dev/docs/tree/main/src/content/docs/adr) using the [Michael Nygard format](https://github.com/joelparkerhenderson/architecture-decision-record/blob/main/locations/nygard/index.md).

Major design changes are proposed as RFCs in [`plinth-dev/.github/rfcs/`](./rfcs/) — open a PR adding `NNNN-title.md` from the [template](./rfcs/0000-template.md).

## Code of conduct

By participating, you agree to abide by our [Code of Conduct](./CODE_OF_CONDUCT.md). Violations: report to `conduct@plinth.run`.

## License

By contributing, you agree your contribution is licensed under the [MIT License](./LICENSE), the project's license.
