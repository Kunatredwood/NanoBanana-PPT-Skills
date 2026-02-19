# API Key Management Guidelines

## 📋 Current Configuration

### API Storage Location

All API keys are now stored in a single location:

```
📁 ppt-generator/.env
```

### ✅ Security Verification

- ✅ `.env` file has been created
- ✅ Protected by `.gitignore` (rule on line 15)
- ✅ Will not be committed to Git
- ✅ `run.sh` can load it correctly

### 🎯 Usage

**No additional configuration needed!** Just run directly:

```bash
./run.sh --plan slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

Output will show:
```
📌 Loading API keys from .env file
```

---

## 🔐 API Management Guidelines

### 1️⃣ Adding New API Keys

Edit the `.env` file:

```bash
# Open with an editor
nano .env

# Or use VS Code
code .env
```

Add entries in the following format:

```bash
# API name description
# Purpose: describe what this API is used for
# Get it at: https://...
API_NAME=your-api-key-here
```

**Example:**

```bash
# OpenAI API
# Purpose: May be used for document analysis in the future
# Get it at: https://platform.openai.com/api-keys
OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxx
```

### 2️⃣ Using API Keys in Code

**❌ Wrong approach** (hardcoding):

```python
# Never do this!
api_key = "AIzaSyAfHE4vctPhMF2mVn96aEZZp8WuURlaGpM"
```

**✅ Correct approach** (read from environment variables):

```python
import os

# Read from environment variable
api_key = os.environ.get("GEMINI_API_KEY")

# Or with a default value
api_key = os.getenv("GEMINI_API_KEY", "")

# Check if it exists
if not api_key:
    raise ValueError("GEMINI_API_KEY environment variable not found")
```

### 3️⃣ Environment Variable Loading Priority

`run.sh` loading logic:

```
1. System environment variables (~/.zshrc, etc.)
   ↓ if not found
2. .env file
   ↓ if neither found
3. Error prompting user to configure
```

This means:
- ✅ CI/CD environments can use system environment variables
- ✅ Local development uses .env file
- ✅ Flexible switching between different environment keys

### 4️⃣ Multi-Environment Management

If you need to manage multiple environments (dev/test/prod):

```bash
# Development
.env.development

# Test
.env.test

# Production
.env.production
```

To use a specific environment:

```bash
# Copy the corresponding environment config
cp .env.development .env

# Or use a symbolic link
ln -sf .env.development .env
```

---

## 📝 .env File Structure

### Current Structure

```bash
.env
├─ [Comments]
│  ├─ Security reminder
│  ├─ Usage instructions
│  └─ Loading priority description
│
├─ [Primary API keys]
│  └─ GEMINI_API_KEY (configured)
│
├─ [Backup API keys]
│  ├─ OPENAI_API_KEY (commented out)
│  ├─ ANTHROPIC_API_KEY (commented out)
│  └─ STABILITY_API_KEY (commented out)
│
└─ [Project configuration]
   ├─ DEFAULT_RESOLUTION (commented out)
   ├─ DEFAULT_STYLE (commented out)
   └─ OUTPUT_DIR (commented out)
```

### Field Descriptions

| Variable | Status | Purpose | Where to Get It |
|----------|--------|---------|-----------------|
| `GEMINI_API_KEY` | ✅ Configured | Nano Banana Pro image generation | [Google AI Studio](https://makersuite.google.com/app/apikey) |
| `OPENAI_API_KEY` | 💤 Reserved | May be used for document analysis in the future | [OpenAI Platform](https://platform.openai.com/api-keys) |
| `ANTHROPIC_API_KEY` | 💤 Reserved | May be used for Claude API in the future | [Anthropic Console](https://console.anthropic.com/) |
| `STABILITY_API_KEY` | 💤 Reserved | May be used for other image models in the future | [Stability AI](https://platform.stability.ai/) |

---

## 🚨 Security Checklist

### During Development

- [ ] Never hardcode API keys in code
- [ ] Use `os.environ.get()` or `os.getenv()` to read them
- [ ] Add error messages when keys are missing
- [ ] Read keys during function/class initialization, not on every request

### Before Committing

- [ ] Run `git status` to confirm .env is not in the list
- [ ] Run `grep -r "AIzaSy" --exclude-dir=.git .` with no output
- [ ] Check that `.gitignore` includes `.env`
- [ ] No hardcoded keys anywhere in the code

### When Sharing the Project

- [ ] Provide `.env.example` as a template
- [ ] Explain how to configure it in README
- [ ] Do not send .env files via chat/email
- [ ] Suggest users use their own API keys

---

## 💡 Best Practices

### 1. Key Rotation

Regularly update API keys (recommended every 3–6 months):

```bash
# 1. Generate a new key on the API platform
# 2. Update the .env file
# 3. Test that everything still works
# 4. Revoke the old key
```

### 2. Key Permissions

Create separate API keys for different purposes:

```bash
# Development (limited quota)
GEMINI_API_KEY_DEV=...

