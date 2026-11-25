# Agentic SDLC tool comparison

Comparison of **built-in** tooling for a fully automated agentic software development lifecycle.

**Column order:** Claude Code → Antigravity → GitHub Copilot → Codex → Cursor → Best-in-class.

| Product | Scope scored |
| --- | --- |
| **Claude Code** | Anthropic Claude Code (CLI, IDE, Desktop, Web) + first-party GitHub Actions, Chrome, Code Review, hooks, cloud scheduled tasks (`/schedule`/routines, research preview), Slack `@Claude` / Claude Tag. |
| **Antigravity** | **Google Antigravity** (`antigravity.google`) — App, CLI `agy` (incl. headless `-p`), IDE extensions, SDK; `/plan`, artifacts, `/browser`, `/automation`, `/schedule`. Assumed public match for “Antigravity.” |
| **GitHub Copilot** | Current agents: app, CLI, IDE agent mode, Copilot in the cloud, code review, Agent Merge, automations / Agentic Workflows. **Copilot Workspace TP ended 2025-05-30 — not scored.** |
| **Codex** | OpenAI Codex CLI, App, Cloud environments, GitHub PR review, `openai/codex-action`. |
| **Cursor** | Agent, Plan Mode, Cloud Agents, Bugbot, Automations, Rollouts, first-party Figma plugin/MCP. |
| **Best-in-class** | Thought experiment (unlimited resources, no regulations): best current industry tools for that stage, any vendor. |

Standards: [`docs/standards/agentic-sdlc-comparison-rubric.md`](standards/agentic-sdlc-comparison-rubric.md) · Skill: [`skills/agentic-sdlc-comparison/SKILL.md`](../skills/agentic-sdlc-comparison/SKILL.md).

---

## Methodology

