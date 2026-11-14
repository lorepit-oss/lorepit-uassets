# UAsset Viewer — lorepit fork

**This is a fork of [UAsset Viewer](https://github.com/1danielcoelho/uassets) by Daniel Coelho
(MIT).** The upstream history is kept in full, and the original licence is unchanged in
[LICENSE](LICENSE). See [NOTICE.md](NOTICE.md) for the credit, and [CHANGES.md](CHANGES.md) for every
way this fork differs from upstream: three small parser changes that let a caller parse a package from
partial reads, each also offered upstream as a pull request.

[lorepit](https://lorepit.com) vendors the parser from this repository to inspect Unreal packages in
its web preview, wiki and CLI. Changes that are not lorepit-specific are offered back upstream.

The upstream README follows.

---

# UAsset Viewer

A fully client-side browser tool for inspecting Unreal Engine `.uasset` and `.umap` files.

**[Try it live →](https://1danielcoelho.github.io/uassets/)**

Files are parsed entirely in your browser — nothing is uploaded to any server.

## Features

- **Hex viewer** — virtual-scrolling canvas with color-coded byte ranges; every byte is shown
- **Annotations panel** — collapsible tree of named byte ranges with size, name, and value columns
- **Summary panel** — asset class, engine version, package path, and embedded thumbnail (if present)
- **Minimap** — proportional overview of the file with viewport indicator
- **Search** — find by hex bytes, ASCII text, byte address, or annotation name (Ctrl+F / Ctrl+G)
- **Context menus** — copy address, raw bytes, or ASCII text from any annotated region
- **Options** — toggle address display between hexadecimal and decimal

## Supported asset types

Static Meshes, Blueprints, Materials, Material Instances, Textures, Level maps, and more. Unknown asset classes are still fully displayed at the binary level.

## Development

| Command | Description |
|---|---|
| `bun run dev` | Start dev server at `http://localhost:3000` with live reload |
| `bun run build` | Bundle to `dist/` for deployment |
| `bun test` | Run parser unit tests |
| `bun run dump <file.uasset>` | Dump parsed annotations to stdout |

Requires [Bun](https://bun.sh).

## Tech stack

- Vanilla TypeScript + HTML/CSS — no framework
- Canvas-based hex viewer with virtual scrolling
- Bun for bundling, dev server, and tests
- Deployed to GitHub Pages via static build

## License

[MIT](LICENSE)
