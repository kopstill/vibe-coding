# Global Rules

These are cross-agent, cross-project defaults for engineering work on this machine. Keep this file repository-agnostic: project architecture, commands, release processes, product decisions, and local exceptions belong in the relevant repository's instructions.

Project-level instructions loaded by the active agent (for example, a repository's `CLAUDE.md` or `AGENTS.md`) may specialize or override these defaults where they conflict — except the Secrets rules, which projects may tighten but never weaken. Do not carry repository-specific assumptions or decisions into another project unless its own context establishes them.

## Engineering Principles

- **No over-engineering, no over-optimization** — build only what the task and current project need, sized to the project's scale, maturity, and constraints. Before adding a mechanism, ask: Is there an evidenced problem, and a real consumer or trigger path? What is the smallest coherent solution? Raise work beyond the authorized scope instead of silently implementing it.
- **Optimize for quality, not brevity** — the task and applicable project rules determine scope. Within that scope, improve correctness, clarity, maintainability, or effectiveness. Do not remove useful context or constraints merely to shorten code, documentation, or prompts.
- **Reuse before writing** — inspect the existing stack first: dependencies, shared helpers, components, and established patterns. Reuse when semantics and lifecycle genuinely match — the same interaction should keep the same implementation; do not force sharing or abstraction merely because code looks similar. When nothing fits, write the smallest coherent implementation. This applies to backend and frontend work alike.
- **Best practices in what you do build** — prefer existing platform capabilities. When a new dependency is justified, choose a mature, actively maintained option compatible with the project's runtime, license, and conventions. Handle real error / edge / failure paths without speculative hardening, and do not take shortcuts that create avoidable technical debt.
- **Code and comments stay in sync** — update directly affected comments and any documentation that restates the changed behavior in the same change. A comment or document that no longer matches the behavior it describes is a defect.
- **Comments are concise and load-bearing** — state the why or the non-obvious constraint, not what the code already says. More detail is not better; delete comments that merely restate the code.

## Git Commit Convention

All commits MUST strictly follow the [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) specification. Include every required element. Use optional scope, body, and footer fields only when useful, and represent breaking changes as the specification requires. When unsure, or when a message goes beyond a simple `type: description` line (scope, body, footers, breaking changes), consult the linked specification rather than reconstructing it from memory.

- Write the commit message description in English.

## Markdown

When writing or editing Markdown files, follow the [CommonMark](https://spec.commonmark.org/) specification.

## Language

- Communicate and respond in Chinese, except where another rule requires English.
- Write all code comments in English.

## Skills & Tools

- Before starting a non-trivial task, scan the available skill list and use a skill when its description clearly matches the task. If applicability is genuinely uncertain, read the relevant skill's entry file before deciding; do not invoke adjacent skills merely because they exist.
- Hooks and meta-skills may control how a selected skill runs; they do not make otherwise-unrelated skills applicable. Once a skill is selected, follow its instructions.
- When a library's behavior or API matters, use the source that answers the question: installed source for the exact installed version, and official documentation for currently supported behavior. Prefer a purpose-built documentation source, such as an available Ref or context7 MCP, over memory.

## Workflow

- For requests to answer, explain, review, diagnose, or plan, inspect the relevant materials and report the result; do not implement changes unless the request also asks for them.
- For requests to change, build, or fix, make the requested in-scope local changes and run relevant non-destructive validation. Do so without separate confirmation, subject to the exceptions below. Report the result briefly.
- For any other small, routine, or easily reversible request (running tests, starting services, querying state), just do it and report briefly, subject to the exceptions below — do not ask for confirmation step by step.
- For a substantial multi-step refactor, briefly state the plan before editing; do not require separate confirmation unless an exception below applies.
- Explain the plan and obtain confirmation before destructive or irreversible actions, and before anything affecting shared or production state (deployments, releases, config or data mutations, applying schema migrations); routine commits and pushes are governed by the version-control rule below.
- Obtain confirmation before materially different architecture or schema choices, third-party writes (posting comments, filing issues, sending messages), new production dependencies, or a meaningful expansion of scope, unless the user's request already explicitly authorizes the exact action and target; a write that mutates shared or production state stays under the rule above regardless of authorization. Read-only access and local reversible setup never require confirmation.
- Only an explicit user request triggers a commit or push; review approval, workflow completion, or the agent's own judgment never does. Such a request authorizes only the named version-control action in the current repository and intended branch — not deployment or any other external write. Non-routine variants (force-push, history rewrites) still require the confirmation above.

## Secrets

- Never put real credentials (API keys, tokens, passwords) in tracked files, commits, logs, docs, or examples — use `<PLACEHOLDER>` values. Store local credentials only in an intended secret store or a repo-local file verified as ignored (e.g. via `git check-ignore`).
- Before committing, check staged changes for credentials; if one is detected or suspected, stop and flag it without reproducing its value.

## Environment (this machine)

These are availability and compatibility facts, not mandates to use every listed tool. Do not probe tools gratuitously. When a task depends on a tool, verify it with `command -v`; installed does not imply available on `PATH`. If a non-login shell cannot resolve it, retry with full shell init (for example, `zsh -lic 'whence -p <tool>'` — `whence -p` reports only real executables; interactive aliases and functions do not exist in non-interactive tool shells) before concluding that it is missing.

- Runtime setup: Node / npm / pnpm / yarn via fnm, Java via jenv (these resolve only after shell init, not at fixed system paths); Go at `/usr/local/go`; Python 3 via Homebrew — use uv for envs/deps.
- Unprefixed `sort` / `date` / etc. are BSD (macOS default); GNU coreutils are installed but only under `g`-prefixed names (e.g. `gsort`, `gdate`).
- `ls` (and `ll` / `la` / `l`) is aliased to eza, whose flags and output differ from macOS `/bin/ls`; avoid parsing listing output in scripts — prefer globs, `find`, or `stat`, or use `/bin/ls` (or `command ls` to bypass aliases) when BSD `ls` behavior is required.
- `docker` / `docker-compose` are backed by OrbStack (not Docker Desktop); `kubectl` present.
- Modern CLIs available, prefer when they fit: `rg` `fd` `bat` `delta` `jq` `yq` `fzf` `gh` `lazygit`.
- Task-specific tools on hand: `ffmpeg` (audio/video), `hyperfine` (benchmarking), `mtr` / `nexttrace` (network path diagnostics), `stripe` (Stripe CLI — webhook listen/trigger), `flyctl` (Fly.io), `cloudflared` (tunnels), `openspec` (spec-driven development, npm global).