# Production (full access)
GEMINI_API_KEY_PROD=...
```

### 3. Error Handling

Add friendly error messages in your code:

```python
import os
import sys

def get_api_key(key_name):
    """Safely retrieve an API key"""
    api_key = os.getenv(key_name)

    if not api_key:
        print(f"❌ Error: {key_name} environment variable not found")
        print("")
        print("Please configure the API key:")
        print("1. Edit the .env file")
        print(f"2. Add: {key_name}=your-key")
        print("3. Save and re-run")
        sys.exit(1)

    return api_key

# Usage
gemini_key = get_api_key("GEMINI_API_KEY")
```

### 4. Log Safety

Do not log the full key:

```python
# ❌ Dangerous
print(f"Using API key: {api_key}")

# ✅ Safe
print(f"Using API key: {api_key[:8]}...{api_key[-4:]}")
# Output: Using API key: AIzaSyAf...GpM
```

---

## 🔄 Migration Guide

### From System Environment Variables to .env

If you previously configured keys in `~/.zshrc`:

**Step 1**: Remove from .zshrc

```bash
# Edit the config file
nano ~/.zshrc

# Delete this line
export GEMINI_API_KEY="..."

# Reload
source ~/.zshrc
```

**Step 2**: Add to .env

```bash
# The .env file already contains the key, no extra steps needed
```

**Step 3**: Test

```bash
./run.sh --help
# Should show: 📌 Loading API keys from .env file
```

### From .env to System Environment Variables

If you want to use system environment variables (shared across projects):

```bash
# 1. Copy the key from .env
cat .env | grep GEMINI_API_KEY

# 2. Add to .zshrc
echo 'export GEMINI_API_KEY="..."' >> ~/.zshrc

# 3. Reload
source ~/.zshrc

# 4. Test
./run.sh --help
# Should show: ✅ Using API key from system environment variables
```

---

## 📚 Related Documentation

- **SECURITY.md** - Complete security guide
- **ENV_SETUP.md** - Environment variable configuration details
- **.env.example** - Configuration template
- **README.md** - Project usage guide

---

## 🆘 FAQ

### Q: Where is the .env file?

A: In the project root directory at `ppt-generator/.env`

### Q: How do I view my API key?

A:
```bash
cat .env | grep GEMINI_API_KEY
```

### Q: Can I commit the .env file?

A: **Absolutely not!** The .env file contains sensitive information and is protected by .gitignore.

### Q: How do I share configuration with a team?

A:
1. Commit the `.env.example` template
2. Team members copy it to `.env`
3. Each person fills in their own API key

### Q: How do I know where the key was loaded from?

A: Check the output when running any command:
- `✅ Using API key from system environment variables` — loaded from system
- `📌 Loading API keys from .env file` — loaded from .env

---

## ✅ Summary

### Current Setup

✅ **Unified API key management**
- Storage: `ppt-generator/.env`
- Security: `.gitignore` rules
- Auto-loading: `run.sh` script

✅ **Development standards**
- No hardcoding in code
- Use `os.getenv()` to read
- Add error handling
- Don't log full keys

✅ **Security guarantees**
- .env will not be committed to Git
- .env.example serves as template
- Regularly rotate keys
- Use different keys for different environments

### Ready to Use

You can now iterate on features directly — all API configuration is ready!

```bash
# Run directly
./run.sh --plan your_plan.json --style styles/gradient-glass.md
```

---

**Created**: 2026-01-11
**Last Updated**: 2026-01-11
**Author**: 歸藏
