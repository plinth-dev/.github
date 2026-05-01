# Roadmap

Public roadmap for Plinth. Updated quarterly. The full per-phase exit criteria live in `PROJECT.md` §11; this is the short version for outside readers.

## Status

**Current**: Phase A — Foundation. Target completion: 2026-05-15.

## Phases

| Phase | What lands | Calendar target |
| --- | --- | --- |
| **A — Foundation** | Org, domain, npm scope, manifesto, docs site at plinth.run, eight cross-linked repos | weeks 1–2 |
| **B — SDK** | Go SDK (7 packages), TypeScript SDK (7 packages), each tagged v0.1.0 | weeks 3–6 |
| **C — Starters** | `starter-web` (Next.js 16), `starter-api` (Go 1.23), both importing the SDK | weeks 7–9 |
| **D — Substrate** | Helm umbrella chart that brings up the full reference architecture; Talos cluster bootstrap | weeks 10–14 |
| **E — Scaffolder** | `plinth new <module>` CLI; Backstage software template; identical output for the same inputs | weeks 15–17 |
| **F — Polish & launch** | Logo, examples gallery, ADRs, launch comms, CI baseline, security disclosure address | weeks 18–19 |

## Exit criteria for v0.1.0

The single end-to-end test that determines whether Plinth has shipped:

> An outside engineer, with only Docker installed, can — in under 60 minutes — read the docs, `helm install` the platform on a fresh kind cluster, run `plinth new <module>`, and watch their module reconcile in Argo CD.

If those four steps work end-to-end on a clean machine, v0.1.0 is done.

## After v0.1.0

The roadmap from v0.1.0 toward v1.0 is open. Likely themes — none committed:

- Bare-metal Talos hardening pass (vs. the kind-first Phase D).
- Cilium service-mesh tuning beyond the defaults.
- Examples gallery expansion (a tenth-module test of cognitive load).
- An audit-evidence export tool for compliance teams.
- A Plinth Cloud reference deployment (cloud is a target, not a service — see anti-goals).

Open an [issue](https://github.com/plinth-dev/platform/issues) tagged `roadmap` or a [Discussion](https://github.com/plinth-dev/platform/discussions) to propose additions.

## Versioning policy

- Every package and chart is semver from v0.1.0.
- Breaking changes within `0.x` are batched into minor versions.
- v1.0 freezes APIs for a year. We will not tag v1.0 until we have at least one production deployment outside the founding team and the API surface has been quiet for a quarter.

## Quarterly retros

Retros land as blog posts on the docs site (`/blog`, lands in Phase F). The first one is scheduled for the close of Phase B.
