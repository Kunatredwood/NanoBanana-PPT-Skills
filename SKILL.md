# PPT Generator Pro - Claude Code Skill

## 📋 Metadata

- **Skill Name**: ppt-generator-pro
- **Version**: 2.0.0
- **Description**: AI-driven tool for generating high-quality PPT images and video presentations with smart transitions and an interactive player
- **Author**: 歸藏
- **Tags**: ppt, presentation, video, ai, nano-banana, kling-ai, image-generation

## ✨ Features

### Core Features
- 🤖 **Intelligent Document Analysis** — auto-extracts key points and plans PPT content structure
- 🎨 **Multi-Style Support** — 2 built-in professional styles: gradient glassmorphism and vector illustration
- 🖼️ **High-Quality Images** — uses Nano Banana Pro to generate 16:9 HD PPT slides
- 🎬 **AI Transition Videos** — Kling AI generates smooth page-to-page animations
- 🎮 **Interactive Player** — mixed video + image playback with keyboard navigation
- 🎥 **Full Video Export** — FFmpeg composes a complete PPT video with all transitions

### New Features (v2.0)
- 🔄 **Cover Loop Preview** — auto-generates an eye-catching looping animation
- 🎞️ **Smart Transitions** — auto-generates transition videos between slides
- 🔧 **Parameter Normalization** — auto-normalizes all video resolutions and frame rates

## 📦 System Requirements

### Environment Variables

**Required:**
- `GEMINI_API_KEY`: Google AI API key (for generating PPT images)

**Optional (for video features):**
- `KLING_ACCESS_KEY`: Kling AI Access Key
- `KLING_SECRET_KEY`: Kling AI Secret Key

### Python Dependencies

```bash
pip install google-genai pillow python-dotenv
```

### Video Feature Dependencies

```bash
# macOS
brew install ffmpeg

# Ubuntu/Debian
sudo apt-get install ffmpeg
```

## 🚀 Usage

### Invoking in Claude Code

```bash
/ppt-generator-pro
```

Or tell Claude directly:

```
I want to generate a 5-page PPT from the following document using the gradient glass style.

[Document content...]
```

## 📝 Skill Execution Workflow

### Phase 1: Collect User Input

#### 1.1 Get Document Content

**Option A: Document path**
```
User: Generate a PPT from my-document.md
→ Use the Read tool to read the file content
```

**Option B: Direct text**
```
User: I want to generate a PPT about AI Product Design
Main content:
1. Current state analysis
2. Design principles
3. Case studies
```

**Option C: Proactively ask**
```
If the user hasn't provided content, ask:
"Please provide a document path or paste the document content directly"
```

#### 1.2 Choose a Style

Scan the `styles/` directory and list available styles:

```python
# Auto-detect style files
styles = ['gradient-glass.md', 'vector-illustration.md']
```

**If multiple styles are available, use AskUserQuestion:**

```markdown
Question: Please choose a PPT style
Options:
- Gradient Glassmorphism Card Style (tech feel, business presentations)
- Vector Illustration Style (warm, education and training)
```

#### 1.3 Choose Slide Count

Use AskUserQuestion to ask:

```markdown
Question: How many slides would you like?
Options:
- 5 slides (5-minute presentation)
- 5–10 slides (10–15-minute presentation)
- 10–15 slides (20–30-minute presentation)
- 20–25 slides (45–60-minute presentation)
```

#### 1.4 Choose Resolution

```markdown
Question: Choose image resolution
Options:
- 2K (2752x1536) — recommended, fast generation
- 4K (5504x3072) — high quality, suitable for printing
```

#### 1.5 Generate Videos? (optional)

If Kling AI keys are configured, ask:

```markdown
Question: Would you like to generate transition videos?
Options:
- Images only (fast)
- Images + transition videos (full experience)
```

### Phase 2: Document Analysis and Content Planning

#### 2.1 Content Planning Strategy

Based on the slide count, intelligently plan the content for each slide:

**5-slide version:**
1. Cover: title + core theme
2. Point 1: first key insight
3. Point 2: second key insight
4. Point 3: third key insight
5. Summary: core conclusions or action recommendations

**5–10-slide version:**
1. Cover
2–3. Introduction/background
4–7. Core content (3–4 key insights)
8–9. Cases or data support
10. Summary and action recommendations

**10–15-slide version:**
1. Cover
2–3. Introduction/table of contents
4–6. Chapter 1 (3 slides)
7–9. Chapter 2 (3 slides)
10–12. Chapter 3/case studies
13–14. Data visualization
15. Summary and next steps

