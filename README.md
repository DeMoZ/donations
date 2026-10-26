# donations

Donation links and texts for DeMoZ's tools. Each tool downloads its own file when its donate window opens,
so links and texts change here without a new release of the tool.

| File | Tool |
|---|---|
| [`enhancecapcut.json`](enhancecapcut.json) | [EnhanceCapCut](https://github.com/DeMoZ/EnhanceCapCut) |

Tools read the files from
`https://raw.githubusercontent.com/DeMoZ/donations/main/<file>` and fall back to
`https://cdn.jsdelivr.net/gh/DeMoZ/donations@main/<file>`, then to their last cached copy.

## Format (`schema` 1)

```json
{
  "schema": 1,
  "message": { "en": "…", "ru": "…" },
  "methods": [
    {
      "id": "cloudtips",
      "title": { "en": "…", "ru": "…" },
      "description": { "en": "…", "ru": "…" },
      "url": "https://…"
    }
  ]
}
```

- `schema` — format version. Tools skip fields they don't know, so adding fields keeps `schema`; bump it only
  for a change old tools would misread.
- `message` — text at the top of the donate window.
- `methods` — donation options in display order. `id` is a stable key, `url` must be `https://`,
  `description` is optional.

### Localized texts

Every text is an object from a language tag to the string. A tool picks, in order:

1. the exact UI language (`pt-BR`),
2. its base language (`pt`),
3. `en`.

`en` is required in every text. A new language is added by adding its key next to `en`; nothing else changes.
