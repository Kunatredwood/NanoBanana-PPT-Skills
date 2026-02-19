# Setup Complete!

## ✅ Completed Configuration

### 1. Python Dependencies Installed ✓
- google-genai (1.57.0)
- pillow (12.1.0)
- All dependencies installed in the virtual environment

### 2. API Key Configured ✓
- GEMINI_API_KEY is set
- Key stored in .env file
- .gitignore configured to prevent key leakage

### 3. Convenience Script Created ✓
- run.sh: startup script that automatically activates the virtual environment and loads the API key

## 🚀 Ready to Use!

### Option 1: Use the convenience script (recommended)

```bash
# Run directly — environment is handled automatically
./run.sh --plan ../test_slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

### Option 2: Activate environment manually

```bash
# Activate virtual environment
source venv/bin/activate

# Set API key (if needed)
export GEMINI_API_KEY="your-api-key-here"

# Run the script
python generate_ppt.py --plan ../test_slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

### Option 3: Use in Claude Code (simplest)

Just tell Claude Code:

```
I want to generate a 5-page PPT based on the "MoYiLanJian.md" document
```

Claude will handle all steps automatically.

## 🧪 Quick Test

A test plan file `test_slides_plan.json` has been created for you, containing 5 pages of PPT content about "MoYiLanJian".

### Run the test:

```bash
cd /Users/guohao/Documents/code/ppt/ppt-generator
./run.sh --plan ../test_slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

### Generation notes:
- Each page takes about 30 seconds
- 5 pages will take about 2.5 minutes total
- The output path will be shown once generation is complete

### View the result:

```bash
# Open the player (the exact path will be shown after generation)
open outputs/TIMESTAMP/index.html
```

## 📁 Project File Structure

```
ppt-generator/
├── run.sh                    # Convenience startup script (recommended)
├── .env                      # API key configuration (do not commit)
├── .gitignore               # Git ignore file (protects keys)
├── venv/                    # Python virtual environment
├── generate_ppt.py          # Core generation script
├── ppt-generator.md         # Skill definition
├── README.md                # Project documentation
├── QUICKSTART.md            # Quick start guide
├── styles/                  # Style library
│   └── gradient-glass.md    # Gradient glass card style
├── templates/               # HTML templates
│   └── viewer.html          # PPT player
└── outputs/                 # Generated results (auto-created)
```

## ⚙️ Environment Variables

The API key is configured in:
1. **run.sh** — automatically loaded by the startup script
2. **.env** — environment variable file

**Important reminders:**
- ⚠️ Do not commit the .env file to a public repository
- ⚠️ The API key is already covered by .gitignore
- ⚠️ If sharing the project, remove the key from the .env file

## 🎯 Next Steps

### Option 1: Run a quick test
```bash
./run.sh --plan ../test_slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

### Option 2: Generate your own PPT
1. Prepare your document (Markdown or plain text)
2. Describe your needs in Claude Code
3. Claude will automatically analyze the document and generate the PPT

### Option 3: Read the documentation
- `README.md` — Full project documentation
- `QUICKSTART.md` — Quick start guide
- `ppt-generator.md` — Detailed technical documentation

## 💡 Usage Tips

### Resolution options:
- **2K (2752x1536)**: Everyday use, fast generation
- **4K (5504x3072)**: Important occasions, high-quality output

### Slide count suggestions:
- **5 slides**: 5-minute quick pitch
- **5–10 slides**: 15-minute standard presentation
- **10–15 slides**: 30-minute in-depth session
- **20–25 slides**: 60-minute full training

### Player keyboard shortcuts:
- `←` `→`: Navigate slides
- `↑` `Home`: First slide
- `↓` `End`: Last slide
- `Space`: Auto-play / pause
- `ESC`: Toggle fullscreen
- `H`: Show / hide controls

## 🆘 Having Issues?

### Environment issues
```bash
# Reactivate the virtual environment
source venv/bin/activate

# Check dependencies
pip list | grep genai
```

### API issues
```bash
# Check API key
echo $GEMINI_API_KEY

# Set manually (if needed)
export GEMINI_API_KEY="your-key"
```

### Generation failures
1. Check your network connection
2. Confirm the API key is valid
3. Try a lower resolution
4. Check the detailed error message

## 🎉 Ready to Go!

Your PPT generator is fully configured and ready to use!

**Recommended first step:** Run the test command to experience the full workflow.

```bash
./run.sh --plan ../test_slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

Happy creating! 🚀
