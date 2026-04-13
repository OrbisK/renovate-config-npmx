# renovate-config-npmx

Renovate preset that adds [npmx.dev](https://npmx.dev) badges to dependency update PR bodies.

## Usage

Add to your `renovate.json`:

```json
{
  "extends": [
    "config:recommended",
    "github>OrbisK/renovate-config-npmx"
  ]
}
```

This adds a single **npmx** column to the PR body table containing badges for downloads, license, types, size, vulnerabilities, and deprecated status.

## Individual presets

Each badge type is available as a standalone preset with its own column:

| Preset | Column | Badge |
|--------|--------|-------|
| `github>OrbisK/renovate-config-npmx:downloads` | npmx downloads | ![downloads](https://npmx.dev/api/registry/badge/downloads/vue) |
| `github>OrbisK/renovate-config-npmx:license` | npmx license | ![license](https://npmx.dev/api/registry/badge/license/vue) |
| `github>OrbisK/renovate-config-npmx:types` | npmx types | ![types](https://npmx.dev/api/registry/badge/types/vue) |
| `github>OrbisK/renovate-config-npmx:size` | npmx size | ![size](https://npmx.dev/api/registry/badge/size/vue) |
| `github>OrbisK/renovate-config-npmx:vulnerabilities` | npmx vulnerabilities | ![vulnerabilities](https://npmx.dev/api/registry/badge/vulnerabilities/vue) |
| `github>OrbisK/renovate-config-npmx:deprecated` | npmx deprecated | ![deprecated](https://npmx.dev/api/registry/badge/deprecated/vue) |

Individual presets can be combined — each adds its own column:

```json
{
  "extends": [
    "config:recommended",
    "github>OrbisK/renovate-config-npmx:downloads",
    "github>OrbisK/renovate-config-npmx:types"
  ]
}
```

## Badges by npmx.dev

Badge data is provided by [npmx.dev](https://docs.npmx.dev/guide/badges). Each badge links to the package page on npmx.dev.
