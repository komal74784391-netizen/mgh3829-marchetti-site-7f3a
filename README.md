# Lab Site Template

A minimal static-site template for the Adaptive Retrieval Lab research site.

## Layout

- `_config.yml` - site metadata and the `author` block
- `_pages/` - the site pages (`about`, `cv`, `publications`, `tooling`)
- `_publications/` - the publication collection (one Markdown file per paper)
- `_data/navigation.yml` - top navigation
- `_data/tool_registry.json` - machine-readable manifest of the lab's active tools
- `vendor/tool_sources/` - source manifests for the tool registry
- `docs/tool_registry_guide.md` - how the tool registry is assembled

## Publishing

Copy this template into your own repository, edit the pages and data files, and
push everything to the default branch.
