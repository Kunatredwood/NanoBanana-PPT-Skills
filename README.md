# NanoBanana PPT Skills

> A powerful AI-driven tool for generating high-quality PPT images and animated video presentations with smart transitions and an interactive player

<div align="center">

![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Python](https://img.shields.io/badge/python-3.8+-green.svg)

**Creator**: [歸藏](https://github.com/op7418)

[Demo](#-demo) • [Features](#-features) • [One-Click Install](#-one-click-install) • [Use as a Skill](#-use-as-a-claude-code-skill) • [Usage Guide](#-usage-guide) • [Video Features](#-video-features) • [Architecture](ARCHITECTURE.md) • [FAQ](#-faq)

</div>

---

## 🎬 Demo

<div align="center">

https://github.com/user-attachments/assets/b394de21-2848-489a-8d33-a8e262e60f60

*AI automatically generates a PPT and adds smooth transition animations — from document analysis to video composition in one click*

</div>

---

## 📖 Introduction

NanoBanana PPT Skills is a powerful AI-driven PPT generation tool that can:

- 📄 **Intelligently analyze documents**, automatically extract key points, and plan PPT structure
- 🎨 **Generate high-quality images** using Google Nano Banana Pro (Gemini 3 Pro Image Preview)
- 🎬 **Automatically generate transition videos** using Kling AI to create smooth page-to-page animations
- 🎮 **Interactive video player** with keyboard control, loop preview, and smart transitions
- 🎥 **Full video export** — one-click composition of a complete PPT video with all transitions

### 🎨 Visual Styles

**Gradient Glassmorphism Card Style**
- Premium tech feel, Apple Keynote minimalism
- 3D glass objects + neon gradients
- Cinematic lighting effects
- Best for: tech products, business presentations, data reports

**Vector Illustration Style**
- Warm flat design, retro color palette
- Black outlines + geometric simplification
- Toy-model-like charm
- Best for: education, creative proposals, brand storytelling

---

## ✨ Features

### 🎯 Core Capabilities

- 🤖 **Intelligent Document Analysis** — auto-extracts key points and plans PPT content structure
- 🎨 **Multi-Style Support** — 2 built-in professional styles, infinitely extensible
- 🖼️ **High-Quality Images** — 16:9 aspect ratio, 2K/4K resolution options
- 🎬 **AI Transition Videos** — Kling AI generates smooth page-to-page animations
- 🎮 **Interactive Player** — mixed video + image playback with keyboard navigation
- 🎥 **Full Video Export** — FFmpeg composes a complete PPT video with all transitions
- 📊 **Smart Layouts** — auto-detects cover pages, content pages, and data pages
- ⚡ **Fast Generation** — 2K takes about 30 seconds per slide

### 🆕 Video Features (v2.0)

- 🎬 **Cover Loop Preview** — auto-generates an eye-catching looping animation
- 🎞️ **Smart Transitions** — auto-generates transition videos between slides
- 🎮 **Interactive Playback** — pressing a key plays the transition video, then shows the static slide
- 🎥 **Full Video Export** — composes a complete video with all transitions and static slides
- 🔧 **Parameter Normalization** — auto-normalizes all video resolutions and frame rates for smooth playback

### 🛠️ Technical Highlights

- ✅ Google Nano Banana Pro (Gemini 3 Pro Image Preview) image generation
- ✅ Kling AI API integration (video generation, digital human, subject library)
- ✅ FFmpeg video composition and parameter normalization
- ✅ Complete prompt engineering and style management system
- ✅ Secure .env environment variable management
- ✅ Modular design, easy to extend

---

## 🚀 One-Click Install

### Method 1: Claude Code Auto-Install (recommended)

**Just copy the following prompt and send it to Claude Code — it will complete the entire installation automatically!**

```
Please help me install NanoBanana PPT Skills:

1. Clone the project and enter the directory:
   git clone https://github.com/op7418/NanoBanana-PPT-Skills.git
   cd NanoBanana-PPT-Skills

2. Create a Python virtual environment:
   python3 -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate

3. Install dependencies:
   pip install google-genai pillow python-dotenv

4. Configure the API key — create a .env file:
   cp .env.example .env

5. Edit the .env file and fill in my API keys:

   GEMINI_API_KEY=YOUR_GEMINI_API_KEY
   KLING_ACCESS_KEY=YOUR_KLING_ACCESS_KEY
   KLING_SECRET_KEY=YOUR_KLING_SECRET_KEY

   Notes:
   - GEMINI_API_KEY: Google AI API key (required, for generating PPT images)
   - KLING_ACCESS_KEY and KLING_SECRET_KEY: Kling AI keys (optional, for generating transition videos)

6. Verify the installation:
   python3 generate_ppt.py --help

When done, tell me the installation result and how to use it.

My API keys:
- GEMINI_API_KEY: YOUR_GEMINI_API_KEY_HERE
- KLING_ACCESS_KEY: YOUR_KLING_ACCESS_KEY_HERE (optional)
- KLING_SECRET_KEY: YOUR_KLING_SECRET_KEY_HERE (optional)
```

**Instructions:**
1. First, get your API keys:
   - **Required**: [Google AI API Key](https://aistudio.google.com/apikey)
   - **Optional**: [Kling AI API Key](https://klingai.com) (for video transition feature)
2. Copy the prompt above
3. Replace `YOUR_GEMINI_API_KEY_HERE` etc. with your actual API keys
4. Send it to Claude Code
5. Claude Code will execute all installation steps and report the result

### Method 2: Manual Installation

If you prefer to install manually, follow these steps:

#### 1. Clone the Project

```bash
git clone https://github.com/op7418/NanoBanana-PPT-Skills.git
cd NanoBanana-PPT-Skills
```

#### 2. Create a Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

#### 3. Install Dependencies

```bash
pip install google-genai pillow
```

For video features, you also need FFmpeg:

```bash
# macOS
brew install ffmpeg

# Ubuntu/Debian
sudo apt-get install ffmpeg

# Windows
# Download FFmpeg and add it to your system PATH
```

#### 4. Configure API Keys

**Recommended: .env file (built-in support)**

```bash
# Copy the example file
cp .env.example .env

# Edit the .env file
nano .env  # or your preferred editor
```

Fill in your API keys in `.env`:

```bash
# Google AI API key (required)
GEMINI_API_KEY=your_gemini_api_key_here

# Kling AI API keys (optional, for video transition feature)
KLING_ACCESS_KEY=your_kling_access_key_here
KLING_SECRET_KEY=your_kling_secret_key_here
```

**Alternative: System environment variables**

```bash
# zsh (macOS default)
echo 'export GEMINI_API_KEY="your-api-key-here"' >> ~/.zshrc
source ~/.zshrc

# bash
echo 'export GEMINI_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

#### 5. Verify the Installation

```bash
python3 generate_ppt.py --help
```

A help message confirms the installation was successful.

---

## 🎯 Use as a Claude Code Skill

NanoBanana PPT Skills fully supports the Claude Code Skill standard and can be invoked directly through Claude Code.

### Quick Install as a Skill

**Method 1: Claude Code Auto-Install as Skill (simplest)**

**Just copy the following prompt and send it to Claude Code — it will complete the Skill installation automatically!**

```
Please help me install NanoBanana PPT Skills as a Claude Code Skill:

1. Create the Skill directory:
   mkdir -p ~/.claude/skills/ppt-generator

2. Clone the project into the Skill directory:
   git clone https://github.com/op7418/NanoBanana-PPT-Skills.git ~/.claude/skills/ppt-generator

3. Enter the directory and install dependencies:
   cd ~/.claude/skills/ppt-generator
   python3 -m venv venv
   source venv/bin/activate
   pip install google-genai pillow python-dotenv

4. Configure API keys:
   cp .env.example .env

   Then edit the .env file and fill in my API keys:
   GEMINI_API_KEY=YOUR_GEMINI_API_KEY
   KLING_ACCESS_KEY=YOUR_KLING_ACCESS_KEY
   KLING_SECRET_KEY=YOUR_KLING_SECRET_KEY

5. Verify the installation:
   python3 generate_ppt.py --help

When done, tell me how to use this Skill in Claude Code.

My API keys:
- GEMINI_API_KEY: YOUR_GEMINI_API_KEY_HERE
- KLING_ACCESS_KEY: YOUR_KLING_ACCESS_KEY_HERE (optional)
- KLING_SECRET_KEY: YOUR_KLING_SECRET_KEY_HERE (optional)
```

**Method 2: Use the install script**

```bash
# Clone the project
git clone https://github.com/op7418/NanoBanana-PPT-Skills.git
cd NanoBanana-PPT-Skills

# Run the install script
bash install_as_skill.sh
```

The install script will automatically:
1. Create the `~/.claude/skills/ppt-generator/` directory
2. Copy all necessary files
3. Install Python dependencies
4. Guide you through API key configuration

**Method 3: Manual installation**

```bash
# 1. Create the Skill directory
mkdir -p ~/.claude/skills/ppt-generator

# 2. Clone the project into the Skill directory
git clone https://github.com/op7418/NanoBanana-PPT-Skills.git ~/.claude/skills/ppt-generator

# 3. Install dependencies
cd ~/.claude/skills/ppt-generator
pip install google-genai pillow python-dotenv

# 4. Configure API keys
cp .env.example .env
nano .env  # fill in your API keys
```

### Environment Variable Configuration

The Skill searches for a `.env` file in the following priority order:

1. **Script directory** — `~/.claude/skills/ppt-generator/.env`
2. **Search up to project root** — until a directory containing `.git` or `.env` is found
3. **User home directory** — `~/.env`
4. **System environment variables** — as a last resort

**Recommended configuration:**

```bash
# Create a .env file in the Skill directory
cat > ~/.claude/skills/ppt-generator/.env << EOF
# Google AI API key (required)
GEMINI_API_KEY=your_gemini_api_key_here

# Kling AI API keys (optional, for video features)
KLING_ACCESS_KEY=your_kling_access_key_here
KLING_SECRET_KEY=your_kling_secret_key_here
EOF
```

### Using in Claude Code

After installation, invoke it directly in Claude Code:

```bash
/ppt-generator-pro
```

Or tell Claude:

```
I want to generate a 5-page PPT from the following document using the gradient glass style.

[Document content...]
```

Claude will automatically:
1. Analyze the document
2. Ask about style, slide count, resolution, etc.
3. Generate `slides_plan.json`
4. Call `generate_ppt.py` to generate images
5. (Optionally) generate transition videos
6. Return the result paths

### Skill Mode vs. Standalone Mode

| Feature | Skill Mode | Standalone Mode |
|---------|-----------|-----------------|
| Install location | `~/.claude/skills/ppt-generator/` | Any directory |
| How to invoke | `/ppt-generator-pro` or natural language | Run Python scripts manually |
| Document analysis | Claude analyzes automatically | Must prepare JSON manually |
| User experience | Conversational, options asked automatically | Command-line arguments |
| .env location | Skill dir or project root | Script directory |
| Best for | Daily use, quick generation | Batch generation, automation |

### Detailed Documentation

See [SKILL.md](SKILL.md) for complete Skill documentation, including:
- Full execution workflow
- User input collection strategy
- Content planning methods
- Error handling guide
- Best practices

---

## 💡 Usage Guide

### Basic: Generate PPT Images

#### 1. Prepare a Content Plan File

Create `my_slides_plan.json`:

```json
{
  "title": "AI Product Design Guide",
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

#### 2. Generate PPT Images

```bash
python3 generate_ppt.py \
  --plan my_slides_plan.json \
  --style styles/gradient-glass.md \
  --resolution 2K
```

#### 3. View the Result

```bash
# Open the image player in a browser
open outputs/TIMESTAMP/index.html
```

### Advanced: Generate a PPT with Transition Videos

#### 1. Generate PPT Images

```bash
python3 generate_ppt.py \
  --plan my_slides_plan.json \
  --style styles/gradient-glass.md \
  --resolution 2K
```

#### 2. Generate Transition Prompts Using Claude Code (required)

In Claude Code:

```
I just generated 5 PPT images in the outputs/TIMESTAMP/images directory.
Please analyze these images, generate video prompts for each slide transition,
and save them as outputs/TIMESTAMP/transition_prompts.json
```

Claude Code will:
1. Read all PPT images
2. Analyze visual differences between adjacent slides
3. Generate precise transition descriptions
4. Save them as a JSON file

#### 3. Generate Transition Videos

```bash
python3 generate_ppt_video.py \
  --slides-dir outputs/TIMESTAMP/images \
  --output-dir outputs/TIMESTAMP_video \
  --prompts-file outputs/TIMESTAMP/transition_prompts.json
```

This generates:
- Cover loop preview video
- Transition videos between each pair of slides
- Interactive video player HTML
- Full video (full_ppt_video.mp4)

#### 4. Play the Interactive Video PPT

```bash
open outputs/TIMESTAMP_video/video_index.html
```

**Playback logic:**
1. First slide: plays the loop preview video
2. Press right arrow: plays transition video → shows target slide image (holds 2 seconds)
3. Press right arrow again: plays next transition → shows next slide
4. And so on...

#### 4. Export Full Video (optional)

The interactive player auto-generates a full video:

```bash
# Video file
outputs/TIMESTAMP_video/full_ppt_video.mp4
```

The full video includes:
- Cover preview (if available)
- Transition video 01→02
- Slide 2 static (2 seconds)
- Transition video 02→03
- Slide 3 static (2 seconds)
- ...

---

## 🎬 Video Features

### Transition Video Generation

Use Kling AI to auto-generate transition videos between slides:

```bash
python3 generate_ppt_video.py \
  --slides-dir outputs/20260111_160221/images \
  --output-dir outputs/20260111_video \
  --mode professional \
  --duration 5
```

**Parameters:**
- `--slides-dir`: Directory of PPT images
- `--output-dir`: Output directory
- `--mode`: Transition mode (`professional` or `creative`)
- `--duration`: Transition video duration in seconds (default 5)

### Interactive Player

The generated `video_index.html` supports:

| Feature | Shortcut | Description |
|---------|----------|-------------|
| Next slide | `→` `↓` | Plays transition video, then shows the next slide |
| Previous slide | `←` `↑` | Returns to previous slide (directly) |
| First slide | `Home` | Returns to cover loop preview |
| Last slide | `End` | Jumps to the last slide |
| Play/pause | `Space` | Pause/resume current video |
| Fullscreen | `ESC` | Toggle fullscreen |
| Hide controls | `H` | Show/hide control hints |

### Full Video Composition

Use FFmpeg to auto-compose a complete video:

```python
from video_composer import VideoComposer

composer = VideoComposer()
composer.compose_full_ppt_video(
    slides_paths=[...],
    transitions_dict={...},
    output_path='output.mp4',
    slide_duration=2,  # 2 seconds per slide
    include_preview=True,
    preview_video_path='preview.mp4',
    resolution='1920x1080',
    fps=24
)
```

**Features:**
- Auto-normalizes all video resolutions and frame rates
- Preserves aspect ratio with letterboxing
- Supports preview video loop
- High-quality H.264 encoding

---

## 🎨 Style Library

### Built-in Styles

#### 1. Gradient Glassmorphism Card Style (`gradient-glass.md`)

**Visual characteristics:**
- Apple Keynote minimalism
- Glassmorphism effect
- Neon purple / electric blue / coral orange gradients
- 3D glass objects + cinematic lighting

**Best for:**
- 🚀 Tech product launches
- 💼 Business presentations
- 📊 Data reports
- 🏢 Corporate branding

#### 2. Vector Illustration Style (`vector-illustration.md`)

**Visual characteristics:**
- Flat vector design
- Uniform black outlines
- Retro muted color palette
- Geometric simplification

**Best for:**
- 📚 Education and training
- 🎨 Creative proposals
- 👶 Children's content
- 💖 Warm brand storytelling

### Add a Custom Style

1. Create a new `.md` file in the `styles/` directory
2. Write the style definition following the template (see existing styles)
3. Use the new style directly when generating PPTs

---

## 📚 Project Structure

```
ppt-generator/
├── README.md                      # This file
├── API_MANAGEMENT.md              # API key management guide
├── ENV_SETUP.md                   # Environment variable configuration
├── SECURITY.md                    # Security best practices
├── .env.example                   # Environment variable template
├── .env                          # Actual environment variables (not committed)
├── .gitignore                    # Git ignore rules
│
├── generate_ppt.py               # PPT image generation script
├── generate_ppt_video.py         # Video generation main script
├── kling_api.py                  # Kling AI API wrapper
├── video_composer.py             # FFmpeg video composition
├── video_materials.py            # Video materials management
├── transition_prompt_generator.py # Transition prompt generator
│
├── styles/                       # Style library
│   ├── gradient-glass.md         # Gradient glassmorphism card style
│   └── vector-illustration.md    # Vector illustration style
│
├── templates/                    # HTML templates
│   ├── viewer.html              # Image player
│   └── video_viewer.html        # Video player
│
├── prompts/                      # Prompt templates
│   └── transition_base.md       # Base transition prompt template
│
└── outputs/                      # Generated results (auto-created)
    ├── TIMESTAMP/               # Image version
    │   ├── images/             # PPT images
    │   ├── index.html          # Image player
    │   └── prompts.json        # Generated prompt log
    └── TIMESTAMP_video/         # Video version
        ├── videos/             # Transition videos
        ├── video_index.html    # Video player
        └── full_ppt_video.mp4  # Full video
```

---

## 🔧 Configuration Options

### Resolution

| Resolution | Dimensions | File Size | Generation Speed | Best For |
|------------|-----------|-----------|------------------|----------|
| 2K | 2752x1536 | ~2.5MB/slide | ~30s/slide | Daily use, online sharing ✅ |
| 4K | 5504x3072 | ~8MB/slide | ~60s/slide | Print output, large screens |

### Video Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| Resolution | 1920x1080 | Normalized to 1080p, compatible with Kling videos |
| Frame rate | 24fps | Normalized frame rate for smooth concatenation |
| Static slide duration | 2s | Display time per slide |
| Transition video duration | 5s | Duration of Kling-generated transitions |

### Slide Count Guide

| Count | Presentation Length | Best For |
|-------|---------------------|----------|
| 5 | 5 minutes | Elevator pitch, quick intro |
| 5–10 | 10–15 minutes | Standard presentation, product intro |
| 10–15 | 20–30 minutes | In-depth session, training course |
| 20–25 | 45–60 minutes | Full training, workshop |

---

## ❓ FAQ

### Q: How do I get API keys?

**A:**
- **Google AI API**: Visit [Google AI Studio](https://aistudio.google.com/apikey) — log in and create one
- **Kling AI API**: Visit the [Kling AI Open Platform](https://klingai.com), register and create an app to get keys

### Q: Is the Kling AI key required?

**A:** No.
- **Generating PPT images only**: you only need `GEMINI_API_KEY`
- **Generating transition videos**: you need `KLING_ACCESS_KEY` and `KLING_SECRET_KEY`

### Q: What if video composition fails?

**A:** Check the following:
1. Is FFmpeg installed? (`ffmpeg -version`)
2. Do the video files exist and are they complete?
3. Is there enough disk space?
4. Check the detailed error message

### Q: How do I change the static slide display time?

**A:** Modify the `slide_duration` parameter in `video_composer.py` (default is 2 seconds)

### Q: Why is transition video generation slow?

**A:** Kling AI takes time to generate videos (typically 30–60 seconds per segment). You can:
- Reduce the number of transitions
- Use a shorter transition duration
- Generate in batches

### Q: Can I export to PDF?

**A:** Yes.
1. Open `index.html` in a browser
2. Press `Cmd+P` (Mac) or `Ctrl+P` (Windows)
3. Select "Save as PDF"

### Q: Can the generated content be used commercially?

**A:** Please check the relevant terms of service:
- [Google AI Terms of Use](https://ai.google.dev/terms)
- [Kling AI Terms of Use](https://klingai.com/terms)

In general, you own usage rights to the generated content.

---

## 🛡️ Security Notes

### API Key Security

This project uses a `.env` file to manage API keys securely:

- ✅ `.env` is in `.gitignore` and will not be committed to Git
- ✅ No hardcoded keys in the code
- ✅ System environment variables supported as an alternative
- ✅ `.env.example` provides a configuration template

**Best practices:**

```bash
# ✅ Correct: use a .env file
cp .env.example .env
# Edit .env and fill in real keys

# ❌ Wrong: write keys directly in code
GEMINI_API_KEY = "AIzaSy..."  # Never do this!
```

### Pre-Commit Check

```bash
# Verify no key leakage
grep -r "AIzaSy\|ak-" --exclude-dir=.git --exclude-dir=venv .
# Should produce no output

# Check that .env is excluded
git status
# Confirm .env is not in the staged list
```

For detailed information, see:
- **API_MANAGEMENT.md** — Complete API key management guide
- **ENV_SETUP.md** — Environment variable configuration guide
- **SECURITY.md** — Security best practices

---

## 📝 Changelog

### v2.0.0 (2026-01-11)

- 🎬 **New video features**
  - Kling AI transition video generation
  - Interactive video player (mixed video + image)
  - FFmpeg full video composition
  - Cover loop preview video
- 🔧 **Video composition improvements**
  - Auto-normalize resolution and frame rate
  - Fix video concatenation compatibility issues
  - Static slide display time changed to 2 seconds
- 🐛 **Bug fixes**
  - Fix preview mode state management issue
  - Fix FFmpeg filter parameter format error
- 📚 **Documentation updates**
  - Complete README rewrite
  - New video feature usage guide
  - Updated API key configuration instructions

### v1.0.0 (2026-01-09)

- ✨ Initial release
- 🎨 2 built-in professional styles
- 🖼️ 2K/4K resolution support
- 🎬 HTML5 image player
- 📊 Intelligent document analysis
- 🔐 Secure environment variable management

---

## 🤝 Contributing

Contributions are welcome! You can:

### Add New Styles

1. Fork this project
2. Create a new style file in `styles/`
3. Write prompts following the existing style format
4. Test the generated output
5. Submit a Pull Request

### Report Issues

Submit issues at [GitHub Issues](https://github.com/op7418/NanoBanana-PPT-Skills/issues). Please include:
- Error message
- Steps to reproduce
- System environment
- Log files (if any)

---

## 📄 License

MIT License

Copyright (c) 2026 歸藏

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## 🙏 Acknowledgements

- **Google Gemini Team** — for the powerful Nano Banana Pro image generation model
- **Kling AI Team** — for the high-quality video generation service
- **FFmpeg Project** — for the powerful video processing tool
- **Open Source Community** — for the various tools and inspiration

---

## 📞 Contact

- **Creator**: 歸藏
- **GitHub**: [@op7418](https://github.com/op7418)
- **Issues**: [GitHub Issues](https://github.com/op7418/NanoBanana-PPT-Skills/issues)

---

<div align="center">

**⭐ If this project is helpful to you, please give it a Star!**

Made with ❤️ by 歸藏 | Powered by Google Gemini & Kling AI & FFmpeg

</div>
