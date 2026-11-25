# Agentic SDLC comparison — scoring rubric & standards

Stable standards for re-running or extending the five-product agentic SDLC comparison. Any session or model must follow this file (and `skills/agentic-sdlc-comparison/SKILL.md`) so scores stay comparable.

## Products in scope (column order — do not change without updating all tables)

1. **Claude Code** (Anthropic)
2. **Antigravity** → public match: **Google Antigravity** (`antigravity.google`; Gemini / DeepMind-associated models). State this assumption if the name is ambiguous.
3. **GitHub Copilot** (current agents — app, CLI, IDE, cloud, review, Agent Merge, automations). **Do not** score sunset Copilot Workspace (TP ended 2025-05-30) as current.
4. **Codex** (OpenAI Codex CLI / App / Cloud / GitHub Action / PR review)
5. **Cursor** (Agent, Plan Mode, Cloud Agents, Bugbot, Automations, Rollouts, first-party plugins)
6. **Best-in-class** (thought experiment: unlimited resources, no regulations — any vendor)

## SDLC row hierarchy (required)

Parent stages, then children:

- **Plan** → Requirements; Architecture / tech selection
- **Design** → UX; API / schema
- **Build** → Implement; Refactor; Review
- **Test** → Unit; Integration; End-to-end
- **Deploy** → CI/CD; Release; Infra
- **Maintain** → Monitor; Incident response; Debt / refactor

Parent scores are **judgmental rollups**, not arithmetic averages of children.

## Score scale (0–5)

| Score | Meaning |
| --- | --- |
| **0** | No built-in tool; human operates the stage fully |
| **1** | Assistive text only; no reliable act/verify loop |
| **2** | Partial automation; heavy human setup; thin/fragile coverage |
| **3** | Meaningful HITL automation for common workflows; human still drives most decisions/gates |
| **4** | Strong built-in agent loop (plan/act/verify); human typically reviews/approves rather than executes |
| **5** | Fully autonomous built-in tooling with unattended completion as a **documented** product capability |

## Hard rules

1. **Evidence:** Base claims on latest **public** official docs / product pages / first-party announcements. Cite URLs. On refresh, re-fetch and HTTP-check primary links.
2. **Conservative:** If docs are unclear, preview-only, or marketing-only → score lower and say so. Do **not** invent features.
3. **Built-in preferred:** Count first-party product surfaces and official CI actions / first-party MCP plugins. Do **not** inflate scores for “could do it with generic chat + custom MCP.”
4. **Product vs methodology:** Methodology articles (e.g. Anthropic AI-native SDLC playbook `intent.md`/`spec.md`/`plan.md`) may be cited under Mechanic/Sources as optional patterns. Do **not** list them as product **Tools** unless the product docs expose them as a first-party command/UI.
5. **Gaps to 5:** Every scored cell must state what is missing for a 5.
6. **Tools + mechanic:** Every cell must name the **tool(s)** and the **mechanic** (how the loop works: trigger → act → verify → handoff). Tool names must match current vendor docs.
7. **No authoritative overall average:** Do not treat an equal-weight mean as the decision metric. Provide a priority-based decision guide. Optional illustrative averages must be labeled non-authoritative.
8. **Best-in-class column:** Name concrete industry tools and score them with the same rubric; still conservative.
9. **Output paths:** User-facing deliverable → `docs/agentic-sdlc-model-comparison.md`. Working notes → `internal/`. Do not invent features to fill gaps.
10. **Verification notes:** After a full Tools/Mechanic re-verify, append dated findings (what was stale, what changed, confidence) under `internal/`.

## Required cell content

### Score matrix layout

- **One** HTML `<table>` (not six separate markdown tables).
- Column 1: parent SDLC stage (`Plan` … `Maintain`) with **`rowspan`** across that stage’s child rows.
- Column 2: child stage.
- Then product columns in fixed order: Claude Code | Antigravity | GitHub Copilot | Codex | Cursor | Best-in-class.

### Score matrix cell content

For each product × child-stage cell, include **all** of:

- **Autonomy meter** — for score **N/5** show plain-text **`■`×N + `□`×(5−N)** plus `N/5`, e.g. `■■■□□ 3/5`.
  - **Do not use SVG** for meters (Project Library / many MD sanitizers strip SVG).
  - Do not use `●`/`○` or gray-filled stand-ins.
- **Tools** — short named features
- **Loop** — one-line mechanic
- **Deep dive →** link to the matching explanation anchor

### Deep dive (per product × sub-stage)

- Expand **Tools**, step-by-step **Mechanic**, **Human role**, **Gaps to ●●●●●** (full autonomy), **Sources**
- Bidirectional links with stable unique IDs (no spaces):
  - Matrix cell: `id="m-{stage}-{child}-{product}"` on the `<td>` (e.g. `m-plan-requirements-cursor`)
  - Deep dive: `<h5 id="d-{stage}-{child}-{product}">` (heading targets scroll more reliably than empty anchors)
  - Forward: matrix → `#d-…` · Back: deep dive → `#m-…` (**exact cell**, not `#score-matrix`)
  - Do **not** add a separate markdown link index or “viewer compatibility / if links don’t work” fallback section
  - Prefer prose/word links in Sources (e.g. `[Plan Mode](https://…)`) over raw URL dumps or dense clickable link lists

## Research date

Stamp `Research date: YYYY-MM-DD` at the top of the deliverable on every refresh.
