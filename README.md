# fastfetch

Fast system-information report (neofetch successor) covering OS, kernel, CPU,
and memory.

The `fastfetch` candy installs the `fastfetch` package on Arch and Fedora,
landing the `/usr/bin/fastfetch` binary. `fastfetch` prints a system-information
report (OS, kernel, host, CPU, GPU, memory) beside an ASCII distro logo and
exposes a `--version` flag, so both its presence and its runtime behaviour are
verifiable inside a disposable container.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `fastfetch` |
| Binary | `/usr/bin/fastfetch` |
| Distro | `arch`, `fedora` |
| Service / port | none |

## How to use it

Compose the layer as an inline list in a box body:

```yaml
my-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-fastfetch:v2026.239.1627'
```

Then, inside the built image:

```bash
fastfetch --version                 # fastfetch x.y.z
fastfetch --pipe --logo none        # system-information report
```

## Layout

- `charly.yml` — the `fastfetch:` candy entity (the per-distro package arms and
  the `check:`/`agent-check:` assertions) and the embedded `fastfetch-skill:`
  skill entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-selkies:fastfetch`
- Included in: `/charly-selkies:sway-desktop` and `/charly-selkies:selkies-desktop-layer`
  metalayers (and their variants)
- Also packaged by: `/charly-coder:dev-tools`
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
