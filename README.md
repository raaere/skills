# Agent Skills

A reusable collection of engineering-focused Agent Skills, designed for reliable, evidence-based development workflows across compatible coding agents.

> **Status: Planning.** This repository has not published any installable skills yet. The initial skill, `inspect`, has a design specification but has not been implemented or validated.

## Goals

- Keep each skill focused, discoverable, and easy to invoke.
- Prefer verified repository evidence over assumptions.
- Adapt inspection and verification effort to risk and impact.
- Keep implementation, review, documentation, and validation responsibilities explicit.
- Make results measurable with clear completion criteria and evaluation cases.
- Preserve owner control over consequential or irreversible actions.

## Design Principles

1. **Clarity:** Write precise, actionable instructions in professional technical English.
2. **Single responsibility:** Give each skill a distinct purpose and activation conditions.
3. **Composability:** Allow skills to participate in larger workflows without making them mutually dependent.
4. **Progressive disclosure:** Keep `SKILL.md` concise; add references and scripts only when warranted.
5. **Evidence-based execution:** Report what was actually inspected, changed, and validated.
6. **Risk-adaptive depth:** Scale effort to task complexity and potential impact.
7. **Safe boundaries:** A skill never grants permissions beyond those of the user and host agent.

## Planned Skills

| Skill | Responsibility | Status |
| --- | --- | --- |
| `inspect` | Establish repository context, assess risk, and report findings without making changes. | Design v1.0; not implemented |
| `spec` | Define requirements, scope, acceptance criteria, and implementation constraints. | Planned |
| `build` | Implement approved changes in accordance with project conventions and specifications. | Planned |
| `verify` | Run relevant checks and report actual validation evidence. | Planned |
| `review` | Review implementation quality, correctness, and architecture impact. | Planned |
| `docs` | Keep technical documentation aligned with the verified implementation. | Planned |

The names above are proposed skill identifiers, not a declaration that these skills are currently available.

## Proposed Repository Layout

```text
skills/
├── README.md
├── skills/
│   ├── inspect/
│   │   ├── SKILL.md
│   │   ├── references/      # Optional
│   │   └── scripts/         # Optional
│   ├── spec/
│   ├── build/
│   ├── verify/
│   ├── review/
│   └── docs/
└── tests/                    # Future evaluation fixtures
```

This is a target structure, not the current repository contents. Each published skill will contain a `SKILL.md` with valid frontmatter, including a short `name` and a precise `description`.

## First Skill: `inspect`

`inspect` is intended to establish a reliable baseline before engineering changes. It is read-only by default and uses three inspection levels:

| Level | Typical scope | Example |
| --- | --- | --- |
| **L1 — Quick** | Applicable instructions, Git state, target files, obvious risks. | Localized UI change |
| **L2 — Focused** | L1 plus relevant interfaces, dependencies, tests, and regression impact. | Business-logic or shared API change |
| **L3 — Deep** | Risk-scoped architectural, security, data-integrity, and operational analysis. | Authentication, migration, or infrastructure change |

The agent starts with minimal discovery, chooses an appropriate level, and escalates when new evidence reveals additional risk. Deep inspection does **not** mean reading every file.

### `inspect` Safety Contract

- Do not modify repository files or Git state.
- Do not install dependencies, deploy, or modify external resources.
- Do not run commands with unassessed side effects.
- Do not expose secrets or confidential configuration values.
- Distinguish confirmed facts, inferences, unknowns, and unexecuted checks.
- Report blockers and request owner decisions when required.

## Installation (After Publication)

Once skills have been added and validated, the intended installer is the open-source Skills CLI:

```bash
npx skills@latest add raaere/skills
```

To request a global installation, where supported:

```bash
npx skills@latest add raaere/skills -g
```

**Not yet actionable:** The repository does not yet contain any installable skills. It is also **private**, so installation requires an authenticated environment with repository access; anonymous installs cannot be assumed to work. Actual compatibility and installation will be verified after publication.

Skills may then be invoked explicitly, for example with `$inspect` in agents that support that syntax, or selected automatically when the host agent's skill-discovery behavior and the task description match. Automatic selection is not guaranteed and must be evaluated.

## Quality and Evaluation

Before a skill is considered ready for release:

1. Validate skill metadata and folder structure.
2. Test explicit invocation and relevant automatic activation behavior.
3. Test cases where the skill **must not** activate.
4. Evaluate representative low-, medium-, and high-risk scenarios.
5. Confirm that safety boundaries are maintained.
6. Record evidence for all passing checks; disclose any skipped or failed checks.
7. Verify that documentation matches the released implementation.

**Status definitions:** `NOT STARTED`, `IN PROGRESS`, `BLOCKED`, `PARTIALLY COMPLETED`, `COMPLETED`, and `VERIFIED` must reflect actual work and evidence. No skill is considered verified solely because its specification or documentation is complete.

## Development Workflow

```text
Design → Implement → Evaluate → Review → Release
```

Each phase should have an explicit scope and acceptance criteria. Repository-wide or externally consequential changes remain subject to the owner's authorization. Skills define reusable workflows; they do not independently provide autonomous orchestration, background execution, or broader permissions.

## Language Policy

Reusable skill names, metadata, instructions, references, and technical specifications use professional technical English. User-facing explanations and reports follow the user's preferred language (Thai by default).

## Acknowledgments

This project draws engineering inspiration from:

- [Matt Pocock — Skills](https://github.com/mattpocock/skills)
- [AI Hero](https://www.aihero.dev/)
- [Agent Skills](https://agentskills.io/)
- [OpenAI Codex Skills documentation](https://developers.openai.com/codex/skills)

These references inform the design approach; this repository is independently maintained and is not presented as affiliated with or endorsed by their authors.

## License

No license has been selected. The repository is private, and no open-source usage permission should be inferred. A license can be added if the owner decides to distribute it publicly.
