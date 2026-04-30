# Plinth

**The load-bearing base for enterprise internal tooling.**

You run a fleet of internal applications — project management, change requests, audit dashboards, HR tooling, internal admin. Modules that began as starters and grew. Every module re-implements the same plumbing: identity, authorization, audit, observability, deployment. Every module inherits the same gaps: a session secret committed in `.env.example`, an authorization layer that fails open in dev mode, no real healthcheck, no error boundaries, no centralized logs.

Plinth is the platform foundation those modules should have stood on from day one. A substrate, an SDK, a scaffolder — assembled into something a small platform team can deploy, and let dozens of modules grow on top of without each one becoming the platform's weakest link.

It is six commitments.

## Zero standing trust

No human or service has ambient privileges. Identity is established per request — users authenticate at the gateway via OIDC; services authenticate to each other via mTLS with workload identity. Secrets are time-bounded; admin actions are audited; production access is just-in-time.

There is no long-lived bastion key. There is no "this database password has been the same since 2019."

## GitOps everything

The state of the platform is the state of git. A reconciler agent applies the repo to the cluster; humans don't `kubectl apply`. Every change is reviewed in a pull request, recorded in audit, reversible by `git revert`.

Configuration drift between environments is structurally impossible, because configuration *is* the git contents.

## Immutable infrastructure

Nodes are not patched; they are replaced. Cluster nodes have no SSH and no shell — configuration is declarative manifests, applied atomically with rollback. Container images are built once, signed, and never mutated in flight.

The phrase "I just edited the file on the box" is a deployment incident.

## Durable workflows

Long-running, multi-step business processes — approvals, integrations, scheduled jobs, retries against flaky dependencies — live in a workflow engine, not in cron and database tables and handler-level retry loops. Code is the source of truth; correctness is testable.

A pod dying mid-transition does not leave indeterminate state.

## Evidence by default

Audit, traces, logs, metrics, and policy decisions are emitted from every component without per-module effort. The platform produces compliance evidence as a side effect of running.

When an auditor asks "who deleted record X on 12 March?", the answer is one query away — not a forensic excavation through git logs and chat history.

## Open source first

Every component is permissively licensed open-source software, self-hostable on-premise. Plinth must be operable indefinitely without recurring vendor cost. Commercial support contracts are welcome — and recommended for Tier 1 components in year one — but optional. No proprietary extensions. No "open core" where the useful features are paid.

---

Plinth is MIT-licensed end to end. The substrate, the SDK, the scaffolder, the docs — all of it. Fork it, ship it commercially, modify it for your regulator. No obligations.

It is opinionated where opinions reduce cognitive load, and silent where teams differ. The opinions are listed above. If you disagree with them, Plinth is not for you — fork it, or pick something else. If you agree with them, the four-step "Try it" tutorial is at [plinth.run](https://plinth.run).

## Get started

```bash
# Stand up the platform on a fresh Kubernetes cluster
helm install plinth oci://ghcr.io/plinth-dev/platform --values dev.values.yaml

# Generate a fully-wired module
plinth new my-module --web --api
```

## Repositories

| Repo | What it is |
| --- | --- |
| [`platform`](https://github.com/plinth-dev/platform) | Helm umbrella chart and Talos cluster bootstrap. The substrate. |
| [`sdk-go`](https://github.com/plinth-dev/sdk-go) | Go SDK packages — fail-closed authz, audit, OTel, typed errors, and more. |
| [`sdk-ts`](https://github.com/plinth-dev/sdk-ts) | TypeScript SDK packages — `@plinth-dev/authz-react`, `api-client`, `forms`, `tables`, and more. |
| [`starter-web`](https://github.com/plinth-dev/starter-web) | Next.js 16 module starter, wired to the SDK. |
| [`starter-api`](https://github.com/plinth-dev/starter-api) | Go 1.23 module starter, wired to the SDK. |
| [`cli`](https://github.com/plinth-dev/cli) | The `plinth` CLI for scaffolding new modules. |
| [`scaffolder`](https://github.com/plinth-dev/scaffolder) | Backstage software template — same output as the CLI, in-portal. |
| [`docs`](https://github.com/plinth-dev/docs) | Source for [plinth.run](https://plinth.run) — architecture, tutorials, ADRs. |

## Community

- **Bugs and features**: file an issue on the relevant repo.
- **Questions and proposals**: open a Discussion on [`platform`](https://github.com/plinth-dev/platform/discussions) or [`docs`](https://github.com/plinth-dev/docs/discussions).
- **Security disclosures**: `security@plinth.run`. See `SECURITY.md` in any repo for the full policy.
- **Contributing**: small-scoped PRs preferred. See [`CONTRIBUTING.md`](https://github.com/plinth-dev/.github/blob/main/CONTRIBUTING.md).
- **Code of Conduct**: Contributor Covenant 2.1.
