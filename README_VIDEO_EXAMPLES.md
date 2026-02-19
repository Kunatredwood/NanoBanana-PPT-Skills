# README Video Demo Options

## Recommended Approach Comparison

### 🎯 Comparison of Options

| Option | File Size Limit | Domestic Access | International Access | Auto-play | Maintenance |
|--------|----------------|-----------------|----------------------|-----------|-------------|
| **Animated GIF** | Recommended < 10MB | ✅ Fast | ✅ Fast | ✅ Yes | ⭐ Low |
| **GitHub repo video** | < 100MB | ⚠️ Slow | ✅ Fast | ❌ No | ⭐ Low |
| **Bilibili** | Unlimited | ✅ Fast | ⚠️ Slow | ❌ No | ⭐⭐ Medium |
| **GitHub + Bilibili** | — | ✅ Fast | ✅ Fast | ❌ No | ⭐⭐ Medium |
| **Cloudinary** | 25GB free | ✅ Fast | ✅ Fast | ❌ No | ⭐⭐⭐ High |

### 💡 Specific Recommendations

**For your project (NanoBanana PPT Skills), I recommend:**

1. **First choice: Animated GIF** — if you can compress it to 5–10MB
   - Best user experience, auto-plays
   - Ideal for a 10–20 second highlight demo

2. **Alternative: GitHub repo + Bilibili dual links**
   - GitHub hosts a short video (< 50MB) for core feature demo
   - Bilibili hosts the full walkthrough (with narration)
   - Serves both domestic and international users

---

## Markdown Code Examples

### Option 1: Animated GIF (recommended)

Add the following after line 15 of README.md (after `</div>`):

```markdown
</div>

---

## 🎬 Demo

<div align="center">

![NanoBanana PPT Skills Demo](demo.gif)

*AI-generated PPT with smooth transition animations*

</div>

---
```

**Or use an HTML tag to control the size:**

```markdown
<div align="center">
  <img src="demo.gif" alt="NanoBanana PPT Skills Demo" width="800">
  <p><em>AI-generated PPT with smooth transition animations</em></p>
</div>
```

---

### Option 2: GitHub Repository Video (< 100MB)

```markdown
## 🎬 Demo

<div align="center">

https://github.com/op7418/NanoBanana-PPT-Skills/assets/YOUR_USER_ID/demo.mp4

*Click to play the full demo*

</div>
```

**Or use an HTML5 video tag for more control:**

```markdown
<div align="center">
  <video src="https://github.com/op7418/NanoBanana-PPT-Skills/assets/YOUR_USER_ID/demo.mp4"
         width="800"
         controls
         loop
         muted>
    Your browser does not support video playback.
  </video>
  <p><em>AI-generated PPT with smooth transition animations</em></p>
</div>
```

---

### Option 3: Bilibili Embed

```markdown
## 🎬 Demo

<div align="center">

[![Watch Demo on Bilibili](https://i0.hdslb.com/bfs/archive/VIDEO_COVER.jpg)](https://www.bilibili.com/video/BVXXXXXXX)

**🎥 [Watch Full Demo (Bilibili)](https://www.bilibili.com/video/BVXXXXXXX)**

*Includes detailed feature walkthrough and usage tutorial*

</div>
```

---

### Option 4: GitHub + Bilibili Dual Hosting (best option for your project)

```markdown
## 🎬 Demo

<div align="center">

### Quick Preview (30 seconds)

https://github.com/op7418/NanoBanana-PPT-Skills/assets/YOUR_USER_ID/demo-short.mp4

### Full Tutorial

**🎥 [Watch Full Demo (Bilibili, 5 min)](https://www.bilibili.com/video/BVXXXXXXX)** — detailed feature walkthrough

**🌍 [Watch Full Demo (YouTube, 5 min)](https://youtube.com/watch?v=XXXXXXXXX)** — English subtitles available

</div>

---
```

---

### Option 5: Cloudinary Hosting

```markdown
## 🎬 Demo

<div align="center">

<video
  src="https://res.cloudinary.com/YOUR_CLOUD_NAME/video/upload/v1234567890/demo.mp4"
  width="800"
  controls
  loop
  muted
  poster="https://res.cloudinary.com/YOUR_CLOUD_NAME/image/upload/v1234567890/demo-poster.jpg">
</video>

*AI-generated PPT with smooth transition animations*

</div>
```

---

### Option 6: Combined Demo Formats (full version)

