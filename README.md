# renovate-config-npmx

Renovate preset that adds [npmx.dev](https://npmx.dev) badges to dependency update PR bodies. Only applies to npm dependencies.

## Usage

Add to your `renovate.json`:

```json
{
  "extends": [
    "config:best-practices",
    "github>OrbisK/renovate-config-npmx"
  ]
}
```

This adds a single **npmx** column containing badges for downloads, license, types, size, vulnerabilities, and deprecated status.

The default `prBodyColumns` are: `Package`, `Change`, `Age`, `Confidence`, `npmx`.

### Minimal preset

A lighter-weight alternative showing downloads, vulnerabilities, and deprecated as individual columns:

```json
{
  "extends": [
    "config:best-practices",
    "github>OrbisK/renovate-config-npmx:minimal"
  ]
}
```

### Individual presets

Each badge type is available as a standalone preset with its own column:

| Preset | Column | Badge |
|--------|--------|-------|
| `github>OrbisK/renovate-config-npmx:version` | npmx version | ![version](https://npmx.dev/api/registry/badge/version/vue) |
| `github>OrbisK/renovate-config-npmx:license` | npmx license | ![license](https://npmx.dev/api/registry/badge/license/vue) |
| `github>OrbisK/renovate-config-npmx:size` | npmx size | ![size](https://npmx.dev/api/registry/badge/size/vue) |
| `github>OrbisK/renovate-config-npmx:downloads` | npmx downloads | ![downloads](https://npmx.dev/api/registry/badge/downloads/vue) |
| `github>OrbisK/renovate-config-npmx:downloads-day` | npmx downloads-day | ![downloads-day](https://npmx.dev/api/registry/badge/downloads-day/vue) |
| `github>OrbisK/renovate-config-npmx:downloads-week` | npmx downloads-week | ![downloads-week](https://npmx.dev/api/registry/badge/downloads-week/vue) |
| `github>OrbisK/renovate-config-npmx:downloads-month` | npmx downloads-month | ![downloads-month](https://npmx.dev/api/registry/badge/downloads-month/vue) |
| `github>OrbisK/renovate-config-npmx:downloads-year` | npmx downloads-year | ![downloads-year](https://npmx.dev/api/registry/badge/downloads-year/vue) |
| `github>OrbisK/renovate-config-npmx:vulnerabilities` | npmx vulnerabilities | ![vulnerabilities](https://npmx.dev/api/registry/badge/vulnerabilities/vue) |
| `github>OrbisK/renovate-config-npmx:dependencies` | npmx dependencies | ![dependencies](https://npmx.dev/api/registry/badge/dependencies/vue) |
| `github>OrbisK/renovate-config-npmx:created` | npmx created | ![created](https://npmx.dev/api/registry/badge/created/vue) |
| `github>OrbisK/renovate-config-npmx:updated` | npmx updated | ![updated](https://npmx.dev/api/registry/badge/updated/vue) |
| `github>OrbisK/renovate-config-npmx:engines` | npmx engines | ![engines](https://npmx.dev/api/registry/badge/engines/vue) |
| `github>OrbisK/renovate-config-npmx:types` | npmx types | ![types](https://npmx.dev/api/registry/badge/types/vue) |
| `github>OrbisK/renovate-config-npmx:maintainers` | npmx maintainers | ![maintainers](https://npmx.dev/api/registry/badge/maintainers/vue) |
| `github>OrbisK/renovate-config-npmx:deprecated` | npmx deprecated | ![deprecated](https://npmx.dev/api/registry/badge/deprecated/vue) |
| `github>OrbisK/renovate-config-npmx:name` | npmx name | ![name](https://npmx.dev/api/registry/badge/name/vue) |
| `github>OrbisK/renovate-config-npmx:likes` | npmx likes | ![likes](https://npmx.dev/api/registry/badge/likes/vue) |

### Columns preset

The `columns` preset defines all badge column definitions without setting `prBodyColumns`. Use it when you want full control over which columns appear:

```json
{
  "extends": [
    "config:best-practices",
    "github>OrbisK/renovate-config-npmx:columns"
  ],
  "packageRules": [
    {
      "matchDatasources": ["npm"],
      "prBodyColumns": ["Package", "Change", "npmx downloads", "npmx types"]
    }
  ]
}
```

Available column names: `npmx` (all badges combined), `npmx version`, `npmx license`, `npmx size`, `npmx downloads`, `npmx downloads-day`, `npmx downloads-week`, `npmx downloads-month`, `npmx downloads-year`, `npmx vulnerabilities`, `npmx dependencies`, `npmx created`, `npmx updated`, `npmx engines`, `npmx types`, `npmx maintainers`, `npmx deprecated`, `npmx name`, `npmx likes`.

## Customizing `prBodyColumns`

Each preset sets `prBodyColumns` to include its badge column(s). Since `prBodyColumns` is **not merged** across presets — the last preset in the `extends` array wins — you may need to override it in your config if you combine this preset with others that also define `prBodyColumns`.

To override, define `prBodyColumns` directly in your `renovate.json`:

```json
{
  "extends": [
    "config:best-practices",
    "github>OrbisK/renovate-config-npmx"
  ],
  "prBodyColumns": ["Package", "Type", "Update", "Change", "npmx"]
}
```

## Usage with Merge Confidence

The default and minimal presets already include `Age` and `Confidence` in their `prBodyColumns`, so they work alongside Merge Confidence out of the box.

If you use `mergeConfidence:all-badges` (which adds `Adoption` and `Passing` columns), place this preset **after** the merge confidence preset so the npmx columns are included:

```json
{
  "extends": [
    "config:best-practices",
    "mergeConfidence:all-badges",
    "github>OrbisK/renovate-config-npmx"
  ]
}
```

If you want all Merge Confidence columns (`Adoption`, `Passing`) alongside the npmx badges, override `prBodyColumns` explicitly:

```json
{
  "extends": [
    "config:best-practices",
    "mergeConfidence:all-badges",
    "github>OrbisK/renovate-config-npmx"
  ],
  "prBodyColumns": ["Package", "Change", "Age", "Adoption", "Passing", "Confidence", "npmx"]
}
```

## Badges by npmx.dev

Badge data is provided by [npmx.dev](https://docs.npmx.dev/guide/badges). Each badge links to the package page on npmx.dev.