**20–25-slide version:**
1. Cover
2. Table of contents
3–4. Introduction and background
5–8. Part 1 (4 slides)
9–12. Part 2 (4 slides)
13–16. Part 3 (4 slides)
17–19. Case studies
20–22. Data analysis and insights
23–24. Key findings and recommendations
25. Summary and acknowledgements

#### 2.2 Generate slides_plan.json

Create the JSON file:

```json
{
  "title": "Document Title",
  "total_slides": 5,
  "slides": [
    {
      "slide_number": 1,
      "page_type": "cover",
      "content": "Title: AI Product Design Guide\nSubtitle: Building User-Centered Intelligent Experiences"
    },
    {
      "slide_number": 2,
      "page_type": "content",
      "content": "Core Principles\n- Simple and intuitive\n- Fast response\n- Transparent and controllable"
    },
    {
      "slide_number": 3,
      "page_type": "content",
      "content": "Design Process\n1. User research\n2. Prototype design\n3. Test and iterate"
    },
    {
      "slide_number": 4,
      "page_type": "data",
      "content": "User Satisfaction\nBefore: 65%\nAfter: 92%\nImprovement: +27%"
    },
    {
      "slide_number": 5,
      "page_type": "content",
      "content": "Summary\n- User-centered\n- Continuous optimization\n- Data-driven decisions"
    }
  ]
}
```

**Important:** Save this file to:
- Standalone use: `./slides_plan.json`
- Skill mode: `.claude/skills/ppt-generator/slides_plan.json`

### Phase 3: Generate PPT Images

#### 3.1 Determine Working Directory

**Standalone mode:**
```bash
cd /path/to/ppt-generator
```

**Skill mode:**
```bash
cd ~/.claude/skills/ppt-generator
```

#### 3.2 Run the Generation Command

```bash
python generate_ppt.py \
  --plan slides_plan.json \
  --style styles/gradient-glass.md \
  --resolution 2K
```

**Or use uv run (recommended):**
```bash
uv run python generate_ppt.py \
  --plan slides_plan.json \
  --style styles/gradient-glass.md \
  --resolution 2K
```

**Parameter descriptions:**
- `--plan`: path to the slides plan JSON file
- `--style`: path to the style file
- `--resolution`: resolution (2K or 4K)
- `--template`: HTML template path (optional)

#### 3.3 Monitor Generation Progress

The script outputs progress information:

```
✅ Loaded environment variables: /path/to/.env
📊 Starting PPT image generation...
   Total slides: 5
   Resolution: 2K (2752x1536)
   Style: Gradient Glassmorphism Card Style

🎨 Generating slide 1 (Cover)...
   Prompt generated
   Calling Nano Banana Pro API...
   ✅ Slide 1 generated successfully (32.5 seconds)

🎨 Generating slide 2 (Content)...
   ✅ Slide 2 generated successfully (28.3 seconds)

...

✅ All slides generated!
📁 Output directory: outputs/20260112_143022/
```

### Phase 4: Generate Transition Prompts (required for video mode)

**This is the core advantage of the Skill**: I (Claude Code) will analyze the generated PPT images and create precise video prompts for each transition.

#### 4.1 Read and Analyze PPT Images

I will read all the generated images:

```python
# Auto-read all images in the output directory
slides = ['slide-01.png', 'slide-02.png', ...]
```

#### 4.2 Analyze Image Differences and Generate Prompts

For each pair of adjacent images, I will:
1. **Visual analysis**: understand the layout, elements, and color differences between the two images
2. **Generate preview prompt**: describe a loopable subtle-motion animation for the cover
3. **Generate transition prompt**: describe in detail how to transition from the start frame to the end frame

**Example output:**
```json
{
  "preview": {
    "slide_path": "outputs/.../slide-01.png",
    "prompt": "The frame holds the cover's static composition; the central 3D glass ring slowly rotates..."
  },
  "transitions": [
    {
      "from_slide": 1,
      "to_slide": 2,
      "prompt": "The camera starts on the cover; the glass ring gradually deconstructs, splitting into transparent fragments..."
    }
  ]
}
```

#### 4.3 Save the Prompt File

I will save the generated prompts to:
```
outputs/TIMESTAMP/transition_prompts.json
```

**Key advantages:**
- ✅ No separate Claude API key required
- ✅ Prompts are tailored to the actual image content
- ✅ Considers text stability to avoid the video model blurring text
- ✅ Consistent with the visual language of the gradient glassmorphism style