```markdown
## 🎬 Demo

<div align="center">

### 🎨 Gradient Glass Style Demo

![Gradient Glass Style Demo](demos/gradient-glass-demo.gif)

### 🎞️ Full PPT Generation Workflow

https://github.com/op7418/NanoBanana-PPT-Skills/assets/YOUR_USER_ID/full-demo.mp4

### 📺 Full Tutorial Videos

| Platform | Link | Duration | Description |
|----------|------|----------|-------------|
| 🎬 **Bilibili** | [Watch Tutorial](https://bilibili.com/video/BVXXXX) | 5:30 | Chinese narration, includes installation and usage |
| 🌏 **YouTube** | [Watch Tutorial](https://youtube.com/watch?v=XXXX) | 5:30 | English subtitles |

</div>

---
```

---

## Step-by-Step Instructions

### If You Choose the GIF Option:

1. **Generate the GIF** (recommended: 10–20 second highlight clip):

```bash
cd /Users/guohao/Documents/code/ppt/ppt-generator

# Method 1: Convert full video to GIF (will be large)
ffmpeg -i outputs/20260112_135018_video/full_ppt_video.mp4 \
  -vf "fps=10,scale=800:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" \
  -loop 0 \
  demo.gif

# Method 2: Trim to first 20 seconds (recommended)
ffmpeg -i outputs/20260112_135018_video/full_ppt_video.mp4 \
  -t 20 \
  -vf "fps=10,scale=800:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" \
  -loop 0 \
  demo.gif

# Method 3: Ultra-compressed version (if file is too large)
ffmpeg -i outputs/20260112_135018_video/full_ppt_video.mp4 \
  -t 15 \
  -vf "fps=8,scale=600:-1:flags=lanczos,split[s0][s1];[s0]palettegen=max_colors=128[p];[s1][p]paletteuse=dither=bayer" \
  -loop 0 \
  demo-compressed.gif
```

2. **Check the file size**:
```bash
ls -lh demo.gif
# Aim for 5–10MB or less
```

3. **Place it in the repo root**:
```bash
# Move the GIF to the repo root
mv demo.gif /Users/guohao/Documents/code/ppt/ppt-generator/

# Add to git
git add demo.gif
```

### If You Choose the GitHub Video Option:

1. **Compress the video** (must be < 100MB):

```bash
# Compress to 1080p, 5Mbps bitrate
ffmpeg -i outputs/20260112_135018_video/full_ppt_video.mp4 \
  -vf "scale=1920:1080:force_original_aspect_ratio=decrease" \
  -c:v libx264 -b:v 5M -maxrate 5M -bufsize 10M \
  -c:a aac -b:a 128k \
  demo-compressed.mp4

# Check size
ls -lh demo-compressed.mp4
```

2. **Upload to GitHub**:
   - Drag and drop the video into a GitHub Issue or Pull Request
   - Copy the generated URL (e.g., `https://github.com/user/repo/assets/12345/video.mp4`)
   - Use that URL in the README

### If You Choose the Bilibili Option:

1. Record a full demo (with narration)
2. Upload to Bilibili, set a cover image
3. Copy the video link (BV number)
4. Use it in the README

---

## Recommended Full Layout

```markdown
# NanoBanana PPT Skills

> A powerful AI-driven tool for generating high-quality PPT images and video presentations with smart transitions and an interactive player

<div align="center">

![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Python](https://img.shields.io/badge/python-3.8+-green.svg)

**Creator**: [歸藏](https://github.com/op7418)

[Features](#-features) • [Demo](#-demo) • [One-Click Install](#-one-click-install) • [Usage Guide](#-usage-guide)

</div>

---

## 🎬 Demo

<div align="center">

### 🎨 Auto-generated Gradient Glass Style PPT

![Demo](demo.gif)

*From document analysis to transition video — one click*

### 📺 Full Tutorial

**🎥 [Watch Detailed Tutorial (Bilibili, 5 min)](https://bilibili.com/video/BVXXXX)** — includes installation and usage instructions

</div>

---

## 📖 Introduction

...
```

---

## My Final Recommendation

**For your project, here's what I recommend:**

1. **Immediate action:**
   - Generate a 15–20 second animated GIF (showcasing the core feature)
   - Place it at the top of README for a great first impression

2. **Follow-up enhancement:**
   - Record a 3–5 minute full demo video
   - Upload to Bilibili (with Chinese narration)
   - Add a link in the README

3. **README structure:**
```
Title + Badges
    ↓
Navigation links (add "Demo")
    ↓
🎬 Demo (GIF, auto-plays)
    ↓
Full tutorial link (Bilibili/YouTube)
    ↓
Introduction
    ↓
Other content...
```

Want me to help you execute any of these steps, such as:
1. Generate an optimized GIF
2. Compress the video to < 100MB
3. Update the README to add a demo section
