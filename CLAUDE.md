# agent-sprite-forge

A collection of image-generation skills for creating 2D game assets (sprites, maps, props) using OpenAI or Azure gpt-image-2.

## Project structure

```
skills/
  imagegen/             — General-purpose image generation skill
    scripts/
      image_gen.py      — CLI for image generation (generate, edit, generate-batch)
      remove_chroma_key.py — Remove solid-magenta backgrounds → transparent PNG
  generate2dsprite/     — 2D sprite and animation sheet generation
  generate2dmap/        — 2D map, prop pack, and scene generation
image-gen.config.example.yaml — Configuration template
requirements.txt        — Python dependencies
```

## Configuration

Set credentials via environment variables or a `.env` file in `skills/imagegen/scripts/`:

```bash
cp skills/imagegen/scripts/.env.example skills/imagegen/scripts/.env
# Edit .env with your credentials
```

Provider options: `openai` (direct API) or `azure` (Azure OpenAI endpoint) — set `IMAGE_GEN_PROVIDER`.

Priority: environment variables > `.env` file values.

## Quick start

```bash
pip install -r requirements.txt
export OPENAI_API_KEY=sk-your-key  # or use .env file

python skills/imagegen/scripts/image_gen.py generate --prompt "a pixel art sword" --out sword.png
python skills/imagegen/scripts/image_gen.py edit --image sword.png --prompt "add a glow effect" --out sword-glow.png
python skills/imagegen/scripts/remove_chroma_key.py --input raw.png --output clean.png
```

## Running tests

```bash
python skills/imagegen/scripts/image_gen.py --help
python skills/imagegen/scripts/image_gen.py generate --dry-run --prompt "test" --out /tmp/test.png
```
