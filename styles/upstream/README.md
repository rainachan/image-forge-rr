# Upstream mirrors

This folder holds **unmodified** YAML files mirrored from the upstream
[`ChenyqThu/image-forge`](https://github.com/ChenyqThu/image-forge) project.

These are not original work — they are pulled in verbatim so this repo can
serve as a single drop-in style library without forcing a clone of the full
upstream. Credit and authorship belong to the original authors named inside
each YAML's `source` field.

## What's mirrored here

| File | Upstream id | Original source (from the YAML) |
|------|-------------|---------------------------------|
| `constructivism.yaml`    | `constructivism`    | `sallyn@linux.do/2044964` |
| `glitch-window-v1.yaml`  | `glitch-window-v1`  | upstream image-forge |
| `glitch-window-v2.yaml`  | `glitch-window-v2`  | upstream image-forge |
| `mixed-media.yaml`       | `mixed-media`       | upstream image-forge |
| `tri-color.yaml`         | `tri-color`         | upstream image-forge |

## Sync policy

When the upstream repo updates, refresh with:

```bash
cd /tmp && git clone --depth 1 https://github.com/ChenyqThu/image-forge.git
cp /tmp/image-forge/styles/{constructivism,glitch-window-v1,glitch-window-v2,mixed-media,tri-color}.yaml \
   path/to/image-forge-rr/styles/upstream/
```

Do not edit these files in place. If a tweak is needed, copy the YAML up one
level into `styles/` and rename it (e.g. `<name>-rr.yaml`) so it's clear which
ones are upstream-pristine and which ones are local variants.

## License

The upstream `image-forge` repo states "Signature 风格 YAML（原创）：MIT".
Files in this folder are redistributed under MIT, with original authorship
preserved in each YAML's `source` field.
