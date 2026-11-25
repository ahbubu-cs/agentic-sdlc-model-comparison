---
name: agentic-sdlc-comparison
description: >-
  Research and update the five-product agentic SDLC comparison (Claude Code,
  Antigravity/Google Antigravity, GitHub Copilot, Codex, Cursor + best-in-class).
  Use when refreshing scores, adding stages, or re-running the comparison in a
  new session or with a different model.
---

# Agentic SDLC comparison skill

## When to use

- User asks to compare AI coding platforms for **agentic SDLC** automation
- User asks to **refresh**, **extend**, or **re-score** the comparison
- A new session must reproduce the same standards as prior work

## Before writing

1. Read and obey:
   - `docs/standards/agentic-sdlc-comparison-rubric.md` (scoring, column order, hard rules)
   - Existing deliverable `docs/agentic-sdlc-model-comparison.md` (update in place unless asked otherwise)
2. List tracked tasks if in a Project; report status to the coordinator when applicable.
3. Research with **current public docs** (official docs, product pages, first-party announcements). Prefer fetch of primary URLs over secondary blogs.

## Products & column order (fixed)

Write tables in this order:

1. Claude Code  
2. Antigravity (Google Antigravity — state assumption)  
3. GitHub Copilot (current agents only; Workspace is sunset)  
4. Codex  
5. Cursor  
6. Best-in-class  

## Stages (fixed hierarchy)

Plan (Requirements; Architecture) → Design (UX; API/schema) → Build (Implement; Refactor; Review) → Test (Unit; Integration; E2E) → Deploy (CI/CD; Release; Infra) → Maintain (Monitor; Incident; Debt/refactor).

## Output contract

1. **User-facing:** update `docs/agentic-sdlc-model-comparison.md` to include:
   - Methodology + research date + autonomy-meter legend
   - **One HTML score matrix** with parent-stage `rowspan`, child-stage column, then products
   - Each cell: meter + tools + one-line loop + **Deep dive →**
   - **Meter rule:** plain text `■`×N + `□`×(5−N) + `N/5` (e.g. `■■■□□ 3/5`). **No SVG** (Library strips it).
   - **Deep dive** with tools, step-by-step mechanic, human role, gaps to full autonomy, sources; targets are `<h5 id="d-…">`
   - Bidirectional anchors: `m-…` on matrix `<td>` ↔ `d-…` on deep-dive heading (keep these; no separate link-index or viewer-compatibility fallback section)
   - Sources as prose/word links (e.g. `[Plan Mode](https://…)`), not raw URL dumps
   - Decision guide by priority (no authoritative overall average)
   - Short primary-sources prose list (entry points; detail lives in Deep dive)
2. **Internal:** append/update research notes under `internal/` (e.g. `internal/agentic-sdlc-research-notes.md`) with source index and assumptions. Use matching `cursor.subagentId` frontmatter when creating agent reports.
3. **Do not open a PR** unless the user explicitly asks to put this in a git repo.

## Scoring discipline

- Rubric 0–5 from `docs/standards/agentic-sdlc-comparison-rubric.md`
- Conservative; cite URLs; name tools + mechanic; always gaps-to-5
- MCP / custom wiring does not equal a high built-in score
- Score **5** only when docs describe unattended end-to-end completion for that stage

## Refresh checklist

- [ ] Re-fetch official docs for each product (prefer vendor docs over blogs)  
- [ ] Confirm Antigravity identity still = Google Antigravity  
- [ ] Confirm Copilot Workspace still sunset / not scored  
- [ ] Update research / re-verification date  
- [ ] For **every** cell: confirm named tools still exist under current product names  
- [ ] Confirm mechanics match documented product behavior (do not invent loops)  
- [ ] Separate **product surfaces** from **methodology articles** (e.g. Anthropic SDLC playbook `intent.md` is methodology, not a Claude Code command)  
- [ ] Probe primary source URLs (HTTP 200) and replace dead links  
- [ ] Re-validate every score against Tools + Mechanic + Gaps to 5  
- [ ] Append what changed to `internal/` verification notes  
- [ ] Update decision guide if relative strengths change  
- [ ] Keep column order and stage hierarchy unchanged  
- [ ] Re-check 96 matrix↔deep-dive `m-`/`d-` pairs if structure changed  

## Prompt starter (paste into a new session)

```text
Follow skills/agentic-sdlc-comparison/SKILL.md and
docs/standards/agentic-sdlc-comparison-rubric.md.
Refresh docs/agentic-sdlc-model-comparison.md from latest public docs.
Keep column order: Claude Code | Antigravity | GitHub Copilot | Codex | Cursor | Best-in-class.
One HTML score matrix with parent-stage rowspan. Meter = plain ■/□ text (e.g. ■■■□□ 3/5), no SVG.
Every cell needs Score/meter, Tools, Mechanic, Gaps to 5, and source URLs.
Anchors: m-… ↔ d-… exact cell both ways; no link-index / viewer-compatibility fallback.
Sources as prose links. No overall average as the decision metric; keep a priority-based decision guide.
Write research notes under internal/. Do not open a PR unless I ask.
```
