# Global Rules

## Git Commit Convention

All commits MUST strictly follow the [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) specification. When writing commit messages, refer to the full spec — do not take shortcuts or omit required elements.

Key requirements:

- Commit message description should be in English
- When in doubt about any rule, consult the spec at the link above

## Markdown

When writing or editing Markdown files, follow the [CommonMark](https://spec.commonmark.org/) specification.

## Language

- Communicate and respond in Chinese
- Write all code comments in English

## Skills

- Before starting a non-trivial task, scan available skills and invoke any whose description matches the work — do not rely on memory alone.
- Treat skill descriptions as triggers, not suggestions: if a skill clearly applies (e.g. planning, debugging, code review, verification, TDD), use it rather than improvising an equivalent.
- Prefer an installed skill over an ad-hoc approach when both could work.
- When unsure whether a skill applies, briefly check it rather than skip it.

## Workflow

- For major decisions (irreversible actions, architecture or schema changes, multi-step refactors, anything affecting shared/production state), explain the plan first and execute only after confirmation
- For small, routine, or easily-reversible tasks, just do them and report briefly — do not ask for confirmation on every minor step

## Environment (this machine)

Facts that change how to work here — a tool being installed ≠ on PATH, so verify with `command -v` before relying on it.

- **Runtime setup**: Node / npm / pnpm / yarn via **fnm**, Java via **jenv** (these resolve only after shell init, not at fixed system paths); Go at `/usr/local/go`; Python 3 via Homebrew — use **uv** for envs/deps.
- **Unprefixed `sort` / `date` / etc. are BSD** (macOS default); GNU coreutils are installed but only under `g`-prefixed names (e.g. `gsort`, `gdate`).
- **`docker` / `docker-compose` are backed by OrbStack** (not Docker Desktop); `kubectl` present.
- Modern CLIs available, prefer when they fit: `rg` `fd` `bat` `delta` `jq` `yq` `fzf` `gh` `lazygit`.
