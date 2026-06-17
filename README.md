# Claire — marketplace

This repository is a thin **marketplace** for [Claire](https://github.com/janikithup/Claire),
a de-priming adversarial-critique plugin for Claude Code. It contains only a
`marketplace.json` pointing at Claire's own repository — installing from here does
**not** vendor a copy; you always get the latest Claire from its source repo.

## Why a separate marketplace repo?

A `marketplace.json` sitting *inside* a plugin folder makes the loader treat that
folder as a marketplace rather than a plugin, which breaks the simple
clone-into-skills-dir install. Keeping the marketplace manifest in its own repo
lets both install routes work cleanly.

## Install

**Claude Desktop** — open the plugins panel → *Add marketplace* → enter:

```
janikithup/claire-marketplace
```

Claire then appears in the panel. It installs **disabled by default** (`defaultEnabled: false`),
so nothing fires until you enable it — it is never silently always-on.

**Claude Code (CLI):**

```
/plugin marketplace add janikithup/claire-marketplace
/plugin install claire@claire-marketplace
```

> `defaultEnabled: false` needs Claude Code v2.1.154 or newer; older clients install it enabled.

### Alternative: direct clone (no marketplace)

If you prefer, skip the marketplace and clone Claire straight into your skills folder:

```
git clone https://github.com/janikithup/Claire.git ~/.claude/skills/claire
```

Use **one** route per machine, not both — two copies double-load Claire's hooks and agents.

## License

MIT — see [LICENSE](LICENSE). Claire is an independent, community-built project, not
affiliated with or endorsed by Anthropic.
