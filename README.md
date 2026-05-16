# Nikki Video Lab Registry

A Claude Code skill by Nikki Harvey for installing and wiring registry blocks and components into HyperFrames compositions. Handles the `hyperframes add` command, install locations, wiring blocks as sub-compositions, and merging component snippets into host compositions.

## What it covers

**Blocks vs components**
Two distinct types of registry items:
- **Blocks** — standalone sub-compositions with their own dimensions, duration, and timeline. Installed to `compositions/<name>.html`, wired into a host via `data-composition-src`.
- **Components** — effect snippets with no own dimensions. Installed to `compositions/components/<name>.html`, merged directly into a host composition's HTML, CSS, and script.

**Installing**
```bash
hyperframes add data-chart              # install a block
hyperframes add grain-overlay           # install a component
hyperframes add shimmer-sweep --dir .   # target a specific project
hyperframes add data-chart --json       # machine-readable output
hyperframes add data-chart --no-clipboard  # skip clipboard (CI/headless)
```

After install the CLI prints the files written and a starter snippet. The snippet needs `data-composition-id`, `data-start`, and `data-track-index` attributes added before it will work.

**Wiring blocks**
Blocks are wired into the host `index.html` via `data-composition-src`. The skill covers the required attributes (`data-composition-id`, `data-start`, `data-duration`, `data-width`, `data-height`, `data-track-index`) and the common mistakes (mismatched composition IDs, wrong track ordering).

**Wiring components**
Components are pasted in three places: HTML elements into the composition div, CSS into the style block, JS into the script before timeline code. The skill covers GSAP timeline integration for components that expose animation hooks.

**Discovery**
Browse the registry manifest to find available blocks and components, filter by type and tags.

**Install paths**
Default paths configurable in `hyperframes.json`: blocks to `compositions/`, components to `compositions/components/`.

## What's in this skill

```
SKILL.md                        — core wiring rules
references/
  demo-html-pattern.md          — example wired composition
  discovery.md                  — browsing the registry
  install-locations.md          — configuring install paths
  wiring-blocks.md              — full block wiring reference
  wiring-components.md          — full component wiring reference
examples/
  add-block.md                  — worked example: installing a block
  add-component.md              — worked example: installing a component
```

## Honest limits

- `hyperframes add` only works for blocks and components. For starter templates, use `hyperframes init --example <name>` instead.
- The skill wires items into compositions but does not create registry items or publish to the registry.
- Discovery is via the raw registry manifest — there is no search UI.

## Installing for Claude Code

```bash
git clone https://github.com/nicolakharvey/nikki-video-lab-registry.git ~/.claude/skills/nikki-video-lab-registry
```

Claude Code picks up skills from `~/.claude/skills/` automatically. No restart needed.

## Installing for Claude desktop

1. Download or clone this repo.
2. Zip the `nikki-video-lab-registry` folder.
3. In Claude desktop, go to Settings > Capabilities > Skills.
4. Upload the zip file.

## Using the skill

Once installed, Claude will use this skill automatically when you run `hyperframes add` or ask to wire a block or component. Examples:

> "Install the data-chart block and wire it into my composition at 5 seconds."
> "Add the grain-overlay component to my intro scene."
> "What blocks are available in the registry?"

---

Part of the **Nikki** suite of AI tools by [Nikki Harvey](https://linkedin.com/in/nicolakharvey).
