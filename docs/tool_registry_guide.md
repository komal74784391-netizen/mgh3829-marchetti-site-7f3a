# Tool Registry Guide

`_data/tool_registry.json` is read by the tooling page. Each entry is:

- `name` - the tool identifier used in vendor manifests
- `description` - one sentence describing what the tool does
- `parameters` - a JSON Schema object describing the call arguments

Only tools marked `"status": "active"` may be published in the registry.
Deprecated tools stay in the vendor tree but never appear in the registry.

## Sources

`vendor/tool_sources/` holds two kinds of material:

- `upstream/` - copies of manifests as published by the external providers we
  vendor. Each package describes exactly one tool, including its call arguments.
- `internal/` - our own draft notes for tools whose manifests the provider never
  published. An internal draft lists parameters as a flat mapping from parameter
  name to a small spec object (`type`/`kind`, `description`, and optionally
  `default`, `enum` or `optional`).

## Type normalisation

Types are written the JSON Schema way in the registry:

| vendor type | registry type |
| ----------- | ------------- |
| dict        | object        |
| str         | string        |
| int         | integer       |
| float       | number        |
| bool        | boolean       |
| list        | array         |

A list type may carry `items` describing its elements.

## Optionality

A parameter is required unless its spec declares a `default` or carries
`optional: true`. Parameters that are not required are collected in the
schema's `optional` array when the source provides one.

## Internal drafts

For an internal draft, build the `parameters` block yourself: use
`type: "object"`, move every parameter spec under `properties` (keeping the
description, `default`, `enum` and optional flag), and compute `required` with
the optionality rule above.

## Reference

`vendor/tool_sources/reference/accepted_example.json` is a conversion that was
accepted in an earlier review; use it as the format reference.
