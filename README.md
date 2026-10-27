# charly-automation

**RETIRED — this repo authors no skill any more.** It was the `charly-automation` family's
concept candy and owned the automation family's `skill:` entities. All nine of them — eight
skills and one `type: agent` definition — have moved beside the command, plugin, image or
contract each one documents (opencharly/opencharly#600, #628), byte-identical at every
destination. It is archived once its drain has merged and been tagged.

## Where the prose went

| entity | now authored in |
|---|---|
| `agent` | [`opencharly/plugin-agent`](https://github.com/opencharly/plugin-agent) — `.agents/skills/agent/SKILL.md` |
| `alias` | [`opencharly/plugin-alias`](https://github.com/opencharly/plugin-alias) — `.agents/skills/alias/SKILL.md` |
| `enc` | [`opencharly/plugin-enc`](https://github.com/opencharly/plugin-enc) — `.agents/skills/enc/SKILL.md` |
| `openclaw-deploy` | [`opencharly/layer-openclaw`](https://github.com/opencharly/layer-openclaw) — `.agents/skills/openclaw-deploy/SKILL.md` |
| `sidecar` | [`opencharly/plugin-deploy-pod`](https://github.com/opencharly/plugin-deploy-pod) — `.agents/skills/sidecar/SKILL.md` |
| `tmux` | [`opencharly/plugin-tmux`](https://github.com/opencharly/plugin-tmux) — `.agents/skills/tmux/SKILL.md` |
| `udev` | [`opencharly/plugin-udev`](https://github.com/opencharly/plugin-udev) — `.agents/skills/udev/SKILL.md` |
| `crabbox-deploy` | [`opencharly/distro-cachyos`](https://github.com/opencharly/distro-cachyos) — `.agents/skills/crabbox-deploy/SKILL.md` |
| `agent-control-operator` | [`opencharly/plugin-agent`](https://github.com/opencharly/plugin-agent) — `.agents/agents/agent-control-operator.md` |

`family:` was kept unchanged on every move, so every existing `/charly-automation:<name>`
address still resolves — from the repo that now authors it. The full per-entity derivation
(which entity each body's own prose names, and the blob comparison) is in `AGENTS.md`.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-automation` (retired concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | nothing: no `skill:` or `agent` node |
| Projected to | nowhere — the corpus publishes these bodies from the repos above |
| Service / port | none |

## How to use it

Do not. Read a skill from the repo that authors it (the table above), or from the projected
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus. The runtime
commands these skills document are provided by the `charly` binary itself, never by this
repo.

## Layout

- `charly.yml` — the `charly-automation:` candy node only, with a `true` no-op `run:` step
  and a `true` no-op `check:` step. Neither is an assertion: there is no body left here to
  resolve.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — this user overview.

## Related

- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
