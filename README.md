# Universal LPC 2D Character Plugin

This Godot 4 plugin composes layered 2D characters from Universal LPC metadata and generated spritesheets. It also includes an editor dock for development-time sprite composition and source-asset auditing.

The plugin files live at this repository's root. Install the repository at `res://addons/universal_lpc` so its built-in resource paths resolve correctly.

## Installation

Clone or add this repository directly at your project's `addons/universal_lpc` path:

```sh
git submodule add https://github.com/csaga77-godot-addons/universal_lpc.git addons/universal_lpc
```

Alternatively, download the repository and copy its contents into `addons/universal_lpc`. Then enable **Universal LPC 2D Character** under **Project > Project Settings > Plugins**.

The reusable runtime entry point is [`universal_lpc_sprite_2d.gd`](universal_lpc_sprite_2d.gd), which exposes the `UniversalLpcSprite2D` node type independently of the editor dock.

## Contents

- `universal_lpc_sprite_2d.gd` - layered animated-sprite renderer
- `universal_lpc_factory.gd` - metadata and texture resolver/cache
- `universal_lpc_sprite_builder.gd` - inspector-facing selection builder
- `universal_lpc_metadata_generator.gd` - development-time metadata and combined-sheet generator
- `universal_lpc_asset_auditor.gd` - source-art and metadata coverage audit
- `universal_lpc_metadata.json` - prebuilt manifest consumed by the runtime
- `resources/spritesheets/` - generated LPC textures consumed by the manifest
- `plugin.gd` / `plugin.cfg` - editor plugin registration and dock lifecycle
- `universal_lpc_dock.gd` - editor status and workflow launcher
- `tests/` - focused generation, composition, and source-audit scenes

## Editor Dock

The `Universal LPC 2D Character` dock reports whether the prebuilt manifest and upstream source checkout are available. It provides actions to open the sprite-composition scene and run the source-asset audit scene, whose report appears in Godot's Output panel.

## Paths And Optional Source Checkout

The generated spritesheets are included under `res://addons/universal_lpc/resources/spritesheets`. The prebuilt manifest's `target_path` points at that resource directory, so runtime use does not require the upstream generator checkout.

Development-time regeneration and source auditing read an optional upstream checkout at `res://3rdparty/Universal-LPC-Spritesheet-Character-Generator` by default. That source repository is not bundled here; all source, metadata, target, and report paths can be overridden by a consuming project.

## Artwork Licensing And Attribution

Universal LPC artwork has per-asset licensing and attribution requirements. Preserve and distribute this repository's [`artwork_credits/CREDITS.csv`](artwork_credits/CREDITS.csv), review [`artwork_credits/ARTWORK_LICENSING.md`](artwork_credits/ARTWORK_LICENSING.md), and confirm that every selected asset's license is compatible with your distribution platform. The attribution folder contains `.gdignore` so Godot does not misinterpret the credits CSV as localization data.

## Documentation

- [`docs/contract.md`](docs/contract.md) - runtime, metadata, asset, and integration contract
- [`docs/feature.md`](docs/feature.md) - architecture, generation workflow, and validation
- [`docs/authoring.md`](docs/authoring.md) - appearance selection, asset generation, validation, and attribution workflow
