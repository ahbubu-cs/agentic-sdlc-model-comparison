# AI model comparison for Agentic SDLC

Project store for comparing coding-agent platforms on **built-in support for a fully automated agentic SDLC**.

## Start here

| Path | Purpose |
| --- | --- |
| [`docs/agentic-sdlc-model-comparison.md`](docs/agentic-sdlc-model-comparison.md) | **User-facing deliverable** — scores, tools, mechanics, gaps, decision guide |
| [`docs/standards/agentic-sdlc-comparison-rubric.md`](docs/standards/agentic-sdlc-comparison-rubric.md) | **Standards** — rubric, column order, hard rules (must follow on refresh) |
| [`skills/agentic-sdlc-comparison/SKILL.md`](skills/agentic-sdlc-comparison/SKILL.md) | **Skill** — instructions for any agent/session re-running the comparison |
| [`internal/agentic-sdlc-research-notes.md`](internal/agentic-sdlc-research-notes.md) | Working research notes / source index (not user-facing) |

## Products compared (fixed column order)

1. Claude Code (Anthropic)  
2. Antigravity → **Google Antigravity** (stated assumption)  
3. GitHub Copilot (current agents; Workspace sunset)  
4. Codex (OpenAI)  
5. Cursor  
6. Best-in-class (thought experiment)

## Re-run in another session or model

1. Open this Project / store.  
2. Point the agent at `skills/agentic-sdlc-comparison/SKILL.md` (or paste the prompt starter inside that skill).  
3. Require obedience to `docs/standards/agentic-sdlc-comparison-rubric.md`.  
4. Update `docs/agentic-sdlc-model-comparison.md` in place; put notes in `internal/`.  
5. Do **not** invent features; cite official docs; keep Tools + Mechanic + Gaps to 5 on every cell.

## Storage note

These files live in the **Cursor Project Agent Store**, not necessarily a git repository, unless you explicitly ask to commit them to a repo.
