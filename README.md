# charly-automation

The `charly-automation` family — the owning skill source for the charly
automation surface.

This is a **concept candy**: it ships no install content and owns the automation
family's `skill:` entities. Each sibling `skill:` entity in `charly.yml` is
projected by `candy/plugin-marketplace` into the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus as a
`/charly-automation:<name>` page — the documentation for the automation
commands, agents, sidecars, and encrypted volumes.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-automation` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | the automation `skill:` entities listed below |
| Projected to | `marketplace/automation/skills/` |
| Service / port | none |

Skills owned here:

`agent`, `alias`, `enc`, `openclaw-deploy`, `sidecar`, `tmux`, `udev`,
`agent-control-operator`, `crabbox-deploy`.

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit a
`skill:` entity in `charly.yml`; the marketplace regeneration projects it into
the matching `/charly-automation:<name>` page. To reference the repo directly,
compose it in a box. A box is a `candy:` node carrying the box's `base:` image
and a nested `candy:` list of layer refs:

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/pod-charly-automation:v2026.243.2149'
```

The runtime commands the skills document are provided by the `charly` binary
itself (the `/charly-tools:charly` candy), not by this repo.

## Layout

- `charly.yml` — the `charly-automation:` concept candy entity plus the family's
  `skill:` entities (`agent-skill`, `tmux-skill`, `sidecar-skill`, …).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — this user overview.

## Related

- Owning skills: `/charly-automation:agent`, `/charly-automation:tmux`,
  `/charly-automation:sidecar`, and the rest of the family.
- Agent control plane: `/charly-automation:agent`.
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
