# AGENTS.md — pod-charly-automation

**This repo is RETIRED.** It authors no skill and no agent definition any more: all nine
bodies it carried have moved beside the command, plugin, image or contract each of them
documents (opencharly/opencharly#600, #628), and every one is byte-identical at its
destination. It is archived once its drain has merged and been tagged.

Canonical files:

- `charly.yml` — the `charly-automation:` candy node and nothing else. It is a real
  `candy:` because a project needs one; its `plan:` is a `true` no-op `run:` step plus a
  `true` no-op `check:` step, and **neither is an assertion** — there is no body left here
  for the body-existence gate to resolve.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — user overview only; never agent guidance.

## Where the prose went (the destination map)

Measured as git blobs: this repo's pre-drain `main` versus each destination's `origin/main`.
Every row compares equal, and a `==` beside a blob means the bytes are identical — the move
relocated the AUTHORITY over a body, it did not rewrite one.

| entity | destination repo | path | blob |
|---|---|---|---|
| `agent` | `opencharly/plugin-agent` | `.agents/skills/agent/SKILL.md` | `feca7d69d6cb` |
| `alias` | `opencharly/plugin-alias` | `.agents/skills/alias/SKILL.md` | `540ec9ee7f65` |
| `enc` | `opencharly/plugin-enc` | `.agents/skills/enc/SKILL.md` | `9f5ef6ee33be` |
| `openclaw-deploy` | `opencharly/layer-openclaw` | `.agents/skills/openclaw-deploy/SKILL.md` | `936873aab588` |
| `sidecar` | `opencharly/plugin-deploy-pod` | `.agents/skills/sidecar/SKILL.md` | `1dfe73e836fb` |
| `tmux` | `opencharly/plugin-tmux` | `.agents/skills/tmux/SKILL.md` | `8a0ad21fe458` |
| `udev` | `opencharly/plugin-udev` | `.agents/skills/udev/SKILL.md` | `388c743e0bf4` |
| `crabbox-deploy` | `opencharly/distro-cachyos` | `.agents/skills/crabbox-deploy/SKILL.md` | `612db8ebebb1` |
| `agent-control-operator` (`type: agent`) | `opencharly/plugin-agent` | `.agents/agents/agent-control-operator.md` | `78df6f61ee76` |

`crabbox-deploy` was the one destination a GATE could not decide: its own prose names four
repos (opencharly/opencharly#628), so the operator settled it on `distro-cachyos` — the repo
holding the two images it deploys, both disposable beds it runs and its plan file. Every row
above was derived from the entity's own prose, never from its name.

`family:` was kept unchanged on every move, so every existing `/charly-automation:<name>`
address still resolves — from the repo that now authors it.

## What still lives here

Only the candy node, the tag workflow and history. Nothing in this repo is a source of
guidance any more, and no consumer should compose it for its prose: compose the repo that
now authors the skill you need.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