- **Research date:** 2026-11-24 (initial). **Re-verified against official public docs:** 2026-11-25.
- **Sources:** Official docs, product pages, first-party announcements (linked in [Deep dive](#deep-dive)). Claims require a living product surface or documented first-party methodology — methodology articles are cited as methodology, not as built-in product buttons.
- **Scope:** Built-in / first-party surfaces. Official CI actions and first-party MCP plugins count. Custom MCP wiring alone does **not** earn a high score.
- **Conservatism:** Unclear or preview-only → score down. Do not invent features.
- **Decision metric:** Stage capabilities only — **no authoritative overall average.** Use the [decision guide](#decision-guide).

### Autonomy meter

Score **N/5** is shown as **N filled squares (`■`) + (5−N) empty squares (`□`)**, always five characters, e.g. **3/5 → ■■■□□**. No SVG (Library preview often strips it).

| Meter | Level | Meaning |
| --- | --- | --- |
| □□□□□ <strong>0/5</strong> | 0/5 | No built-in tool; human operates fully |
| ■□□□□ <strong>1/5</strong> | 1/5 | Assistive text only; no reliable act/verify loop |
| ■■□□□ <strong>2/5</strong> | 2/5 | Partial automation; heavy setup; thin/fragile |
| ■■■□□ <strong>3/5</strong> | 3/5 | Meaningful HITL for common paths; human still drives |
| ■■■■□ <strong>4/5</strong> | 4/5 | Strong plan/act/verify loop; human typically approves |
| ■■■■■ <strong>5/5</strong> | 5/5 | Documented unattended completion for that stage |

**Matrix cells** show: meter · tools · loop · Deep dive link.  
**Deep dive** headings use <code>id="d-…"</code>; matrix cells use <code>id="m-…"</code>. Back link = **↑ matrix cell** to the exact cell.

## Score matrix

One HTML table. Parent stages use <code>rowspan</code>. Meter encoding: <strong>N×■ + (5−N)×□</strong> (example 3/5 → ■■■□□).

<a id="score-matrix" name="score-matrix"></a>
<div>
<table>
<thead><tr><th>SDLC stage</th><th>Child stage</th><th>Claude Code</th><th>Antigravity</th><th>GitHub Copilot</th><th>Codex</th><th>Cursor</th><th>Best-in-class</th></tr></thead>
<tbody><tr><td rowspan="2"><strong><a href="#deep-dive-plan">Plan</a></strong></td><td><a href="#d-plan-requirements"><strong>Requirements</strong></a></td><td id="m-plan-requirements-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>/plan</code> / plan permission mode, <code>CLAUDE.md</code>, skills, MCP<br><strong>Loop:</strong> explore → propose plan (no edits) → human accept → build<br><a href="#d-plan-requirements-claude"><strong>Deep dive →</strong></a></td><td id="m-plan-requirements-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>/plan</code>, Implementation Plan artifacts, <code>/agents</code>, rules (<code>AGENTS.md</code>/<code>GEMINI.md</code>), MCP<br><strong>Loop:</strong> explore → plan artifact → human edit/Proceed → execute<br><a href="#d-plan-requirements-antigravity"><strong>Deep dive →</strong></a></td><td id="m-plan-requirements-copilot">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> App/IDE/CLI Plan mode, Autopilot, cloud agent from issues<br><strong>Loop:</strong> issue/session → plan → approve → implement → PR<br><a href="#d-plan-requirements-copilot"><strong>Deep dive →</strong></a></td><td id="m-plan-requirements-codex">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> CLI/App/Cloud, <code>AGENTS.md</code>, skills<br><strong>Loop:</strong> goal → explore/plan in session → edit under permissions<br><a href="#d-plan-requirements-codex"><strong>Deep dive →</strong></a></td><td id="m-plan-requirements-cursor">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Plan Mode, saved plans, Projects (coordinator)<br><strong>Loop:</strong> clarifying Qs → research → editable plan → click build<br><a href="#d-plan-requirements-cursor"><strong>Deep dive →</strong></a></td><td id="m-plan-requirements-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Linear Agent, Notion AI, Cursor Plan Mode<br><strong>Loop:</strong> intake/PRD → refine → implementation plan<br><a href="#d-plan-requirements-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-plan-architecture"><strong>Architecture / tech selection</strong></a></td><td id="m-plan-architecture-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>/plan</code>, strong reasoning models, <code>CLAUDE.md</code><br><strong>Loop:</strong> propose structure/tradeoffs in plan → human picks<br><a href="#d-plan-architecture-claude"><strong>Deep dive →</strong></a></td><td id="m-plan-architecture-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>/plan</code> artifacts, thinking levels (Low–Extra), Orchestrator, rules<br><strong>Loop:</strong> approach in artifact → human accepts<br><a href="#d-plan-architecture-antigravity"><strong>Deep dive →</strong></a></td><td id="m-plan-architecture-copilot">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Plan mode, cloud repo research<br><strong>Loop:</strong> plan/approve before multi-file change<br><a href="#d-plan-architecture-copilot"><strong>Deep dive →</strong></a></td><td id="m-plan-architecture-codex">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> session planning, <code>AGENTS.md</code> constraints<br><strong>Loop:</strong> propose design under markdown guidance<br><a href="#d-plan-architecture-codex"><strong>Deep dive →</strong></a></td><td id="m-plan-architecture-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Plan Mode for multi-file architecture<br><strong>Loop:</strong> Qs + research → plan lists approach/files → build<br><a href="#d-plan-architecture-cursor"><strong>Deep dive →</strong></a></td><td id="m-plan-architecture-best">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> plan agents + Devin code maps<br><strong>Loop:</strong> map systems → options → human decides<br><a href="#d-plan-architecture-best"><strong>Deep dive →</strong></a></td></tr><tr><td rowspan="2"><strong><a href="#deep-dive-design">Design</a></strong></td><td><a href="#d-design-ux"><strong>UX</strong></a></td><td id="m-design-ux-claude">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> Claude in Chrome; optional Figma MCP<br><strong>Loop:</strong> code UI → browser verify vs mock → fix<br><a href="#d-design-ux-claude"><strong>Deep dive →</strong></a></td><td id="m-design-ux-antigravity">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> browser subagent, screenshots, recordings<br><strong>Loop:</strong> playtest flows → evidence → fix code<br><a href="#d-design-ux-antigravity"><strong>Deep dive →</strong></a></td><td id="m-design-ux-copilot">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> none first-party; chat/MCP only<br><strong>Loop:</strong> describe or emit components if prompted<br><a href="#d-design-ux-copilot"><strong>Deep dive →</strong></a></td><td id="m-design-ux-codex">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> none first-party; image/<code>--image</code> input<br><strong>Loop:</strong> screenshot as context → code (no Figma product)<br><a href="#d-design-ux-codex"><strong>Deep dive →</strong></a></td><td id="m-design-ux-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Figma plugin/MCP, Code Connect skills<br><strong>Loop:</strong> Figma link → tokens/frames → code → optional write-back<br><a href="#d-design-ux-cursor"><strong>Deep dive →</strong></a></td><td id="m-design-ux-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Figma AI / Figma Make + MCP<br><strong>Loop:</strong> generate directions → polish → prototype/code handoff<br><a href="#d-design-ux-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-design-api"><strong>API / schema</strong></a></td><td id="m-design-api-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> file edits, OpenAPI/DB migrations, <code>CLAUDE.md</code><br><strong>Loop:</strong> draft schema → typecheck/tests → PR<br><a href="#d-design-api-claude"><strong>Deep dive →</strong></a></td><td id="m-design-api-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> agent file tools, project rules<br><strong>Loop:</strong> draft schema → verify → PR<br><a href="#d-design-api-antigravity"><strong>Deep dive →</strong></a></td><td id="m-design-api-copilot">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> agent in IDE/cloud<br><strong>Loop:</strong> draft schema → tests → PR<br><a href="#d-design-api-copilot"><strong>Deep dive →</strong></a></td><td id="m-design-api-codex">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> CLI/Cloud + <code>AGENTS.md</code><br><strong>Loop:</strong> draft schema → tests → PR<br><a href="#d-design-api-codex"><strong>Deep dive →</strong></a></td><td id="m-design-api-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Agent + rules<br><strong>Loop:</strong> draft schema → tests → PR<br><a href="#d-design-api-cursor"><strong>Deep dive →</strong></a></td><td id="m-design-api-best">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> coding agents + contract tests<br><strong>Loop:</strong> draft → contract validate → human merge<br><a href="#d-design-api-best"><strong>Deep dive →</strong></a></td></tr><tr><td rowspan="3"><strong><a href="#deep-dive-build">Build</a></strong></td><td><a href="#d-build-implement"><strong>Implement</strong></a></td><td id="m-build-implement-claude">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> CLI/IDE/Desktop/Web, subagents, cloud, git/PR<br><strong>Loop:</strong> context → edit/run/verify → commit/PR<br><a href="#d-build-implement-claude"><strong>Deep dive →</strong></a></td><td id="m-build-implement-antigravity">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> App/CLI/IDE/SDK, subagents, worktrees<br><strong>Loop:</strong> tools (+ browser) → artifacts/diffs → iterate<br><a href="#d-build-implement-antigravity"><strong>Deep dive →</strong></a></td><td id="m-build-implement-copilot">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> app/CLI/IDE/cloud; Interactive · Plan · Autopilot modes<br><strong>Loop:</strong> delegate → edit/test in env → PR<br><a href="#d-build-implement-copilot"><strong>Deep dive →</strong></a></td><td id="m-build-implement-codex">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> CLI/App, Cloud envs, worktrees, subagents<br><strong>Loop:</strong> inspect/edit/run → checkpoints → PR<br><a href="#d-build-implement-codex"><strong>Deep dive →</strong></a></td><td id="m-build-implement-cursor">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Agent, Cloud VMs, multi-repo, MCP, checkpoints<br><strong>Loop:</strong> local/cloud tool loop → tests → PR<br><a href="#d-build-implement-cursor"><strong>Deep dive →</strong></a></td><td id="m-build-implement-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Devin + Cursor/Claude/Copilot cloud<br><strong>Loop:</strong> ticket → sandbox impl → PR<br><a href="#d-build-implement-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-build-refactor"><strong>Refactor</strong></a></td><td id="m-build-refactor-claude">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> same agent loop + subagents + tests<br><strong>Loop:</strong> multi-file edits → test → fix → PR<br><a href="#d-build-refactor-claude"><strong>Deep dive →</strong></a></td><td id="m-build-refactor-antigravity">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> parallel subagents, worktrees<br><strong>Loop:</strong> split work → merge results → verify<br><a href="#d-build-refactor-antigravity"><strong>Deep dive →</strong></a></td><td id="m-build-refactor-copilot">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> agent modes, cloud sandbox<br><strong>Loop:</strong> branch refactor → tests → PR<br><a href="#d-build-refactor-copilot"><strong>Deep dive →</strong></a></td><td id="m-build-refactor-codex">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> worktrees, multi-agent tools<br><strong>Loop:</strong> isolated refactor → verify → integrate<br><a href="#d-build-refactor-codex"><strong>Deep dive →</strong></a></td><td id="m-build-refactor-cursor">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> checkpoints, cloud parallel<br><strong>Loop:</strong> checkpoint → refactor → restore if wrong<br><a href="#d-build-refactor-cursor"><strong>Deep dive →</strong></a></td><td id="m-build-refactor-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> coding agents + worktree isolation<br><strong>Loop:</strong> parallel safe refactors → PR<br><a href="#d-build-refactor-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-build-review"><strong>Review</strong></a></td><td id="m-build-review-claude">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> <code>/code-review</code>, GitHub Code Review<br><strong>Loop:</strong> diff → findings → optional <code>--fix</code>/<code>--comment</code><br><a href="#d-build-review-claude"><strong>Deep dive →</strong></a></td><td id="m-build-review-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> unified diffs, plan/verification artifacts<br><strong>Loop:</strong> inspect artifacts before accept<br><a href="#d-build-review-antigravity"><strong>Deep dive →</strong></a></td><td id="m-build-review-copilot">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Copilot code review (auto/on-demand)<br><strong>Loop:</strong> PR → contextual review → suggestions<br><a href="#d-build-review-copilot"><strong>Deep dive →</strong></a></td><td id="m-build-review-codex">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> <code>@codex review</code>, automatic review<br><strong>Loop:</strong> PR trigger → P0/P1-focused comments<br><a href="#d-build-review-codex"><strong>Deep dive →</strong></a></td><td id="m-build-review-cursor">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Agent Review, Bugbot (+ Autofix)<br><strong>Loop:</strong> PR push → comments/fixes → check status<br><a href="#d-build-review-cursor"><strong>Deep dive →</strong></a></td><td id="m-build-review-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Bugbot + Copilot review + CodeRabbit<br><strong>Loop:</strong> multi-bot review → policy gate<br><a href="#d-build-review-best"><strong>Deep dive →</strong></a></td></tr><tr><td rowspan="3"><strong><a href="#deep-dive-test">Test</a></strong></td><td><a href="#d-test-unit"><strong>Unit</strong></a></td><td id="m-test-unit-claude">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> shell + project test runner<br><strong>Loop:</strong> change → test → fix → re-run<br><a href="#d-test-unit-claude"><strong>Deep dive →</strong></a></td><td id="m-test-unit-antigravity">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> shell + test runner<br><strong>Loop:</strong> change → test → fix → re-run<br><a href="#d-test-unit-antigravity"><strong>Deep dive →</strong></a></td><td id="m-test-unit-copilot">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> shell + test runner in sandbox<br><strong>Loop:</strong> change → test → fix → re-run<br><a href="#d-test-unit-copilot"><strong>Deep dive →</strong></a></td><td id="m-test-unit-codex">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> shell + test runner<br><strong>Loop:</strong> change → test → fix → re-run<br><a href="#d-test-unit-codex"><strong>Deep dive →</strong></a></td><td id="m-test-unit-cursor">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> shell + test runner (local/cloud)<br><strong>Loop:</strong> change → test → fix → re-run<br><a href="#d-test-unit-cursor"><strong>Deep dive →</strong></a></td><td id="m-test-unit-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> any coding agent + strong harness<br><strong>Loop:</strong> maintain tests with code changes<br><a href="#d-test-unit-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-test-integration"><strong>Integration</strong></a></td><td id="m-test-integration-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> local/cloud env, GH Action runners<br><strong>Loop:</strong> needs services up → run suite → fix<br><a href="#d-test-integration-claude"><strong>Deep dive →</strong></a></td><td id="m-test-integration-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> local env, <code>agy -p</code> in CI<br><strong>Loop:</strong> env-dependent suite → fix<br><a href="#d-test-integration-antigravity"><strong>Deep dive →</strong></a></td><td id="m-test-integration-copilot">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> cloud/local sandboxes<br><strong>Loop:</strong> run if deps present → fix<br><a href="#d-test-integration-copilot"><strong>Deep dive →</strong></a></td><td id="m-test-integration-codex">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> published Cloud environments<br><strong>Loop:</strong> env with deps → run suite → fix<br><a href="#d-test-integration-codex"><strong>Deep dive →</strong></a></td><td id="m-test-integration-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Cloud env snapshots/builds<br><strong>Loop:</strong> prepared VM → run suite → fix<br><a href="#d-test-integration-cursor"><strong>Deep dive →</strong></a></td><td id="m-test-integration-best">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> cloud agents with full envs<br><strong>Loop:</strong> same; env quality is the gate<br><a href="#d-test-integration-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-test-e2e"><strong>End-to-end</strong></a></td><td id="m-test-e2e-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Claude in Chrome, GIF recording<br><strong>Loop:</strong> drive UI → console/DOM → fix → re-verify<br><a href="#d-test-e2e-claude"><strong>Deep dive →</strong></a></td><td id="m-test-e2e-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> browser subagent, recordings, traces<br><strong>Loop:</strong> <code>/browser</code> playtest → evidence → fix<br><a href="#d-test-e2e-antigravity"><strong>Deep dive →</strong></a></td><td id="m-test-e2e-copilot">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> shell + Playwright/Cypress etc.<br><strong>Loop:</strong> generate/run E2E scripts (no first-party browser agent)<br><a href="#d-test-e2e-copilot"><strong>Deep dive →</strong></a></td><td id="m-test-e2e-codex">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> shell + frameworks; image prompts<br><strong>Loop:</strong> generate/run E2E scripts<br><a href="#d-test-e2e-codex"><strong>Deep dive →</strong></a></td><td id="m-test-e2e-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> cloud desktop/browser control<br><strong>Loop:</strong> computer drives UI → verify → fix<br><a href="#d-test-e2e-cursor"><strong>Deep dive →</strong></a></td><td id="m-test-e2e-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> browser agents + Momentic/Mabl + Playwright<br><strong>Loop:</strong> generate + heal E2E → CI<br><a href="#d-test-e2e-best"><strong>Deep dive →</strong></a></td></tr><tr><td rowspan="3"><strong><a href="#deep-dive-deploy">Deploy</a></strong></td><td><a href="#d-deploy-cicd"><strong>CI/CD</strong></a></td><td id="m-deploy-cicd-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>anthropics/claude-code-action@v1</code>, <code>@claude</code>, hooks<br><strong>Loop:</strong> event/schedule → agent in CI → comment/push<br><a href="#d-deploy-cicd-claude"><strong>Deep dive →</strong></a></td><td id="m-deploy-cicd-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> headless <code>agy -p</code>/<code>--print</code>, permission allowlists<br><strong>Loop:</strong> CI invokes agent → stdout/JSON → job fail/pass<br><a href="#d-deploy-cicd-antigravity"><strong>Deep dive →</strong></a></td><td id="m-deploy-cicd-copilot">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> <code>/pr fix ci</code>, <code>/pr auto</code>, Agent Merge<br><strong>Loop:</strong> fail/conflict → diagnose logs → push → loop green<br><a href="#d-deploy-cicd-copilot"><strong>Deep dive →</strong></a></td><td id="m-deploy-cicd-codex">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>openai/codex-action@v1</code>, <code>codex exec</code><br><strong>Loop:</strong> workflow step → prompt → patch/review out<br><a href="#d-deploy-cicd-codex"><strong>Deep dive →</strong></a></td><td id="m-deploy-cicd-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Automations on CI/workflow events<br><strong>Loop:</strong> CI done → cloud agent fix → push/comment<br><a href="#d-deploy-cicd-cursor"><strong>Deep dive →</strong></a></td><td id="m-deploy-cicd-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Copilot <code>/pr</code> + Agent Merge + Actions<br><strong>Loop:</strong> fail → fix → green (policy still gates)<br><a href="#d-deploy-cicd-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-deploy-release"><strong>Release</strong></a></td><td id="m-deploy-release-claude">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> agent-drafted notes/workflows<br><strong>Loop:</strong> draft changelog/workflow → human runs release<br><a href="#d-deploy-release-claude"><strong>Deep dive →</strong></a></td><td id="m-deploy-release-antigravity">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> agent drafting only<br><strong>Loop:</strong> assistive release text/scripts<br><a href="#d-deploy-release-antigravity"><strong>Deep dive →</strong></a></td><td id="m-deploy-release-copilot">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>/pr agentmerge</code> + GitHub auto-merge<br><strong>Loop:</strong> keep green → enable auto-merge when requirements met<br><a href="#d-deploy-release-copilot"><strong>Deep dive →</strong></a></td><td id="m-deploy-release-codex">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> drafting / Action prompts<br><strong>Loop:</strong> assistive only<br><a href="#d-deploy-release-codex"><strong>Deep dive →</strong></a></td><td id="m-deploy-release-cursor">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> drafting; merge-event automations<br><strong>Loop:</strong> post-merge tasks; no CD train<br><a href="#d-deploy-release-cursor"><strong>Deep dive →</strong></a></td><td id="m-deploy-release-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Agent Merge + Harness (or similar CD)<br><strong>Loop:</strong> merge-ready → progressive delivery<br><a href="#d-deploy-release-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-deploy-infra"><strong>Infra</strong></a></td><td id="m-deploy-infra-claude">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> IaC authoring via agent edits<br><strong>Loop:</strong> write Terraform/K8s → human apply<br><a href="#d-deploy-infra-claude"><strong>Deep dive →</strong></a></td><td id="m-deploy-infra-antigravity">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> IaC authoring<br><strong>Loop:</strong> write → human apply<br><a href="#d-deploy-infra-antigravity"><strong>Deep dive →</strong></a></td><td id="m-deploy-infra-copilot">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> IaC authoring<br><strong>Loop:</strong> write → human apply<br><a href="#d-deploy-infra-copilot"><strong>Deep dive →</strong></a></td><td id="m-deploy-infra-codex">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> IaC authoring<br><strong>Loop:</strong> write → human apply<br><a href="#d-deploy-infra-codex"><strong>Deep dive →</strong></a></td><td id="m-deploy-infra-cursor">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> IaC authoring<br><strong>Loop:</strong> write → human apply<br><a href="#d-deploy-infra-cursor"><strong>Deep dive →</strong></a></td><td id="m-deploy-infra-best">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Spacelift/Harness + agent-written IaC<br><strong>Loop:</strong> agent writes → platform applies w/ policy<br><a href="#d-deploy-infra-best"><strong>Deep dive →</strong></a></td></tr><tr><td rowspan="3"><strong><a href="#deep-dive-maintain">Maintain</a></strong></td><td><a href="#d-maintain-monitor"><strong>Monitor</strong></a></td><td id="m-maintain-monitor-claude">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> no first-party watcher (MCP only if wired)<br><strong>Loop:</strong> external tools required<br><a href="#d-maintain-monitor-claude"><strong>Deep dive →</strong></a></td><td id="m-maintain-monitor-antigravity">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> no first-party watcher<br><strong>Loop:</strong> external tools required<br><a href="#d-maintain-monitor-antigravity"><strong>Deep dive →</strong></a></td><td id="m-maintain-monitor-copilot">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> repo automations ≠ APM<br><strong>Loop:</strong> event→task, not live service health<br><a href="#d-maintain-monitor-copilot"><strong>Deep dive →</strong></a></td><td id="m-maintain-monitor-codex">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> no first-party watcher<br><strong>Loop:</strong> external tools required<br><a href="#d-maintain-monitor-codex"><strong>Deep dive →</strong></a></td><td id="m-maintain-monitor-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Rollouts (Teams/Enterprise)<br><strong>Loop:</strong> PR plan → deploy events → logs/metrics/traces → issue<br><a href="#d-maintain-monitor-cursor"><strong>Deep dive →</strong></a></td><td id="m-maintain-monitor-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Datadog Bits + Cursor Rollouts<br><strong>Loop:</strong> detect → investigate; change↔health<br><a href="#d-maintain-monitor-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-maintain-incident"><strong>Incident response</strong></a></td><td id="m-maintain-incident-claude">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> Slack <code>@Claude</code>/Claude Tag, <code>claude-code-action</code>, scheduled tasks<br><strong>Loop:</strong> feed signal → diagnose → patch PR<br><a href="#d-maintain-incident-claude"><strong>Deep dive →</strong></a></td><td id="m-maintain-incident-antigravity">■□□□□ <strong>1/5</strong><br><strong>Tools:</strong> <code>/automation</code>, <code>/schedule</code>, <code>agy -p</code> (no IR product)<br><strong>Loop:</strong> custom wiring only<br><a href="#d-maintain-incident-antigravity"><strong>Deep dive →</strong></a></td><td id="m-maintain-incident-copilot">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> automations, assign cloud agent, security campaigns<br><strong>Loop:</strong> event/issue → cloud agent PR<br><a href="#d-maintain-incident-copilot"><strong>Deep dive →</strong></a></td><td id="m-maintain-incident-codex">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> Cloud tasks, Action, MCP<br><strong>Loop:</strong> context in → investigate → PR<br><a href="#d-maintain-incident-codex"><strong>Deep dive →</strong></a></td><td id="m-maintain-incident-cursor">■■□□□ <strong>2/5</strong><br><strong>Tools:</strong> Rollouts Fix issue, webhook automations<br><strong>Loop:</strong> regression issue → cloud agent PR (no auto-rollback)<br><a href="#d-maintain-incident-cursor"><strong>Deep dive →</strong></a></td><td id="m-maintain-incident-best">■■■■□ <strong>4/5</strong><br><strong>Tools:</strong> Datadog Bits Remediation, PagerDuty Paige<br><strong>Loop:</strong> alert → investigate → approve remediate → verify<br><a href="#d-maintain-incident-best"><strong>Deep dive →</strong></a></td></tr><tr><td><a href="#d-maintain-debt"><strong>Debt / refactor</strong></a></td><td id="m-maintain-debt-claude">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> cloud scheduled tasks (<code>/schedule</code>/routines, research preview), <code>claude-code-action</code> cron<br><strong>Loop:</strong> schedule/event → audit → PR → human review<br><a href="#d-maintain-debt-claude"><strong>Deep dive →</strong></a></td><td id="m-maintain-debt-antigravity">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> <code>/automation</code> sidecars, <code>/schedule</code>, <code>agy -p</code> headless<br><strong>Loop:</strong> cron/automation → agent → PR<br><a href="#d-maintain-debt-antigravity"><strong>Deep dive →</strong></a></td><td id="m-maintain-debt-copilot">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> automations, Agentic Workflows<br><strong>Loop:</strong> schedule/event → agent → PR<br><a href="#d-maintain-debt-copilot"><strong>Deep dive →</strong></a></td><td id="m-maintain-debt-codex">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> ChatGPT/Codex scheduled tasks, <code>openai/codex-action</code> cron<br><strong>Loop:</strong> schedule → agent → PR<br><a href="#d-maintain-debt-codex"><strong>Deep dive →</strong></a></td><td id="m-maintain-debt-cursor">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Automations; Security Review / Vulnerability Remediation agents<br><strong>Loop:</strong> schedule/PR trigger → sweep → PR<br><a href="#d-maintain-debt-cursor"><strong>Deep dive →</strong></a></td><td id="m-maintain-debt-best">■■■□□ <strong>3/5</strong><br><strong>Tools:</strong> Devin automations + Cursor sweeps<br><strong>Loop:</strong> proactive debt/vuln PRs → human merge<br><a href="#d-maintain-debt-best"><strong>Deep dive →</strong></a></td></tr></tbody>
</table>
</div>

---

## Deep dive
<a id="deep-dive" name="deep-dive"></a>


Expanded evidence for every matrix cell. Use **↑ matrix cell** to return to the exact matrix cell (`#m-…`).

<a id="deep-dive-plan"></a>

### Plan

<a id="d-plan-requirements"></a>

#### Requirements

What “good” looks like at ■■■■■ (5/5): unattended intake from customers/tickets → validated requirements artifact → automatic handoff to design/build **without** a human starting or approving each cycle (still rare in industry).

<h5 id="d-plan-requirements-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-requirements-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/plan` / plan permission mode (`Shift+Tab`, `claude --permission-mode plan`); `CLAUDE.md` + skills; MCP connectors to issue trackers/docs |
| **Mechanic (step-by-step)** | 1) Human starts a session with a goal or ticket context. 2) Enter plan mode so Claude explores the repo and interviews as needed **without editing source**. 3) Claude proposes a plan; human edits (`Ctrl+G`) or accepts. 4) Approving exits plan mode and starts implementation under the chosen permission mode. 5) **Optional methodology** (not a built-in product button): Anthropic’s AI-native SDLC playbook uses committed `intent.md` → `spec.md` → `plan.md` artifacts so humans and agents share the same stage handoff. |
| **Human role** | Owns intake quality, accepts the plan, and remains accountable for product judgment. |
| **Gaps to ■■■■■ (5/5)** | No productized unattended pipeline from raw customer signal → approved requirements. The playbook is methodology guidance, not an autonomous requirements engine shipped as a product surface. |
| **Sources** | [Commands](https://code.claude.com/docs/en/commands), [Permission modes / plan mode](https://code.claude.com/docs/en/permission-modes), [AI-native SDLC playbook](https://claude.com/resources/articles/the-ai-native-sdlc-playbook) |

<h5 id="d-plan-requirements-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-requirements-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/plan` (App/CLI; also `agy --mode=plan`); **Implementation Plan** artifacts; `/agents` Agent Manager for custom agents/subagents; rules (`AGENTS.md`/`GEMINI.md`, `.agents/rules`); MCP |
| **Mechanic** | 1) Human invokes `/plan` with a task (or plan mode). 2) Agent explores without premature writes, may ask clarifying questions. 3) Emits a reviewable Implementation Plan artifact. 4) Human leaves inline comments or clicks **Proceed**. 5) Agent executes against the approved plan. |
| **Human role** | Starts work, steers, and accepts plans before/while execution. |
| **Gaps to ■■■■■ (5/5)** | No documented autonomous org-wide requirements synthesis from tickets/CRM without a human in the loop. |
| **Sources** | [Plan (/plan)](https://antigravity.google/docs/plan/), [Artifacts](https://antigravity.google/docs/artifacts/), [Agents (/agents)](https://antigravity.google/docs/cli/commands/agents/), [Rules](https://antigravity.google/docs/rules/) |

<h5 id="d-plan-requirements-copilot">GitHub Copilot — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-requirements-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Copilot app/CLI session modes: **Interactive**, **Plan**, **Autopilot**; IDE **Plan mode** (VS Code/JetBrains/Xcode/Eclipse); Copilot cloud agent from issues/Agents tab; GitHub issue/PR context |
| **Mechanic** | 1) Start from an issue (app “New session” or assign Copilot on GitHub) or a prompt. 2) Plan mode drafts a plan for review (cloud agent can also be asked to plan before coding). 3) Human approves / steers. 4) Agent implements in local, worktree, or cloud sandbox. 5) Opens or updates a PR. |
| **Human role** | Approves plans; Copilot Workspace TP ended 2025-05-30 — **not scored**. |
| **Gaps to ■■■■■ (5/5)** | HITL plan gate remains; no autonomous PRD system; Workspace specification richness is gone. |
| **Sources** | [About agents](https://docs.github.com/en/copilot/concepts/agent-capabilities/about-agents/about-github-copilot-agents), [App sessions](https://docs.github.com/en/copilot/how-tos/github-copilot-app/agent-sessions), [IDE Plan mode](https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode), [Kick off a task](https://docs.github.com/en/copilot/how-tos/copilot-on-github/use-copilot-agents/kick-off-a-task), [Workspace sunset](https://githubnext.com/projects/copilot-workspace/) |

<h5 id="d-plan-requirements-codex">Codex — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-requirements-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Codex CLI / App / Cloud; `AGENTS.md`; skills; MCP |
| **Mechanic** | 1) Human describes the goal in a repo or Cloud task. 2) Codex explores and plans in-session. 3) Edits/runs under chosen permissions. 4) Human steers follow-ups. |
| **Human role** | Defines scope; no first-party “plan artifact → click build” product comparable to Cursor Plan Mode. |
| **Gaps to ■■■■■ (5/5)** | Planning is conversational/session-based, not an autonomous requirements product. |
| **Sources** | [CLI](https://learn.chatgpt.com/docs/codex/cli), [AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md.md) |

<h5 id="d-plan-requirements-cursor">Cursor — ■■■■□ <strong>4/5</strong> · <a href="#m-plan-requirements-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Plan Mode**; plans saved as markdown (home or workspace); Agent build handoff; **Projects** (coordinator delegates to worker Cloud Agents) for larger bodies of work |
| **Mechanic** | 1) Enter Plan Mode (Shift+Tab / mode picker; also suggested for complex prompts). 2) Agent asks clarifying questions. 3) Researches the codebase. 4) Writes an editable plan. 5) Human edits the plan. 6) Click build → Agent implements. |
| **Human role** | Answers questions, edits the plan, clicks build — but does not have to invent the implementation breakdown. |
| **Gaps to ■■■■■ (5/5)** | Still requires human Q&A and explicit build; does not own product discovery or stakeholder sign-off unattended. |
| **Sources** | [Plan Mode](https://cursor.com/docs/agent/plan-mode), [Projects](https://cursor.com/docs/agent/projects), [Agent](https://cursor.com/docs/agent/overview) |

<h5 id="d-plan-requirements-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-plan-requirements-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **[Linear Agent](https://linear.app/docs/linear-agent)** / **Notion AI** for intake & PRD drafts; **[Cursor Plan Mode](https://cursor.com/docs/agent/plan-mode)** for implementation planning |
| **Mechanic** | Capture/synthesize requests in Linear/Notion → engineer refines acceptance criteria → Cursor Plan Mode turns that into a codebase-aware build plan. |
| **Gaps to ■■■■■ (5/5)** | Product judgment, compliance, and stakeholder approval remain human across the industry. |

<a id="d-plan-architecture"></a>

#### Architecture / tech selection

<h5 id="d-plan-architecture-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-architecture-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Plan mode; high-reasoning models; architecture notes in `CLAUDE.md` / skills |
| **Mechanic** | In plan mode, Claude proposes modules, libraries, and tradeoffs grounded in the repo → human selects → implement. |
| **Gaps to ■■■■■ (5/5)** | No enforceable org tech-radar, cost model, or risk simulation as a built-in product loop. |
| **Sources** | [How Claude Code works](https://code.claude.com/docs/en/how-claude-code-works), [SDLC playbook](https://claude.com/resources/articles/the-ai-native-sdlc-playbook) |

<h5 id="d-plan-architecture-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-architecture-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/plan` Implementation Plan artifacts; model **thinking levels** (Low/Medium/High/Extra on supported Gemini models); optional **Orchestrator** (planner + executor models); rules |
| **Mechanic** | Agent embeds approach/tradeoffs in the plan artifact → human accepts or revises → Proceed to execute. |
| **Gaps to ■■■■■ (5/5)** | Advisory only — not policy-bound autonomous selection. |
| **Sources** | [Plan](https://antigravity.google/docs/plan/), [Models / thinking levels](https://antigravity.google/docs/models/), [Rules](https://antigravity.google/docs/rules/) |

<h5 id="d-plan-architecture-copilot">GitHub Copilot — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-architecture-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Plan mode; cloud research over the repository |
| **Mechanic** | Plan/approve before large multi-file architectural changes. |
| **Gaps to ■■■■■ (5/5)** | No org-wide architecture governor product. |
| **Sources** | [About agents](https://docs.github.com/en/copilot/concepts/agent-capabilities/about-agents/about-github-copilot-agents) |

<h5 id="d-plan-architecture-codex">Codex — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-architecture-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Session planning; `AGENTS.md` as soft constraints |
| **Mechanic** | Propose design under project markdown guidance → human steers. |
| **Gaps to ■■■■■ (5/5)** | Constraints are documents, not an automated decision system. |
| **Sources** | [AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md.md) |

<h5 id="d-plan-architecture-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-architecture-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Plan Mode for multi-file / architectural tasks |
| **Mechanic** | Clarifying questions + research → plan lists approach and files → human edits → build. |
| **Gaps to ■■■■■ (5/5)** | Strong assist; not enforceable autonomous tech selection. |
| **Sources** | [Plan Mode](https://cursor.com/docs/agent/plan-mode) |

<h5 id="d-plan-architecture-best">Best — ■■■□□ <strong>3/5</strong> · <a href="#m-plan-architecture-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Cursor/Claude plan agents; **Devin** codebase mapping |
| **Mechanic** | Map systems → propose options → human decides irreversible bets. |
| **Gaps to ■■■■■ (5/5)** | Industry still HITL for architecture that locks cost and risk. |
| **Sources** | [Devin](https://devin.ai/) |

<a id="deep-dive-design"></a>

### Design

<a id="d-design-ux"></a>

#### UX

<h5 id="d-design-ux-claude">Claude Code — ■■□□□ <strong>2/5</strong> · <a href="#m-design-ux-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Claude in Chrome** (browser extension integration); optional Figma/design MCP |
| **Mechanic** | 1) Implement UI in code. 2) Launch with Chrome connected (`claude --chrome` or enabled default). 3) Agent opens the app, reads console/DOM, compares to a mock if provided. 4) Fixes code and re-checks. Login/CAPTCHA can pause for a human. |
| **What this is good for** | Design *verification* and UI bugfix loops. |
| **Gaps to ■■■■■ (5/5)** | Not a design authoring studio; brand systems live elsewhere (Figma). |
| **Sources** | [Chrome](https://code.claude.com/docs/en/chrome) |

<h5 id="d-design-ux-antigravity">Antigravity — ■■□□□ <strong>2/5</strong> · <a href="#m-design-ux-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Browser subagent; screenshots; session recordings; (CLI) traces/Lighthouse paths |
| **Mechanic** | Ask in plain language or `/browser` → subagent playtests → captures evidence → agent fixes code. |
| **Gaps to ■■■■■ (5/5)** | Verification ≠ creation; no first-party design-system authoring product. |
| **Sources** | [Browser use](https://antigravity.google/docs/browser/) |

<h5 id="d-design-ux-copilot">GitHub Copilot — ■□□□□ <strong>1/5</strong> · <a href="#m-design-ux-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | No first-party design surface; generic chat / optional MCP |
| **Mechanic** | Can describe UI or emit components when prompted — no native design loop. |
| **Gaps to ■■■■■ (5/5)** | Missing design product entirely. |
| **Sources** | Copilot docs emphasize coding/PR/cloud agents, not UX authoring ([AI tools by phase](https://docs.github.com/en/copilot/concepts/agent-capabilities/choosing-and-delegating-agent-work/ai-tools)). |

<h5 id="d-design-ux-codex">Codex — ■□□□□ <strong>1/5</strong> · <a href="#m-design-ux-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Optional image input (`codex --image`); MCP possible; no Figma-native product |
| **Mechanic** | Screenshot/diagram as prompt context → code. |
| **Gaps to ■■■■■ (5/5)** | No design authoring surface. |
| **Sources** | [CLI](https://learn.chatgpt.com/docs/codex/cli) |

<h5 id="d-design-ux-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-design-ux-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Figma plugin / remote MCP**; designer skills (Code Connect, generate library, etc.) |
| **Mechanic** | Connect Figma → paste frame link → agent reads components/variables/layout → generates code aligned to design system → can write native Figma content back. |
| **Gaps to ■■■■■ (5/5)** | Still depends on Figma + human design judgment; Cursor is the bridge, not a full design OS. |
| **Sources** | [Cursor for designers](https://cursor.com/for/designers), [Figma MCP setup](https://help.figma.com/hc/en-us/articles/39889260656407-Cursor-and-Figma-Set-up-the-MCP-server) |

<h5 id="d-design-ux-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-design-ux-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Figma AI / Figma Make**; MCP into coding agents |
| **Mechanic** | Generate/explore directions in Figma → polish → code-backed prototype or hand off to an IDE agent via MCP. |
| **Gaps to ■■■■■ (5/5)** | Brand, accessibility, and product taste remain human. |
| **Sources** | [Figma AI](https://www.figma.com/ai/) |

<a id="d-design-api"></a>

#### API / schema


<h5 id="d-design-api-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-design-api-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agent file edits; OpenAPI/GraphQL/SQL migrations; `CLAUDE.md` / skills |
| **Mechanic** | Prompt for API/DB shape → draft schemas/handlers/migrations → typecheck/tests → human reviews PR. |
| **Gaps to ■■■■■ (5/5)** | No built-in multi-service contract governance or unattended API platform ownership. |
| **Sources** | [How Claude Code works](https://code.claude.com/docs/en/how-claude-code-works) |


<h5 id="d-design-api-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-design-api-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agent file tools; project rules (`AGENTS.md` / `GEMINI.md`) |
| **Mechanic** | Prompt for API/DB shape → draft schemas/handlers/migrations → verify → human reviews PR. |
| **Gaps to ■■■■■ (5/5)** | No built-in multi-service contract governance or unattended API platform ownership. |
| **Sources** | [Rules](https://antigravity.google/docs/rules/), [Features](https://antigravity.google/docs/features/) |


<h5 id="d-design-api-copilot">GitHub Copilot — ■■■□□ <strong>3/5</strong> · <a href="#m-design-api-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | IDE/cloud coding agents; repo conventions |
| **Mechanic** | Prompt for API/DB shape → draft schemas/handlers/migrations → tests → PR. |
| **Gaps to ■■■■■ (5/5)** | No built-in multi-service contract governance or unattended API platform ownership. |
| **Sources** | [About agents](https://docs.github.com/en/copilot/concepts/agent-capabilities/about-agents/about-github-copilot-agents) |


<h5 id="d-design-api-codex">Codex — ■■■□□ <strong>3/5</strong> · <a href="#m-design-api-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | CLI/Cloud agents; [`AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md.md) |
| **Mechanic** | Prompt for API/DB shape → draft schemas/handlers/migrations → tests → PR. |
| **Gaps to ■■■■■ (5/5)** | No built-in multi-service contract governance or unattended API platform ownership. |
| **Sources** | [CLI](https://learn.chatgpt.com/docs/codex/cli) |


<h5 id="d-design-api-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-design-api-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agent + project rules / skills |
| **Mechanic** | Prompt for API/DB shape → draft schemas/handlers/migrations → tests → PR. |
| **Gaps to ■■■■■ (5/5)** | No built-in multi-service contract governance or unattended API platform ownership. |
| **Sources** | [Agent](https://cursor.com/docs/agent/overview) |


<h5 id="d-design-api-best">Best-in-class — ■■■□□ <strong>3/5</strong> · <a href="#m-design-api-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Coding agents + OpenAPI-aware contract tests (schemathesis / pact-style suites) |
| **Mechanic** | Draft → contract validate in CI → human merge for breaking changes. |
| **Gaps to ■■■■■ (5/5)** | Industry still HITL for breaking multi-service API changes. |
|

<a id="deep-dive-build"></a>

### Build

<a id="d-build-implement"></a>

#### Implement

<h5 id="d-build-implement-claude">Claude Code — ■■■■□ <strong>4/5</strong> · <a href="#m-build-implement-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Terminal, VS Code/JetBrains, Desktop, Web; file/search/shell/web tools; subagents; cloud sessions; git commit/PR |
| **Mechanic** | Goal → gather context → edit → run commands/tests → verify → commit/PR. Human can interrupt anytime. Surfaces share `CLAUDE.md` / MCP. |
| **Gaps to ■■■■■ (5/5)** | Human/policy review still expected; not documented as unattended always-correct shipping. |
| **Sources** | [Overview](https://code.claude.com/docs/en/overview/), [How it works](https://code.claude.com/docs/en/how-claude-code-works) |

<h5 id="d-build-implement-antigravity">Antigravity — ■■■■□ <strong>4/5</strong> · <a href="#m-build-implement-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | App, CLI `agy`, IDE extensions, Python SDK; async subagents; Git worktrees; artifacts |
| **Mechanic** | Task → tool use (optionally browser) → diffs/artifacts for review → iterate; parallel agents for background work. |
| **Gaps to ■■■■■ (5/5)** | HITL merge expectation remains. |
| **Sources** | [Product](https://antigravity.google/), [Features](https://antigravity.google/docs/features/) |

<h5 id="d-build-implement-copilot">GitHub Copilot — ■■■■□ <strong>4/5</strong> · <a href="#m-build-implement-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Copilot app, CLI, IDE agent mode, cloud agent; Interactive / Plan / Autopilot autonomy levels |
| **Mechanic** | Delegate → agent edits and runs tests in local or cloud env → PR → human review. Autopilot reduces mid-flight prompts but not accountability. |
| **Gaps to ■■■■■ (5/5)** | Repo policies and human responsibility still apply. |
| **Sources** | [About agents](https://docs.github.com/en/copilot/concepts/agent-capabilities/about-agents/about-github-copilot-agents), [Copilot on GitHub](https://docs.github.com/en/copilot/concepts/copilot-surfaces/copilot-on-github) |

<h5 id="d-build-implement-codex">Codex — ■■■■□ <strong>4/5</strong> · <a href="#m-build-implement-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Codex CLI/App; Cloud environments; permissions; subagents; worktrees |
| **Mechanic** | Local `codex` or Cloud task → inspect/edit/run → Git checkpoints → PR/review. |
| **Gaps to ■■■■■ (5/5)** | Permissions and acceptance remain human-controlled. |
| **Sources** | [CLI](https://learn.chatgpt.com/docs/codex/cli), [Cloud environments](https://learn.chatgpt.com/docs/environments/cloud-environments) |

<h5 id="d-build-implement-cursor">Cursor — ■■■■□ <strong>4/5</strong> · <a href="#m-build-implement-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agent; Cloud Agents on VMs; multi-repo; MCP; checkpoints; Projects |
| **Mechanic** | Local or cloud tool loop with tests in a real env → PR; parallel agents for larger work. |
| **Gaps to ■■■■■ (5/5)** | Environment setup quality gates autonomy; merge still human. |
| **Sources** | [Agent](https://cursor.com/docs/agent/overview), [Cloud Agents](https://cursor.com/docs/cloud-agent) |

<h5 id="d-build-implement-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-build-implement-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Devin**; Cursor Cloud Agents; Claude Code; Copilot cloud |
| **Mechanic** | Assign ticket → sandbox implementation → PR. |
| **Gaps to ■■■■■ (5/5)** | Review/merge gates remain industry-standard. |
| **Sources** | [Devin](https://devin.ai/) |

<a id="d-build-refactor"></a>

#### Refactor


<h5 id="d-build-refactor-claude">Claude Code — ■■■■□ <strong>4/5</strong> · <a href="#m-build-refactor-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Same implement agent loop; multi-file edits; tests as verify |
| **Mechanic** | Scope refactor → multi-file edits → run tests → fix → PR. **Extra:** Strong single-agent (or cloud) multi-file refactor + test loop. |
| **Gaps to ■■■■■ (5/5)** | Large behavioral refactors still need human architecture sign-off; no product claims unattended org-wide rewrites. |


<h5 id="d-build-refactor-antigravity">Antigravity — ■■■■□ <strong>4/5</strong> · <a href="#m-build-refactor-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Same implement agent loop; multi-file edits; tests as verify |
| **Mechanic** | Scope refactor → multi-file edits → run tests → fix → PR. **Extra:** Parallel subagents + worktree isolation for split refactors. |
| **Gaps to ■■■■■ (5/5)** | Large behavioral refactors still need human architecture sign-off; no product claims unattended org-wide rewrites. |


<h5 id="d-build-refactor-copilot">GitHub Copilot — ■■■■□ <strong>4/5</strong> · <a href="#m-build-refactor-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Same implement agent loop; multi-file edits; tests as verify |
| **Mechanic** | Scope refactor → multi-file edits → run tests → fix → PR. **Extra:** Strong single-agent (or cloud) multi-file refactor + test loop. |
| **Gaps to ■■■■■ (5/5)** | Large behavioral refactors still need human architecture sign-off; no product claims unattended org-wide rewrites. |


<h5 id="d-build-refactor-codex">Codex — ■■■■□ <strong>4/5</strong> · <a href="#m-build-refactor-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Same implement agent loop; multi-file edits; tests as verify |
| **Mechanic** | Scope refactor → multi-file edits → run tests → fix → PR. **Extra:** Explicit worktrees / multi-agent tools for isolated refactors. |
| **Gaps to ■■■■■ (5/5)** | Large behavioral refactors still need human architecture sign-off; no product claims unattended org-wide rewrites. |


<h5 id="d-build-refactor-cursor">Cursor — ■■■■□ <strong>4/5</strong> · <a href="#m-build-refactor-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Same implement agent loop; multi-file edits; tests as verify |
| **Mechanic** | Scope refactor → multi-file edits → run tests → fix → PR. **Extra:** Checkpoints before risky edits; restore if wrong. |
| **Gaps to ■■■■■ (5/5)** | Large behavioral refactors still need human architecture sign-off; no product claims unattended org-wide rewrites. |


<h5 id="d-build-refactor-best">Best-in-class — ■■■■□ <strong>4/5</strong> · <a href="#m-build-refactor-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Same implement agent loop; multi-file edits; tests as verify |
| **Mechanic** | Scope refactor → multi-file edits → run tests → fix → PR. **Extra:** Coding agents + worktree isolation for parallel safe refactors → PR. |
| **Gaps to ■■■■■ (5/5)** | Large behavioral refactors still need human architecture sign-off; no product claims unattended org-wide rewrites. |


<a id="d-build-review"></a>

#### Review

<h5 id="d-build-review-claude">Claude Code — ■■■■□ <strong>4/5</strong> · <a href="#m-build-review-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/code-review` (local; `--fix`, `--comment`); managed **GitHub Code Review** |
| **Mechanic** | Trigger on branch/PR → review subagent reads diff/context → findings in session or PR comments → optional apply. |
| **Gaps to ■■■■■ (5/5)** | Advisory; does not replace required human approvals. |
| **Sources** | [Local review](https://code.claude.com/docs/en/code-review-local), [Code Review](https://code.claude.com/docs/en/code-review) |

<h5 id="d-build-review-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-build-review-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Unified multi-file diffs; implementation plans; verification reports/recordings |
| **Mechanic** | Human (or agent-assisted) inspects artifacts before accepting work — strong verification UX, weaker dedicated PR-bot. |
| **Gaps to ■■■■■ (5/5)** | No documented automated PR review service on par with Bugbot/Copilot/Codex review. |
| **Sources** | [Features](https://antigravity.google/docs/features/) |

<h5 id="d-build-review-copilot">GitHub Copilot — ■■■■□ <strong>4/5</strong> · <a href="#m-build-review-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Copilot code review** (request or automatic) |
| **Mechanic** | PR → agentic context gather → review comments/suggestions → human applies. |
| **Gaps to ■■■■■ (5/5)** | Review ≠ merge authority. |
| **Sources** | [Copilot on GitHub](https://docs.github.com/en/copilot/concepts/copilot-surfaces/copilot-on-github) |

<h5 id="d-build-review-codex">Codex — ■■■■□ <strong>4/5</strong> · <a href="#m-build-review-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `@codex review`; Automatic review settings |
| **Mechanic** | Comment or auto trigger → Codex posts focused (P0/P1) review. |
| **Gaps to ■■■■■ (5/5)** | Advisory. |
| **Sources** | [GitHub review](https://learn.chatgpt.com/docs/third-party/github) |

<h5 id="d-build-review-cursor">Cursor — ■■■■□ <strong>4/5</strong> · <a href="#m-build-review-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local Agent Review; **Bugbot** on PRs; optional Autofix |
| **Mechanic** | PR push → Bugbot analyzes → comments / fix PRs → publishes check status → human merge under branch protection. |
| **Gaps to ■■■■■ (5/5)** | Findings assist; policies still gate merge. |
| **Sources** | [Bugbot](https://cursor.com/docs/bugbot), [Reviewing & testing](https://cursor.com/learn/reviewing-testing) |

<h5 id="d-build-review-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-build-review-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Bugbot + Copilot code review + CodeRabbit (multi-bot) |
| **Gaps to ■■■■■ (5/5)** | No credible “bots alone merge everything” default in serious orgs. |

<a id="deep-dive-test"></a>

### Test

<a id="d-test-unit"></a>

#### Unit


<h5 id="d-test-unit-claude">Claude Code — ■■■■□ <strong>4/5</strong> · <a href="#m-test-unit-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Product shell/tool runner + the repo’s unit test framework |
| **Mechanic** | Edit code → run unit tests → parse failures → fix → re-run until green or escalate to human. |
| **Gaps to ■■■■■ (5/5)** | Does not invent complete correct suites for arbitrary legacy systems with proven coverage guarantees unattended. |


<h5 id="d-test-unit-antigravity">Antigravity — ■■■■□ <strong>4/5</strong> · <a href="#m-test-unit-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Product shell/tool runner + the repo’s unit test framework |
| **Mechanic** | Edit code → run unit tests → parse failures → fix → re-run until green or escalate to human. |
| **Gaps to ■■■■■ (5/5)** | Does not invent complete correct suites for arbitrary legacy systems with proven coverage guarantees unattended. |


<h5 id="d-test-unit-copilot">GitHub Copilot — ■■■■□ <strong>4/5</strong> · <a href="#m-test-unit-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Product shell/tool runner + the repo’s unit test framework |
| **Mechanic** | Edit code → run unit tests → parse failures → fix → re-run until green or escalate to human. |
| **Gaps to ■■■■■ (5/5)** | Does not invent complete correct suites for arbitrary legacy systems with proven coverage guarantees unattended. |


<h5 id="d-test-unit-codex">Codex — ■■■■□ <strong>4/5</strong> · <a href="#m-test-unit-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Product shell/tool runner + the repo’s unit test framework |
| **Mechanic** | Edit code → run unit tests → parse failures → fix → re-run until green or escalate to human. |
| **Gaps to ■■■■■ (5/5)** | Does not invent complete correct suites for arbitrary legacy systems with proven coverage guarantees unattended. |


<h5 id="d-test-unit-cursor">Cursor — ■■■■□ <strong>4/5</strong> · <a href="#m-test-unit-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Product shell/tool runner + the repo’s unit test framework |
| **Mechanic** | Edit code → run unit tests → parse failures → fix → re-run until green or escalate to human. |
| **Gaps to ■■■■■ (5/5)** | Does not invent complete correct suites for arbitrary legacy systems with proven coverage guarantees unattended. |


<h5 id="d-test-unit-best">Best-in-class — ■■■■□ <strong>4/5</strong> · <a href="#m-test-unit-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Product shell/tool runner + the repo’s unit test framework |
| **Mechanic** | Edit code → run unit tests → parse failures → fix → re-run until green or escalate to human. |
| **Gaps to ■■■■■ (5/5)** | Does not invent complete correct suites for arbitrary legacy systems with proven coverage guarantees unattended. |


<a id="d-test-integration"></a>

#### Integration


<h5 id="d-test-integration-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-test-integration-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local services; CI runners; cloud/agent environments |
| **Mechanic** | Local/cloud env and GH Action runners when services are available. If DBs/APIs/deps are present, agent runs integration suites and fixes failures. |
| **Gaps to ■■■■■ (5/5)** | Env quality stays on the team; none is a turnkey multi-service integration platform. |


<h5 id="d-test-integration-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-test-integration-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local services; CI runners; cloud/agent environments |
| **Mechanic** | Local env or `agy -p` in CI when services are available. If DBs/APIs/deps are present, agent runs integration suites and fixes failures. |
| **Gaps to ■■■■■ (5/5)** | Env quality stays on the team; none is a turnkey multi-service integration platform. |


<h5 id="d-test-integration-copilot">GitHub Copilot — ■■■□□ <strong>3/5</strong> · <a href="#m-test-integration-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local services; CI runners; cloud/agent environments |
| **Mechanic** | Cloud/local sandboxes if deps are present. If DBs/APIs/deps are present, agent runs integration suites and fixes failures. |
| **Gaps to ■■■■■ (5/5)** | Env quality stays on the team; none is a turnkey multi-service integration platform. |


<h5 id="d-test-integration-codex">Codex — ■■■□□ <strong>3/5</strong> · <a href="#m-test-integration-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local services; CI runners; cloud/agent environments |
| **Mechanic** | Published Cloud environments with deps installed. If DBs/APIs/deps are present, agent runs integration suites and fixes failures. |
| **Gaps to ■■■■■ (5/5)** | Env quality stays on the team; none is a turnkey multi-service integration platform. |


<h5 id="d-test-integration-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-test-integration-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local services; CI runners; cloud/agent environments |
| **Mechanic** | Cloud env snapshots/builds on a prepared VM. If DBs/APIs/deps are present, agent runs integration suites and fixes failures. |
| **Gaps to ■■■■■ (5/5)** | Env quality stays on the team; none is a turnkey multi-service integration platform. |


<h5 id="d-test-integration-best">Best-in-class — ■■■□□ <strong>3/5</strong> · <a href="#m-test-integration-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Local services; CI runners; cloud/agent environments |
| **Mechanic** | Cloud agents with full envs — env quality is still the gate. If DBs/APIs/deps are present, agent runs integration suites and fixes failures. |
| **Gaps to ■■■■■ (5/5)** | Env quality stays on the team; none is a turnkey multi-service integration platform. |


<a id="d-test-e2e"></a>

#### End-to-end

<h5 id="d-test-e2e-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-test-e2e-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Claude in Chrome; GIF session recording |
| **Mechanic** | Start app → browser tools navigate/click → read console/DOM → fix → re-verify. Human handles login/CAPTCHA pauses. |
| **Gaps to ■■■■■ (5/5)** | Not a full unattended CI E2E product for every app class. |
| **Sources** | [Chrome](https://code.claude.com/docs/en/chrome) |

<h5 id="d-test-e2e-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-test-e2e-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Browser subagent; recordings; screenshots; DevTools-oriented traces |
| **Mechanic** | `/browser` or built-in browser → playtest → evidence artifacts → fix. Some CI/headless limits documented. |
| **Gaps to ■■■■■ (5/5)** | Fleet-wide unattended E2E ownership not documented. |
| **Sources** | [Browser](https://antigravity.google/docs/browser/), [Codelab limits](https://codelabs.developers.google.com/agentic-ui-automation-with-antigravity) |

<h5 id="d-test-e2e-copilot">GitHub Copilot — ■■□□□ <strong>2/5</strong> · <a href="#m-test-e2e-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Shell + E2E frameworks (Playwright, etc.) |
| **Mechanic** | Generate/run scripts if the project has them — no first-party browser-actuation product comparable to Claude/Antigravity/Cursor. |
| **Gaps to ■■■■■ (5/5)** | Missing native browser agent loop. |

<h5 id="d-test-e2e-codex">Codex — ■■□□□ <strong>2/5</strong> · <a href="#m-test-e2e-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Shell + frameworks; optional images in prompt |
| **Mechanic** | Same script-centric pattern as Copilot. |
| **Gaps to ■■■■■ (5/5)** | Same missing first-party browser agent. |
| **Sources** | [CLI](https://learn.chatgpt.com/docs/codex/cli) |

<h5 id="d-test-e2e-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-test-e2e-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Cloud agent desktop/browser control; local test commands |
| **Mechanic** | Cloud computer drives UI against the changed app → verify → fix. |
| **Gaps to ■■■■■ (5/5)** | Requires computer/env setup; not a specialized always-on E2E SaaS. |
| **Sources** | [Cloud Agents](https://cursor.com/docs/cloud-agent) |

<h5 id="d-test-e2e-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-test-e2e-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Browser-capable coding agents + Momentic/Mabl + Playwright |
| **Mechanic** | Generate and heal E2E → run in CI. |
| **Gaps to ■■■■■ (5/5)** | Auth, data setup, and flake management still block true 5. |

<a id="deep-dive-deploy"></a>

### Deploy

<a id="d-deploy-cicd"></a>

#### CI/CD

<h5 id="d-deploy-cicd-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-deploy-cicd-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `anthropics/claude-code-action`; `@claude` interactive mode; `prompt` automation mode; hooks |
| **Mechanic** | GitHub/GitLab event or schedule → Action runs Claude in the repo → analyze/implement/comment/push under permissions and hooks. |
| **Gaps to ■■■■■ (5/5)** | Not a keep-PR-green / merge autopilot like Copilot Agent Merge. |
| **Sources** | [GitHub Actions](https://code.claude.com/docs/en/github-actions), [Hooks](https://code.claude.com/docs/en/hooks-guide) |

<h5 id="d-deploy-cicd-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-deploy-cicd-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `agy -p` headless; `permissions.allow`; JSON output; timeouts |
| **Mechanic** | CI job invokes headless agent → capture stdout/JSON → fail the job on non-SUCCESS. You wire the workflow. |
| **Gaps to ■■■■■ (5/5)** | No native GitHub “watch and fix until green” product. |
| **Sources** | [Headless mode](https://antigravity.google/docs/cli/headless/) |

<h5 id="d-deploy-cicd-copilot">GitHub Copilot — ■■■■□ <strong>4/5</strong> · <a href="#m-deploy-cicd-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/pr fix ci`, `/pr auto`, `/pr fix conflicts|feedback`, **Agent Merge** (“Watch and fix”) |
| **Mechanic** | CI failure or conflict → Copilot reads logs → targeted fixes → push → re-check; Agent Merge watches and restarts when blockers appear. Docs state it does **not** replace human review. |
| **Gaps to ■■■■■ (5/5)** | Required reviews / branch protections still apply → cannot be 5 under documented behavior. |
| **Sources** | [`/pr` command](https://docs.github.com/en/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests), [Agent Merge](https://docs.github.com/en/copilot/how-tos/copilot-on-github/use-copilot-agents/watch-and-fix-pull-requests) |

<h5 id="d-deploy-cicd-codex">Codex — ■■■□□ <strong>3/5</strong> · <a href="#m-deploy-cicd-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `openai/codex-action@v1`; `codex exec` |
| **Mechanic** | Workflow step installs/runs Codex with prompt or prompt-file → patches/reviews as directed → later steps consume output. |
| **Gaps to ■■■■■ (5/5)** | Building block, not a full green-PR autopilot. |
| **Sources** | [GitHub Action](https://learn.chatgpt.com/docs/github-action) |

<h5 id="d-deploy-cicd-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-deploy-cicd-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Automations with CI completed / workflow completed triggers; Cloud Agents |
| **Mechanic** | CI event fires automation → cloud agent diagnoses/fixes → push or PR comment. |
| **Gaps to ■■■■■ (5/5)** | Triggers agents; does not own Actions/CD as a platform. |
| **Sources** | [Automations](https://cursor.com/docs/cloud-agent/automations) |

<h5 id="d-deploy-cicd-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-deploy-cicd-best"><strong>↑ matrix cell</strong></a></h5>


Copilot `/pr` + Agent Merge + GitHub Actions. Policy gates remain.

<a id="d-deploy-release"></a>

#### Release


<h5 id="d-deploy-release-claude">Claude Code — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-release-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agent-drafted release notes/workflows |
| **Mechanic** | Draft changelog/workflow → human runs the release train |
| **Gaps to ■■■■■ (5/5)** | No progressive delivery control plane |


<h5 id="d-deploy-release-antigravity">Antigravity — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-release-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agent drafting only |
| **Mechanic** | Assistive release text/scripts → human runs release |
| **Gaps to ■■■■■ (5/5)** | No progressive delivery control plane |


<h5 id="d-deploy-release-copilot">GitHub Copilot — ■■■□□ <strong>3/5</strong> · <a href="#m-deploy-release-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/pr agentmerge` + GitHub auto-merge; Agent Merge |
| **Mechanic** | Keep PR green → enable auto-merge when requirements met |
| **Gaps to ■■■■■ (5/5)** | Still waits on approvals/merge queue; not full prod orchestration |
| **Sources** | [`/pr` docs](https://docs.github.com/en/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests) |


<h5 id="d-deploy-release-codex">Codex — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-release-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Drafting / Action prompts |
| **Mechanic** | Assistive only |
| **Gaps to ■■■■■ (5/5)** | No progressive delivery control plane |


<h5 id="d-deploy-release-cursor">Cursor — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-release-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Drafting; merge-event automations |
| **Mechanic** | Post-merge tasks possible; no CD train |
| **Gaps to ■■■■■ (5/5)** | No progressive delivery control plane |


<h5 id="d-deploy-release-best">Best-in-class — ■■■■□ <strong>4/5</strong> · <a href="#m-deploy-release-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Copilot Agent Merge + **Harness** (or similar CD) |
| **Mechanic** | Merge-ready PR → progressive delivery |
| **Gaps to ■■■■■ (5/5)** | Regulated prod still gated |


<a id="d-deploy-infra"></a>

#### Infra


<h5 id="d-deploy-infra-claude">Claude Code — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-infra-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agents author Terraform/Kubernetes/Actions IaC |
| **Mechanic** | Prompt → generate modules/manifests → **human** (or separate IaC platform) plans/applies |
| **Gaps to ■■■■■ (5/5)** | None of the five is a cloud control plane (apply/drift/heal). |


<h5 id="d-deploy-infra-antigravity">Antigravity — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-infra-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agents author Terraform/Kubernetes/Actions IaC |
| **Mechanic** | Prompt → generate modules/manifests → **human** (or separate IaC platform) plans/applies |
| **Gaps to ■■■■■ (5/5)** | None of the five is a cloud control plane (apply/drift/heal). |


<h5 id="d-deploy-infra-copilot">GitHub Copilot — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-infra-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agents author Terraform/Kubernetes/Actions IaC |
| **Mechanic** | Prompt → generate modules/manifests → **human** (or separate IaC platform) plans/applies |
| **Gaps to ■■■■■ (5/5)** | None of the five is a cloud control plane (apply/drift/heal). |


<h5 id="d-deploy-infra-codex">Codex — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-infra-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agents author Terraform/Kubernetes/Actions IaC |
| **Mechanic** | Prompt → generate modules/manifests → **human** (or separate IaC platform) plans/applies |
| **Gaps to ■■■■■ (5/5)** | None of the five is a cloud control plane (apply/drift/heal). |


<h5 id="d-deploy-infra-cursor">Cursor — ■■□□□ <strong>2/5</strong> · <a href="#m-deploy-infra-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Agents author Terraform/Kubernetes/Actions IaC |
| **Mechanic** | Prompt → generate modules/manifests → **human** (or separate IaC platform) plans/applies |
| **Gaps to ■■■■■ (5/5)** | None of the five is a cloud control plane (apply/drift/heal). |


<h5 id="d-deploy-infra-best">Best-in-class — ■■■□□ <strong>3/5</strong> · <a href="#m-deploy-infra-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Spacelift / Harness IaC + agent-written modules |
| **Mechanic** | Agent writes IaC → platform applies with policy |
| **Gaps to ■■■■■ (5/5)** | Still not unattended prod by default; none of the five coding agents is a cloud control plane. |


<a id="deep-dive-maintain"></a>

### Maintain

<a id="d-maintain-monitor"></a>

#### Monitor


<h5 id="d-maintain-monitor-claude">Claude Code — ■□□□□ <strong>1/5</strong> · <a href="#m-maintain-monitor-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | No first-party watcher (MCP only if wired) |
| **Mechanic** | External observability tools required |
| **Gaps to ■■■■■ (5/5)** | No native prod telemetry product |


<h5 id="d-maintain-monitor-antigravity">Antigravity — ■□□□□ <strong>1/5</strong> · <a href="#m-maintain-monitor-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | No first-party watcher |
| **Mechanic** | External observability tools required |
| **Gaps to ■■■■■ (5/5)** | No native prod telemetry product |


<h5 id="d-maintain-monitor-copilot">GitHub Copilot — ■□□□□ <strong>1/5</strong> · <a href="#m-maintain-monitor-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Repo automations (not APM) |
| **Mechanic** | Event→task; not live service health |
| **Gaps to ■■■■■ (5/5)** | No first-party APM / change-health product |


<h5 id="d-maintain-monitor-codex">Codex — ■□□□□ <strong>1/5</strong> · <a href="#m-maintain-monitor-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | No first-party watcher |
| **Mechanic** | External observability tools required |
| **Gaps to ■■■■■ (5/5)** | No native prod telemetry product |


<h5 id="d-maintain-monitor-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-monitor-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Rollouts** (Teams/Enterprise) |
| **Mechanic** | PR opens → rollout plan → deploy events → logs/metrics/traces per env on a schedule → issue on regression; **no auto-rollback** |
| **Gaps to ■■■■■ (5/5)** | Plan-gated; not a full APM suite |
| **Sources** | [Rollouts](https://cursor.com/docs/rollouts) |


<h5 id="d-maintain-monitor-best">Best-in-class — ■■■■□ <strong>4/5</strong> · <a href="#m-maintain-monitor-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Datadog Bits** + Cursor Rollouts |
| **Mechanic** | Detect/investigate in telemetry; tie health to the change that shipped |
| **Gaps to ■■■■■ (5/5)** | Prod actions usually approval-gated |


<a id="d-maintain-incident"></a>

#### Incident response

<h5 id="d-maintain-incident-claude">Claude Code — ■■□□□ <strong>2/5</strong> · <a href="#m-maintain-incident-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Slack `@Claude` / **Claude Tag** (Team/Enterprise; public beta); `anthropics/claude-code-action@v1`; cloud scheduled tasks (`/schedule`, research preview); pipe logs into CLI |
| **Mechanic** | Signal (chat/issue/Action/schedule) → Claude diagnoses in cloud or CI → proposes/pushes a fix PR. |
| **Gaps to ■■■■■ (5/5)** | Not an on-call investigate→remediate→verify product like Bits/Paige. |
| **Sources** | [Slack](https://code.claude.com/docs/en/slack), [Platforms](https://code.claude.com/docs/en/platforms), [GitHub Actions](https://code.claude.com/docs/en/github-actions), [Scheduled tasks](https://code.claude.com/docs/en/routines) |

<h5 id="d-maintain-incident-antigravity">Antigravity — ■□□□□ <strong>1/5</strong> · <a href="#m-maintain-incident-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/automation`, `/schedule`, headless `agy -p` — custom wiring only |
| **Mechanic** | No first-party investigate→remediate→verify IR product; teams can wire schedules/CI themselves. |
| **Gaps to ■■■■■ (5/5)** | No dedicated IR loop documented. |
| **Sources** | [/automation](https://antigravity.google/docs/commands/automation/), [Headless](https://antigravity.google/docs/cli/headless) |

<h5 id="d-maintain-incident-copilot">GitHub Copilot — ■■□□□ <strong>2/5</strong> · <a href="#m-maintain-incident-copilot"><strong>↑ matrix cell</strong></a></h5>


Automations / assign cloud agent / security campaign alert fixes → PR. Not a full SRE agent with runbooks + live telemetry. · [Copilot on GitHub](https://docs.github.com/en/copilot/concepts/copilot-surfaces/copilot-on-github)

<h5 id="d-maintain-incident-codex">Codex — ■■□□□ <strong>2/5</strong> · <a href="#m-maintain-incident-codex"><strong>↑ matrix cell</strong></a></h5>


Cloud tasks / Action / MCP with supplied context → investigate → PR. Same gap vs AI SRE products.

<h5 id="d-maintain-incident-cursor">Cursor — ■■□□□ <strong>2/5</strong> · <a href="#m-maintain-incident-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Rollouts **Fix issue** → cloud agent; Automations from webhooks/Slack |
| **Mechanic** | Regression issue → start cloud agent → PR. Explicitly **no** auto revert/rollback. |
| **Gaps to ■■■■■ (5/5)** | No autonomous production remediation authority. |
| **Sources** | [Rollouts](https://cursor.com/docs/rollouts) |

<h5 id="d-maintain-incident-best">Best — ■■■■□ <strong>4/5</strong> · <a href="#m-maintain-incident-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Datadog Bits Remediation**; **PagerDuty Paige** |
| **Mechanic** | Alert → investigate with telemetry/runbooks → recommend or approval-gated remediate (rollback, infra action, code-fix PR) → verify recovery. |
| **Gaps to ■■■■■ (5/5)** | Production actions are usually still approval-gated by design. |
| **Sources** | [Bits Remediation](https://docs.datadoghq.com/bits_ai/bits_remediation.md), [Paige](https://docs.pagerduty.com/ai-automation/advance/sre-agent) |

<a id="d-maintain-debt"></a>

#### Debt / refactor


<h5 id="d-maintain-debt-claude">Claude Code — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-debt-claude"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Cloud scheduled tasks via `/schedule` (alias `/routines`; **research preview**); GitHub Action cron/`prompt` automation with `anthropics/claude-code-action@v1` |
| **Mechanic** | Schedule or event → agent audits deps/debt/vulns → opens PR → **human reviews** |
| **Gaps to ■■■■■ (5/5)** | Continuous unattended debt elimination is not documented as a finished product capability. Scheduled tasks are research preview. |
| **Sources** | [Scheduled tasks](https://code.claude.com/docs/en/routines), [GitHub Actions](https://code.claude.com/docs/en/github-actions) |


<h5 id="d-maintain-debt-antigravity">Antigravity — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-debt-antigravity"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | `/automation` persistent sidecars (App Automations tab); conversation `/schedule` timers; headless `agy -p` / `--print` in CI |
| **Mechanic** | Cron/automation or CI prompt → agent audits deps/debt/vulns → opens PR → **human reviews**. Note: `/schedule` is conversation-scoped; use `/automation` for jobs that outlive a session. |
| **Gaps to ■■■■■ (5/5)** | Continuous unattended debt elimination is not documented as a finished product capability. |
| **Sources** | [/automation](https://antigravity.google/docs/commands/automation/), [/schedule](https://antigravity.google/docs/commands/schedule/), [Headless](https://antigravity.google/docs/cli/headless) |


<h5 id="d-maintain-debt-copilot">GitHub Copilot — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-debt-copilot"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Copilot **automations** (cloud/local); repository **GitHub Agentic Workflows** (markdown → Actions); security campaigns / agentic autofix for CodeQL alerts |
| **Mechanic** | Schedule or repo event → cloud agent or agentic workflow → PR → **human reviews**. Automations require private/internal repos + cloud-agent policy. |
| **Gaps to ■■■■■ (5/5)** | Continuous unattended debt elimination is not documented as a finished product capability. |
| **Sources** | [Automations](https://docs.github.com/en/copilot/concepts/agent-capabilities/agent-powered-workflows-and-operations/about-automations), [Agentic Workflows](https://docs.github.com/en/copilot/concepts/agent-capabilities/agent-powered-workflows-and-operations/about-github-agentic-workflows), [Security campaigns](https://docs.github.com/en/code-security/concepts/security-at-scale/about-security-campaigns) |


<h5 id="d-maintain-debt-codex">Codex — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-debt-codex"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | ChatGPT/Codex **scheduled tasks** (web/desktop; CLI has no Scheduled UI); `openai/codex-action@v1` in cron GitHub Actions workflows |
| **Mechanic** | Schedule or CI cron → agent audits deps/debt/vulns → opens PR → **human reviews** |
| **Gaps to ■■■■■ (5/5)** | Continuous unattended debt elimination is not documented as a finished product capability. |
| **Sources** | [Scheduled tasks](https://learn.chatgpt.com/docs/automations.md), [codex-action](https://github.com/openai/codex-action) |


<h5 id="d-maintain-debt-cursor">Cursor — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-debt-cursor"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | **Automations** (schedules/events); Cursor-managed **Security Review** and **Vulnerability Remediation** agents under Automations |
| **Mechanic** | Schedule or PR/event trigger → cloud agent sweep → PR → **human reviews** |
| **Gaps to ■■■■■ (5/5)** | Continuous unattended debt elimination is not documented as a finished product capability. |
| **Sources** | [Automations](https://cursor.com/docs/cloud-agent/automations) |


<h5 id="d-maintain-debt-best">Best-in-class — ■■■□□ <strong>3/5</strong> · <a href="#m-maintain-debt-best"><strong>↑ matrix cell</strong></a></h5>


| | |
| --- | --- |
| **Tools** | Devin automations + Cursor sweeps |
| **Mechanic** | Schedule or event → agent audits deps/debt/vulns → opens PR → **human reviews** |
| **Gaps to ■■■■■ (5/5)** | Continuous unattended debt elimination is not documented as a finished product capability. |


---

## Decision guide
<a id="decision-guide"></a>

**Do not pick from an equal-weight average.** Weight the stages you care about:

| If your bottleneck is… | Prefer | Why |
| --- | --- | --- |
| Editable plan → build | **Cursor** (■■■■□ Requirements) | Strongest first-party Plan Mode |
| Keep GitHub PRs green / CI fix | **GitHub Copilot** (■■■■□ CI/CD) | `/pr` + Agent Merge |
| Coding harness + Chrome verify + SDLC playbook | **Claude Code** | `/plan`, Chrome, Code Review, Actions, `/schedule` |
| Terminal/Cloud + GH Action + PR review | **Codex** | Solid implement/review/CI action |
| Parallel local agents + browser verify + Gemini SDK | **Antigravity** | Strong agent/browser/SDK; thinner merge/maintain |
| UX authoring | **Figma AI / Make** (+ Cursor Figma MCP) | None of the five alone |
| Prod monitor / incident | **Cursor Rollouts** + **Datadog Bits / Paige** | Only Cursor has first-party change-health among the five |

**One primary coding-agent platform today:** **Cursor** for widest first-party span; **GitHub Copilot** if GitHub PR/CI/merge is the decisive bottleneck. Pair with Figma + observability/SRE for Design and Maintain.

**Shared blockers to ■■■■■:** design authoring, infra/CD control planes, AI SRE stacks, and documented human/policy gates.

---

## Primary sources

Official docs cited per cell in Deep dive. Key entry points:

- **Claude Code** — [Overview](https://code.claude.com/docs/en/overview/), [Commands](https://code.claude.com/docs/en/commands), [Permission modes](https://code.claude.com/docs/en/permission-modes) (incl. plan mode), [Code Review](https://code.claude.com/docs/en/code-review), [Scheduled tasks](https://code.claude.com/docs/en/routines), [GitHub Actions](https://code.claude.com/docs/en/github-actions), [Chrome](https://code.claude.com/docs/en/chrome), [Slack / Claude Tag](https://code.claude.com/docs/en/slack).
- **Google Antigravity** — [Product](https://antigravity.google/), [Plan](https://antigravity.google/docs/plan/), [Browser](https://antigravity.google/docs/commands/browser/), [Headless CLI](https://antigravity.google/docs/cli/headless/), [Automation](https://antigravity.google/docs/commands/automation/), [Schedule](https://antigravity.google/docs/commands/schedule/).
- **GitHub Copilot** — [About agents](https://docs.github.com/en/copilot/concepts/agent-capabilities/about-agents/about-github-copilot-agents), [App sessions](https://docs.github.com/en/copilot/how-tos/github-copilot-app/agent-sessions), [IDE Plan mode](https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode), [`/pr`](https://docs.github.com/en/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests), [Agent Merge](https://docs.github.com/en/copilot/how-tos/copilot-on-github/use-copilot-agents/watch-and-fix-pull-requests), [Automations](https://docs.github.com/en/copilot/concepts/agent-capabilities/agent-powered-workflows-and-operations/about-automations), [Agentic Workflows](https://docs.github.com/en/copilot/concepts/agent-capabilities/agent-powered-workflows-and-operations/about-github-agentic-workflows).
- **Codex** — [CLI](https://learn.chatgpt.com/docs/codex/cli), [AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md.md), [GitHub review](https://learn.chatgpt.com/docs/third-party/github), [Scheduled tasks](https://learn.chatgpt.com/docs/automations.md), [codex-action](https://github.com/openai/codex-action).
- **Cursor** — [Plan Mode](https://cursor.com/docs/agent/plan-mode), [Cloud Agents](https://cursor.com/docs/cloud-agent), [Computer use](https://cursor.com/docs/cloud-agent/capabilities), [Automations](https://cursor.com/docs/cloud-agent/automations), [Bugbot](https://cursor.com/docs/bugbot), [Rollouts](https://cursor.com/docs/rollouts), [Figma MCP](https://help.figma.com/hc/en-us/articles/39889260656407-Cursor-and-Figma-Set-up-the-MCP-server).
- **Best-in-class references** — [Linear Agent](https://linear.app/docs/linear-agent), [Figma AI](https://www.figma.com/ai/), [Devin](https://devin.ai/), [Momentic](https://momentic.ai/docs/get-started/how-momentic-works), [mabl](https://help.mabl.com/hc/en-us/articles/37947539774612-Agentic-test-authoring-capabilities), [Datadog Bits Remediation](https://docs.datadoghq.com/bits_ai/bits_remediation.md), [PagerDuty Paige](https://docs.pagerduty.com/ai-automation/advance/sre-agent), [Harness CD](https://www.harness.io/products/use-cases/ai-dlc), [Spacelift](https://spacelift.io/).