### Phase 5: Generate Transition Videos (optional)

If the user chooses to generate videos, use the prompt file from Phase 4:

```bash
python generate_ppt_video.py \
  --slides-dir outputs/20260112_143022/images \
  --output-dir outputs/20260112_143022_video \
  --prompts-file outputs/20260112_143022/transition_prompts.json
```

**Generated content:**
- Cover loop preview video (`preview.mp4`)
- Slide transition videos (`transition_01_to_02.mp4`, etc.)
- Interactive video player (`video_index.html`)
- Full video (`full_ppt_video.mp4`)

### Phase 6: Return Results

#### 6.1 Image-Only Mode

```
✅ PPT generated successfully!

📁 Output directory: outputs/20260112_143022/
🖼️ PPT images: outputs/20260112_143022/images/
🎬 Player page: outputs/20260112_143022/index.html

Open the player:
open outputs/20260112_143022/index.html

Player shortcuts:
- ← → keys: navigate slides
- ↑ Home: back to first slide
- ↓ End: jump to last slide
- Space: pause/resume auto-play
- ESC: toggle fullscreen
- H: show/hide controls
```

#### 5.2 Video Mode

```
✅ PPT video generated successfully!

📁 Output directory: outputs/20260112_143022_video/
🖼️ PPT images: outputs/20260112_143022/images/
🎬 Transition videos: outputs/20260112_143022_video/videos/
🎮 Interactive player: outputs/20260112_143022_video/video_index.html
🎥 Full video: outputs/20260112_143022_video/full_ppt_video.mp4

Open the interactive player:
open outputs/20260112_143022_video/video_index.html

Playback logic:
1. First slide: plays cover loop preview video
2. Press → key → plays transition video → shows target slide image (2 seconds)
3. Press → again → plays next transition → shows next slide
4. And so on...

Video player shortcuts:
- ← → keys: previous/next slide (with transitions)
- Space: play/pause current video
- ESC: toggle fullscreen
- H: show/hide controls
```

## 🔧 Environment Variable Configuration

### .env File Location

The Skill searches for a `.env` file in the following order:

1. **Script directory** — `./ppt-generator/.env`
2. **Search up to project root** — until a directory containing `.git` or `.env` is found
3. **Claude Skill standard location** — `~/.claude/skills/ppt-generator/.env`
4. **System environment variables** — if none of the above are found

### .env File Example

```bash
# Google AI API key (required)
GEMINI_API_KEY=your_gemini_api_key_here

# Kling AI API keys (optional, for video features)
KLING_ACCESS_KEY=your_kling_access_key_here
KLING_SECRET_KEY=your_kling_secret_key_here
```

## ⚠️ Error Handling

### Common Errors and Solutions

**1. API key not set**
```
Error: ⚠️ No .env file found, trying system environment variables
      GEMINI_API_KEY environment variable is not set

Solution:
1. Create a .env file
2. Add GEMINI_API_KEY=your_key_here
```

**2. Missing Python dependency**
```
Error: ModuleNotFoundError: No module named 'google.genai'

Solution: pip install google-genai pillow python-dotenv
```

**3. FFmpeg not installed**
```
Error: ❌ FFmpeg is not available!

Solution: brew install ffmpeg  # macOS
          sudo apt-get install ffmpeg  # Ubuntu
```

**4. API call failed**
```
Error: API call timed out or failed

Solution:
1. Check your network connection
2. Confirm the API key is valid
3. Try again later
```

**5. Video generation failed**
```
Error: Kling AI keys not configured

Solution:
1. If you only need images, skip the video generation step
2. If you need videos, configure KLING_ACCESS_KEY and KLING_SECRET_KEY
```

## 🎨 Style System

### Built-in Styles

#### 1. Gradient Glassmorphism Card Style (`gradient-glass.md`)

**Visual characteristics:**
- Apple Keynote minimalism
- Glassmorphism effect
- Neon purple / electric blue / coral orange gradients
- 3D glass objects + cinematic lighting

**Best for:**
- Tech product launches
- Business presentations
- Data reports
- Corporate branding

#### 2. Vector Illustration Style (`vector-illustration.md`)

**Visual characteristics:**
- Flat vector design
- Uniform black outlines
- Retro muted color palette
- Geometric simplification

**Best for:**
- Education and training
- Creative proposals
- Children's content
- Warm brand storytelling

### Add a Custom Style

1. Create a new `.md` file in the `styles/` directory
2. Write it following the existing style format
3. The Skill will auto-detect it and offer it as an option

