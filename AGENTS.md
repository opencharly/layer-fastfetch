# AGENTS.md — layer-fastfetch

Standalone candy repo for the `fastfetch` layer — the fast system-information
tool (neofetch successor). The candy lives in `charly.yml` at the repo root: the
per-distro package arms, the `check:`/`agent-check:` assertions, and the
embedded `skill:` entity projected into the marketplace corpus as
`/charly-selkies:fastfetch`.

Canonical files:

- `charly.yml` — the `fastfetch:` candy entity and the `fastfetch-skill:` skill
  entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-selkies:fastfetch` — the owning skill. The binary, its version banner,
  and the pipe-mode report. Load before editing or troubleshooting the layer.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`/`agent-check:`, per-distro `distro:` arms,
  package sections). Load before editing any entity field or plan step.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- The candy's `plan:` `check:` steps are the functional evidence: the
  `/usr/bin/fastfetch` binary, the `--version` banner matching `[0-9]+\.[0-9]+`,
  and a pipe-mode report run. They must stay valid on the `arch`/`fedora` arms
  they run on.

## Modify this repo

- Edit the `fastfetch:` candy entity AND the `fastfetch-skill:` skill entity in
  `charly.yml` together. The skill is the projected usage source, so a package or
  behaviour change not mirrored in the skill leaves the corpus stale.
- `fastfetch` is deliberately NOT in Ubuntu noble main; do not add an Ubuntu arm
  here without re-checking availability (the `dev-tools` candy documents the
  same constraint).
- New behaviour claims belong in the `plan:` as an observable `check:` step, and
  in the skill body.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
