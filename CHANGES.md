# Changes from upstream

Upstream: [1danielcoelho/uassets](https://github.com/1danielcoelho/uassets), forked at `bebf758`
("Add LICENSE", 2026-08-30). Every way this fork differs is listed here, newest first.

## Unreleased

### Parser changes (offered upstream, one pull request each)

Three small changes to `src/parser/`, each on its own branch so upstream can take them separately.
The hex viewer, dev server, CLI and tests are as upstream left them.

- **The table parsers are exported** (`export-table-parsers`). `parseNamesTable`,
  `parseImportsTable`, `parseExportsTable`, `parseIndexTables`, `parseOpaqueBlobs`, `parseMetadata`,
  `parseGenericExport` and `resolvePackageIndex` can be called by code that holds only part of a file.
  `parseUAsset` is unchanged.
- **`BinaryReader` can read a window of the file** (`windowed-reader`). The constructor takes an
  optional `baseOffset` and `totalLength`; a reader over bytes `[baseOffset, baseOffset + length)`
  reports and seeks absolute file positions, so parsing one export needs only that export's bytes.
  A reader built with one argument behaves exactly as before.
- **FName instance numbers are kept** (`fname-instance-number`). `FObjectImport` and `FObjectExport`
  gain `objectNameNumber`, which the parser read and discarded. `StaticMeshComponent_0` and
  `StaticMeshComponent_1` are now distinguishable.

### Repository

- `NOTICE.md`, this file, and the fork section at the top of `README.md`.

## How lorepit uses this fork

[lorepit](https://lorepit.com) vendors `src/parser/**` and `src/types.ts` from a pinned commit of this
repository into its own `packages/uasset/upstream/`, with one mechanical transformation (the `.ts`
extensions on relative imports are removed). lorepit's own code on top of the parser (range-read
header inspection, per-object inspection, object-level diffs, the facts shown for each asset class)
lives in lorepit, not here. A new engine release is supported here first, then re-vendored.