## 📊 Technical Details

### API Configuration

**Nano Banana Pro (image generation):**
- Model: `gemini-3-pro-image-preview`
- Aspect ratio: `16:9`
- Response mode: `IMAGE`
- Resolution: 2K (2752x1536) or 4K (5504x3072)

**Kling AI (video generation):**
- Mode: professional
- Duration: 5 seconds
- Resolution: 1920x1080
- Frame rate: 24fps

**FFmpeg (video composition):**
- Encoding: H.264
- Quality: CRF 23
- Frame rate: 24fps (normalized)
- Resolution: 1920x1080 (normalized)

### Performance Metrics

**Generation speed:**
- PPT images: ~30s/slide (2K) | ~60s/slide (4K)
- Transition videos: ~30–60s/segment
- Video composition: ~5–10s

**File size:**
- PPT images: ~2.5MB/slide (2K) | ~8MB/slide (4K)
- Transition videos: ~3–5MB/segment (1080p, 5 seconds)
- Full video: ~12–20MB (5-slide PPT + transitions)

## 📁 File Organization

### Output Directory Structure

**Image-only mode:**
```
outputs/20260112_143022/
├── images/
│   ├── slide-01.png
│   ├── slide-02.png
│   └── ...
├── index.html          # Image player
└── prompts.json        # Prompt log
```

**Video mode:**
```
outputs/20260112_143022_video/
├── videos/
│   ├── preview.mp4              # Cover loop preview
│   ├── transition_01_to_02.mp4
│   ├── transition_02_to_03.mp4
│   └── ...
├── video_index.html             # Interactive player
└── full_ppt_video.mp4           # Full video
```

## 🎯 Best Practices

1. **Document quality**: the clearer and more structured the input document, the higher the PPT quality
2. **Slide count**: choose an appropriate count based on document length and presentation context
3. **Resolution**: 2K recommended for everyday use; 4K for important showcases
4. **Video features**: try image-only mode first, then explore video features once you're familiar
5. **Prompt adjustment**: check `prompts.json` to understand the generation logic; you can manually adjust and regenerate

## 📝 Usage Examples

### Example 1: Quick Generation

**User input:**
```
I need a 5-page PPT from this meeting minutes using the vector illustration style.

Meeting theme: Q1 Product Roadmap Planning
Participants: Product team

Discussion topics:
1. User feedback summary
2. New feature priorities
3. Technical feasibility assessment
4. Q1 milestones
5. Next action items
```

**Skill execution:**
1. Collect input (content already provided)
2. Confirm style (vector illustration)
3. Confirm slide count (5 slides)
4. Confirm resolution (ask user)
5. Generate slides_plan.json
6. Run generation command
7. Return results

### Example 2: Full Workflow

**User input:**
```
Based on the AI-Product-Design.md document, generate a 15-page PPT using the gradient glass style with transition videos.
```

**Skill execution:**
1. Read document content
2. Confirm style (gradient glassmorphism)
3. Confirm slide count (15 slides)
4. Confirm resolution (ask user)
5. Confirm video generation (yes)
6. Analyze document, plan 15-slide content
7. Generate slides_plan.json
8. Generate PPT images
9. Generate transition videos
10. Compose full video
11. Return all results

## 🔄 Changelog

### v2.0.0 (2026-01-12)

- 🎬 **New video features**
  - Kling AI transition video generation
  - Interactive video player
  - FFmpeg full video composition
  - Cover loop preview video
- 🔧 **Video composition improvements**
  - Auto-normalize resolution and frame rate
  - Fix video concatenation compatibility issues
  - Static slide display time changed to 2 seconds
- 🔑 **Improved environment variable handling**
  - Intelligent .env file search
  - Support for multiple deployment modes
  - Auto search up to project root directory
- 📚 **Documentation improvements**
  - Renamed to SKILL.md (following official naming convention)
  - Updated all paths and commands
  - Added video feature usage guide

### v1.0.0 (2026-01-09)

- ✨ Initial release
- 🎨 2 built-in professional styles
- 🖼️ 2K/4K resolution support
- 🎬 HTML5 image player
- 📊 Intelligent document analysis

## 📄 License

MIT License

## 📞 Support

- Project architecture: see `ARCHITECTURE.md`
- API management: see `API_MANAGEMENT.md`
- Environment configuration: see `ENV_SETUP.md`
- Security notes: see `SECURITY.md`
- Complete documentation: see `README.md`
