# Quick Start Guide

## 🚀 Get Started in 5 Minutes

### Step 1: Set Your API Key

```bash
export GEMINI_API_KEY='your-google-ai-api-key'
```

**Get your API key**: Visit [Google AI Studio](https://makersuite.google.com/app/apikey)

### Step 2: Install Dependencies

```bash
pip install google-genai pillow
```

### Step 3: Prepare Your Document

Create or prepare a markdown document, e.g. `my-document.md`:

```markdown
# My Presentation Topic

## Part 1: Background
Background introduction here...

## Part 2: Core Points
- Point 1: ...
- Point 2: ...
- Point 3: ...

## Part 3: Summary
Key findings and action recommendations...
```

### Step 4: Use in Claude Code

Open Claude Code and run:

```
I want to generate a 5-page PPT from my-document.md using the gradient glass card style at 2K resolution.
```

Claude will automatically:
1. Analyze the document content
2. Plan the 5-page PPT structure
3. Generate high-quality images
4. Create an HTML presentation viewer

### Step 5: View the Result

```bash
open outputs/TIMESTAMP/index.html
```

Keyboard controls:
- `←` `→`: Navigate slides
- `ESC`: Fullscreen mode
- `Space`: Auto-play

## 💡 Tips

### Tip 1: Choose the Right Slide Count

- **5 slides**: Elevator pitch (5 minutes)
- **5–10 slides**: Standard presentation (10–15 minutes)
- **10–15 slides**: In-depth session (20–30 minutes)
- **20–25 slides**: Full training (45–60 minutes)

### Tip 2: Optimize Your Document Structure

**Good structure:**
```markdown
# Main Title

## Core Point 1
- Key point
- Key point
- Key point

## Core Point 2
[Detailed explanation...]

## Summary
[Key conclusions...]
```

**Less ideal structure:**
```markdown
# Title
One long paragraph of text with no sectioning...
```

### Tip 3: Resolution Selection Guide

| Use Case | Recommended Resolution | Generation Time | File Size |
|----------|------------------------|-----------------|-----------|
| Daily presentations | 2K | ~30s/slide | ~2MB/slide |
| Formal occasions | 2K | ~30s/slide | ~2MB/slide |
| Print output | 4K | ~60s/slide | ~8MB/slide |
| Large screen display | 4K | ~60s/slide | ~8MB/slide |

### Tip 4: Batch Generation

To generate multiple versions at once:

```bash
# 5-slide brief version
python generate_ppt.py --plan plan_5.json --style styles/gradient-glass.md --resolution 2K --output outputs/v1-brief

# 15-slide detailed version
python generate_ppt.py --plan plan_15.json --style styles/gradient-glass.md --resolution 2K --output outputs/v2-detailed
```

## 🎨 Custom Styles

### Create a New Style

1. Copy an existing style file:
```bash
cp styles/gradient-glass.md styles/my-style.md
```

2. Edit the style definition:
```markdown
# My Custom Style

## Style ID
my-custom-style

## Base Prompt Template
[Modify to describe your style...]
```

3. Use the new style:
```bash
python generate_ppt.py --plan plan.json --style styles/my-style.md
```

## 🔧 Advanced Usage

### Manually Adjust Prompts

1. View generated prompts:
```bash
cat outputs/TIMESTAMP/prompts.json
```

2. Copy and modify the prompt for a specific slide

3. Create a new plan file and regenerate

### Mix Page Types

Customize page types in the JSON plan file:

```json
{
  "slides": [
    {"page_type": "cover", "content": "..."},
    {"page_type": "content", "content": "..."},
    {"page_type": "data", "content": "..."},
    {"page_type": "content", "content": "..."}
  ]
}
```

### Parallel Generation

Generate multiple versions simultaneously:

```bash
python generate_ppt.py --plan plan1.json --style styles/gradient-glass.md --output outputs/v1 &
python generate_ppt.py --plan plan2.json --style styles/gradient-glass.md --output outputs/v2 &
wait
echo "All versions generated!"
```

## 📋 FAQ

### Q: What if generation fails?

A: Check the following:
1. Is the API key set correctly?
2. Is the network connection stable?
3. Are all Python dependencies installed?
4. Review the detailed error message

### Q: Can I generate content in Chinese?

A: Yes! Nano Banana Pro supports multiple languages, including Chinese.

### Q: How long does generation take?

A:
- 2K: About 30 seconds per slide
- 4K: About 60 seconds per slide
- A 5-slide PPT takes approximately 2.5–5 minutes

### Q: How do I export to PDF?

A: Open the HTML player in a browser and use the print function:
1. Open the player
2. Press `Cmd+P` (Mac) or `Ctrl+P` (Windows)
3. Select "Save as PDF"

### Q: Can I modify an already generated PPT?

A: Yes, through the following methods:
1. Edit the JSON plan file
2. Modify the prompts
3. Re-run the generation script

### Q: What document formats are supported?

A: Markdown format works best, but plain text is also supported.

## 📞 Get Help

Stuck?
1. See README.md
2. See ppt-generator.md for detailed documentation
3. Use `/help` in Claude Code

## 🎯 Best Practices Checklist

✅ Use clear headings and sections
✅ Keep each slide to 3–5 key points maximum
✅ Choose an appropriate slide count
✅ Use 2K resolution for everyday use
✅ Save the original JSON plan file
✅ Check API quota usage regularly
✅ Test the player across different browsers

---

**Start creating!** 🚀
