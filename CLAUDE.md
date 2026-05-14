# agent-sprite-forge

A collection of image-generation skills for creating 2D game assets (sprites, maps, props) using OpenAI or Azure gpt-image-2.

## Project structure

```
scripts/
  image_gen.py          — CLI for image generation (generate, edit, generate-batch)
  remove_chroma_key.py  — Remove solid-magenta backgrounds → transparent PNG
skills/
  imagegen/             — General-purpose image generation skill
  generate2dsprite/     — 2D sprite and animation sheet generation
  generate2dmap/        — 2D map, prop pack, and scene generation
image-gen.config.example.yaml — Configuration template
requirements.txt        — Python dependencies
```

## Configuration

Copy `image-gen.config.example.yaml` to `image-gen.config.yaml` and fill in credentials. The config supports environment variable expansion (`${VAR_NAME}`).

Provider options: `openai` (direct API) or `azure` (Azure OpenAI endpoint).

Config search order: `--config` CLI flag > `IMAGE_GEN_CONFIG` env var > `./image-gen.config.yaml` > skill root directory.

## Quick start

```bash
pip install -r requirements.txt
cp image-gen.config.example.yaml image-gen.config.yaml
# Edit image-gen.config.yaml with your credentials

python scripts/image_gen.py generate --prompt "a pixel art sword" --out sword.png
python scripts/image_gen.py edit --image sword.png --prompt "add a glow effect" --out sword-glow.png
python scripts/remove_chroma_key.py --input raw.png --output clean.png
```

## Running tests

```bash
python scripts/image_gen.py --help
python scripts/image_gen.py generate --dry-run --prompt "test" --out /tmp/test.png
```
