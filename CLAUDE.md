# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

NanoBanana PPT Skills is an AI-driven presentation generation system that produces high-quality slide images and animated video presentations. It integrates three AI services (Google Gemini for images, Kling AI for video transitions, Claude for prompt analysis) and FFmpeg for video composition.

## Running the Scripts

There is no build system. Scripts are run directly with Python 3.8+.

```bash
# Install dependencies
pip install google-genai pillow python-dotenv requests PyJWT anthropic

# Generate PPT images from a slide plan
python3 generate_ppt.py \
  --plan slides_plan.json \
  --style styles/gradient-glass.md \
  --resolution 2K

# Generate video from existing PPT images (requires FFmpeg + Kling API keys)
python3 generate_ppt_video.py \
  --slides-dir outputs/TIMESTAMP/images \
  --output-dir outputs/TIMESTAMP_video \
  --prompts-file outputs/TIMESTAMP/transition_prompts.json

# Generate transition prompts from images (uses Claude API)
python3 transition_prompt_generator.py \
  --slides-dir outputs/TIMESTAMP/images \
  --output outputs/TIMESTAMP/transition_prompts.json
```

There is no test suite. Validation is done by running scripts and inspecting outputs.

## Required Configuration

Copy `.env.example` to `.env` and populate:

```bash
GEMINI_API_KEY=...       # Required: Google Gemini for slide image generation
KLING_ACCESS_KEY=...     # Optional: Kling AI for video transitions
KLING_SECRET_KEY=...     # Optional: Kling AI for video transitions
```

The `.env` file is searched in: script directory → parent directories (up to `.git`) → `~/.claude/skills/ppt-generator/` → system environment.

## Architecture

The pipeline has distinct phases, each handled by a separate module:

1. **Image generation** (`generate_ppt.py`) — Reads a `slides_plan.json`, loads a style template from `styles/`, calls the Google Gemini API (`gemini-3-pro-image-preview`), and outputs `slide-01.png` through `slide-N.png` into `outputs/TIMESTAMP/images/`.

2. **Transition prompt generation** (`transition_prompt_generator.py` or `simple_transition_prompt_generator.py`) — Reads slide images, uses Claude (`claude-sonnet-4-5-20250929`) to analyze visual transitions, and outputs `transition_prompts.json`.

3. **Video generation orchestrator** (`generate_ppt_video.py`) — Coordinates the full video pipeline using `concurrent.futures` (default 3 workers). Delegates to:
   - `video_materials.py` — Generates preview loop and per-transition video clips via Kling AI
   - `kling_api.py` — Kling AI API wrapper with JWT authentication and polling

4. **Video composition** (`video_composer.py`) — FFmpeg subprocess wrapper. Normalizes all clips to 1920×1080 at 24fps and concatenates into `full_ppt_video.mp4` (H.264, 300s timeout).

5. **HTML players** (`templates/viewer.html`, `templates/video_viewer.html`) — Self-contained browser-based players generated into the output directory. No server required.

## Style System

Styles live in `styles/` as Markdown files. Each style file contains detailed prompt instructions passed directly to the Gemini API. Two built-in styles:
- `gradient-glass.md` — Glassmorphism with neon gradients
- `vector-illustration.md` — Flat design with retro colors

To add a new style, create a new `.md` file in `styles/` following the same structure.

## Key Data Formats

**`slides_plan.json`** — Input to `generate_ppt.py`. Defines slide content structure.

**`transition_prompts.json`** — Input to `generate_ppt_video.py`. Array of prompt objects describing how each slide transitions to the next.

**Output layout:**
```
outputs/
  TIMESTAMP/
    images/        # slide-01.png, slide-02.png, ...
    viewer.html    # Image player
    transition_prompts.json
  TIMESTAMP_video/
    preview.mp4
    transition_XX_to_YY.mp4
    full_ppt_video.mp4
    video_viewer.html
```

## Claude Code Skill Mode

This project can be installed as a Claude Code skill at `~/.claude/skills/ppt-generator/`. In skill mode, Claude orchestrates the entire pipeline conversationally. See `SKILL.md` for the 6-phase skill workflow and command reference.
