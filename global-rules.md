# Global Rules

Project-level instructions (CLAUDE.md / AGENTS.md in a repo) override these rules where they conflict — except the Secrets rules, which projects may tighten but never weaken.

## Git Commit Convention

All commits MUST strictly follow the [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) specification. When writing commit messages, refer to the full spec — do not take shortcuts or omit required elements.

- Commit message description should be in English

## Markdown

When writing or editing Markdown files, follow the [CommonMark](https://spec.commonmark.org/) specification.

## Language

- Communicate and respond in Chinese
- Write all code comments in English

## Skills & Tools

- Before starting a non-trivial task, scan available skills; if one clearly applies (e.g. planning, debugging, code review, TDD), invoke it rather than improvising an equivalent — treat skill descriptions as triggers, not suggestions.
- When unsure whether a skill applies, briefly check it rather than skip it.
- When a library's current behavior or API matters, prefer a purpose-built docs source or an available Ref / context7 MCP; otherwise consult official docs or installed source rather than relying on memory alone.

## Workflow

- For major decisions (irreversible actions, architecture or schema changes, multi-step refactors, anything affecting shared/production state), explain the plan first and execute only after confirmation
- For small, routine, or easily-reversible tasks, just do them and report briefly — do not ask for confirmation on every minor step

## Secrets

- Never put real credentials (API keys, tokens, passwords) in tracked files, commits, logs, docs, or examples — use `<PLACEHOLDER>` values. Store local credentials only in an intended secret store or a repo-local file verified as ignored (e.g. via `git check-ignore`).
- Before committing, check staged changes for credentials; if one is detected or suspected, stop and flag it without reproducing its value.

## Environment (this machine)

Facts that change how to work here — a tool being installed ≠ on PATH, so verify with `command -v` before relying on it.

- Runtime setup: Node / npm / pnpm / yarn via fnm, Java via jenv (these resolve only after shell init, not at fixed system paths); Go at `/usr/local/go`; Python 3 via Homebrew — use uv for envs/deps.
- Unprefixed `sort` / `date` / etc. are BSD (macOS default); GNU coreutils are installed but only under `g`-prefixed names (e.g. `gsort`, `gdate`).
- `ls` (and `ll` / `la` / `l`) is aliased to eza, whose flags and output differ from macOS `/bin/ls`; avoid parsing listing output in scripts — prefer globs, `find`, or `stat`, or use `/bin/ls` (or `command ls` to bypass aliases) when BSD `ls` behavior is required.
- `docker` / `docker-compose` are backed by OrbStack (not Docker Desktop); `kubectl` present.
- Modern CLIs available, prefer when they fit: `rg` `fd` `bat` `delta` `jq` `yq` `fzf` `gh` `lazygit`.
- Task-specific tools on hand: `ffmpeg` (audio/video), `hyperfine` (benchmarking), `mtr` / `nexttrace` (network path diagnostics), `stripe` (Stripe CLI — webhook listen/trigger), `flyctl` (Fly.io), `cloudflared` (tunnels), `openspec` (spec-driven development, npm global).
