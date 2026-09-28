# AGENTS.md — pod-charly-automation

Standalone repo for the `charly-automation` concept candy — it ships no install
content and owns the automation family's `skill:` entities (the documentation
for the charly automation surface: agent control plane, aliases, encrypted
volumes, sidecars, tmux, udev, OpenClaw, Crabbox). The entities live in
`charly.yml` at the repo root; `candy/plugin-marketplace` regenerates the
standalone opencharly/marketplace corpus from them.

Canonical files:

- `charly.yml` — the `charly-automation:` concept candy entity plus the family's
  `skill:` entities (`agent-skill`, `alias-skill`, `enc-skill`,
  `openclaw-deploy-skill`, `sidecar-skill`, `tmux-skill`, `udev-skill`,
  `agent-control-operator-skill`, `crabbox-deploy-skill`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- The owning skill for the surface you are changing, e.g.
  `/charly-automation:agent` (the agent control plane), `/charly-automation:tmux`,
  `/charly-automation:alias`, `/charly-automation:enc` (encrypted volumes),
  `/charly-automation:sidecar`, `/charly-automation:udev`,
  `/charly-automation:openclaw-deploy`, `/charly-automation:crabbox-deploy`.
  Load the one whose `skill:` entity you are editing.
- `/charly-internals:skills` — the skill maintenance rules (author on the
  entity, regenerate the corpus, never hand-edit a projected `SKILL.md`).
- `/charly-internals:git-workflow` — before any git/PR action.

## Build / validate / test

- `charly box validate` at the repo root — the structural check: the manifest
  must parse and validate at the installed charly.
- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no**
  per-repo candy gate. Its only workflow file is
  `.github/workflows/tag-on-merge.yml`.
- The candy is documentation-only: its `plan:` is a `true` no-op plus a `true`
  `check:` that the skill entities are present and generated into the
  marketplace. There is no live bed.

## Modify this repo

- The `skill:` entities are the projected usage sources. Edit them here, never
  the generated `SKILL.md` in the marketplace corpus; a corpus regeneration
  (`charly marketplace generate`) projects them.
- Keep each entity's `name` / `family` / `owner` fields and the projection path
  (`marketplace/automation/skills/<name>/`) consistent; a rename must sweep every
  `/charly-automation:<old>` cross-reference in the same change.
- Keep the concept candy's `plan:` no-op; it exists only to carry the entities.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
