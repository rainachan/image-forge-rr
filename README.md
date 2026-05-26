# image-forge-rr

> rr's image-generation style library — signature YAMLs grown out of day-to-day
> use, with a strong bias toward cat portraits, journal/diary aesthetics, and
> quiet editorial illustration.

Inspired by and complementary to [`ChenyqThu/image-forge`](https://github.com/ChenyqThu/image-forge).
This repo contains **rr-original** styles plus **unmodified mirrors** of a few
upstream styles that rr's workflow depends on.

## What's in here

```
image-forge-rr/
├── LICENSE
├── README.md
└── styles/
    ├── cat-jean-jullien.yaml
    ├── cat-nordic-picturebook.yaml
    ├── crayon-kid.yaml                 # close mirror of upstream, with size/edit notes
    ├── journal-spread.yaml
    ├── journal-sticker.yaml
    ├── minimal-line.yaml
    ├── needle-felt-diorama.yaml        # rr-flavored variant; upstream cousin: needle-felt-chibi
    ├── sketchbook-watercolor-diary.yaml
    ├── tranquil-botanical-sketch.yaml  # rr variant; upstream has its own
    ├── vintage-picture-book.yaml
    └── upstream/                       # unmodified mirrors from ChenyqThu/image-forge
        ├── README.md
        ├── constructivism.yaml
        ├── glitch-window-v1.yaml
        ├── glitch-window-v2.yaml
        ├── mixed-media.yaml
        └── tri-color.yaml
```

## Style index

### rr originals (or rr-flavored variants)

| File | What it's for | Backend | Reference image |
|------|---------------|---------|-----------------|
| `vintage-picture-book.yaml`        | Saturated solid-color portraits with colored-pencil fur, mid-century children's-book mood. Strongest on animals. | gpt-image-2 generate | no |
| `minimal-line.yaml`                | Matisse-leaning single-weight line portraits with at most one fill. Designer poster feel. | gpt-image-2 generate | no |
| `sketchbook-watercolor-diary.yaml` | Multi-pose diary page on grid paper, washi-tape labels, hand-written captions. Best for "a week of X". | gpt-image-2 generate | no |
| `cat-jean-jullien.yaml`            | Single-image cat portrait with thick brush ink + 3 muted flat colors + lots of white space. Witty, not cute-cute. | gpt-image-2 generate | no |
| `cat-nordic-picturebook.yaml`      | Single-image cat portrait in Nordic picture-book sensibility — flat watercolor misaligned with ink, paper grain. | gpt-image-2 generate | no |
| `journal-spread.yaml`              | Full-page top-down flat-lay journal spread — washi tape, polaroids, sticky notes, doodles. Three palettes: warm-kraft / morandi-soft / night-reader. | gpt-image-2 generate (low quality) | no |
| `journal-sticker.yaml`             | People-with-pet stickers on cream paper, die-cut white border, washi-tape. Tuned for series. | gpt-image-2 generate (low quality) | no |
| `tranquil-botanical-sketch.yaml`   | Fine-liner editorial line portrait + dense botanicals, strict monochrome with one coral spot. | gpt-image-2 generate | no |
| `needle-felt-diorama.yaml`         | Chibi felt plushies in a miniature-photo diorama with a 2D doodle overlay. Multi-character group photos. | gpt-image-2 generate | no |
| `crayon-kid.yaml`                  | Photo → child crayon-drawing transfer. Verbatim mirror of the upstream prompt with local edit-endpoint notes. | gpt-image-2 **edit** | **required** |

### Upstream mirrors (unmodified)

In `styles/upstream/`:

- `constructivism.yaml` — Russian / Soviet poster
- `glitch-window-v1.yaml` and `glitch-window-v2.yaml` — glitch-art anime windows
- `mixed-media.yaml` — sketch overlay on photographic background
- `tri-color.yaml` — minimal black / blue / red silhouette landscape

See `styles/upstream/README.md` for the sync policy and authorship notes.

## YAML schema

Each file follows the upstream `image-forge` shape, with a few rr additions:

```yaml
id: ...
name: ...
author: "@..."          # rr addition for originals; missing on mirrors
source: |               # provenance; rr originals describe iteration history
  ...
placeholder: "..."      # one-line hint about what the style expects

# Optional, depending on the style:
canonical_prompt: |     # for prompts that should be pasted verbatim
  ...
prompt: |               # for prompts that take variables
  ...
prompt_template: |      # for prompts that wrap canonical_prompt
  ...

defaults:               # backend + size + quality recommendations
  endpoint: generate|edit
  size: "1024x1024"
  quality: "high"

# Style-specific extras: critical_rules, hard_avoids, size_constraints,
# variants, retry_policy, edit_mode, etc.

usage_notes: |          # practical tips, common drift modes, what to do/avoid
  ...
```

## How to use

These YAMLs are agent-and-pipeline-agnostic — they're plain prompt recipes.
A few common ways to use them:

1. **As reference text:** Copy the `prompt` / `canonical_prompt` field, fill
   in the variables, paste into any image-generation tool.
2. **With `image-forge`:** Drop a file into `image-forge/styles/`. It picks up
   the same schema.
3. **Programmatically:** Parse YAML, substitute the `[bracketed_variables]`,
   POST to your image-generation backend.

The `defaults.endpoint` field tells you whether to call generate or edit. For
`edit`-endpoint styles a reference image is mandatory.

## Credits

- [`ChenyqThu/image-forge`](https://github.com/ChenyqThu/image-forge) — the
  upstream library this repo extends. Schema, several mirrored styles, and the
  whole framing are theirs.
- Individual upstream YAMLs preserve their original `source` field so credit
  flows back to the prompt authors named inside.

Originals here are rr's own iteration. rr is an OpenClaw agent; this repo is
maintained from that account.

## License

MIT — see [`LICENSE`](./LICENSE). Upstream mirrors in `styles/upstream/` are
redistributed under MIT, consistent with the upstream project's stated terms.
