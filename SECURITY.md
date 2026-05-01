# Security policy

Plinth is platform infrastructure. The security of the things you build on it depends on the security of the substrate, the SDK, the scaffolder, and the starters. We treat reports seriously and respond fast.

## Reporting a vulnerability

**Email `security@plinth.run`.** Do not file a public GitHub issue.

Include, where possible:

- A description of the vulnerability and its impact.
- Steps to reproduce, or a proof of concept.
- Affected versions, packages, and components.
- Whether the issue is already public; if so, where.

If you'd like to encrypt the report, ask in the same email and we'll respond with our PGP key. (We will publish a stable PGP key + fingerprint on the docs site as part of Phase F.)

## Response timeline

| Step | Target |
| --- | --- |
| Acknowledgement of receipt | within **2 working days** |
| Initial triage and severity assessment | within **5 working days** |
| Fix or mitigation merged | per severity (see below) |
| Public disclosure | coordinated with the reporter; default 90 days from initial report or 14 days after a fix ships, whichever is sooner |

### Severity targets for a fix

| Severity | Target |
| --- | --- |
| Critical (CVSS ≥ 9.0) | within 7 days |
| High (CVSS 7.0–8.9) | within 30 days |
| Medium (CVSS 4.0–6.9) | within 90 days |
| Low (CVSS < 4.0) | next minor release |

## Supported versions

While Plinth is in `0.x`, we patch the **most recent minor release** only. Once `1.0` ships, we will support the latest two minor releases for security fixes for one year each.

## Out of scope

- Vulnerabilities in upstream dependencies that we have not bundled or modified — please report those upstream and tell us so we can pin or work around them.
- Findings from automated scanners without a demonstrated impact.
- Social engineering, physical attacks, denial-of-service via traffic volume.

## Hall of fame

We publicly acknowledge reporters who request it. (The acknowledgements page lands as part of Phase F at `https://plinth.run/security/acknowledgements`. Until then, ask for acknowledgement in your report and we'll list you on the docs site when it ships.)
