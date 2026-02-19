# System Environment Variable Configuration Guide

## ✅ Current Configuration Status

Your project now uses **system environment variables** to manage API keys — the most secure approach!

### 🎯 Comparison of Approaches

| Approach | Security | Convenience | Git Safety |
|----------|----------|-------------|------------|
| Hardcoded | ❌ Very low | ✓ Convenient | ❌ Will leak |
| .env file | ⚠️ Medium | ✓ Convenient | ⚠️ Requires .gitignore |
| **System env vars** | ✅ **High** | ✅ **Most convenient** | ✅ **Fully safe** |

## 📋 Completed Configuration

### 1. System Environment Variables ✅

The API key has been added to your `~/.zshrc`:

```bash
# Google AI API Key for PPT Generator
export GEMINI_API_KEY="your-api-key-here"
```

**Verification:**
```bash
echo $GEMINI_API_KEY
# Should display your API key
```

### 2. Smart Detection in run.sh ✅

The startup script has been updated with the following priority order:
1. **System environment variables** (highest priority) ✅
2. .env file (fallback)

When you run `./run.sh`, it will show:
```
✅ Using API key from system environment variables
```

### 3. Project File Cleanup ✅

- ✅ `.env` file has been deleted
- ✅ `.env.example` retained (as a template)
- ✅ `run.sh` contains no hardcoded keys
- ✅ All documentation uses placeholders

## 🔐 Git Commit Safety

### Committing to GitHub is now completely safe!

**What will NOT be committed:**
- ❌ API keys (stored in system environment variables)
- ❌ `.env` file (deleted and in .gitignore)
- ❌ Virtual environment (venv/)
- ❌ Output files (outputs/)

**What WILL be committed (all safe):**
- ✅ `.env.example` - contains only a template
- ✅ `.gitignore` - Git ignore rules
- ✅ `run.sh` - reads keys from environment variables
- ✅ `generate_ppt.py` - Python script
- ✅ All documentation and style files

### Verification Commands

```bash
# Search for API keys in the project
grep -r "AIzaSy" --exclude-dir=.git --exclude-dir=venv .

# Should produce no output! ✅
```

## 🚀 Usage

### In the Current Project

Run directly — system environment variables will be used automatically:

```bash
./run.sh --plan ../test_slides_plan.json --style styles/gradient-glass.md --resolution 2K
```

Output will show:
```
✅ Using API key from system environment variables
```

### On a New Machine

When you clone the project on a new machine:

**Step 1**: Clone the repository
```bash
git clone https://github.com/your-username/ppt-generator.git
cd ppt-generator
```

**Step 2**: Configure environment variables (choose by shell)

**zsh users (recommended):**
```bash
echo 'export GEMINI_API_KEY="your-api-key"' >> ~/.zshrc
source ~/.zshrc
```

**bash users:**
```bash
echo 'export GEMINI_API_KEY="your-api-key"' >> ~/.bashrc
source ~/.bashrc
```

**fish users:**
```bash
set -Ux GEMINI_API_KEY "your-api-key"
```

**Step 3**: Install dependencies and run
```bash
python3 -m venv venv
source venv/bin/activate
pip install google-genai pillow
./run.sh --help
```

## 🔄 Managing API Keys

### View Current Key

```bash
echo $GEMINI_API_KEY
```

### Temporarily Change Key (current session only)

```bash
export GEMINI_API_KEY="new-key-here"
```

### Permanently Change Key

Edit the config file:
```bash
nano ~/.zshrc  # or your preferred editor
```

Find and update this line:
```bash
export GEMINI_API_KEY="new-key-here"
```

Reload the config:
```bash
source ~/.zshrc
```

### Delete Key

Edit `~/.zshrc`, remove the line containing `GEMINI_API_KEY`, then:
```bash
source ~/.zshrc
unset GEMINI_API_KEY
```

## 💡 Best Practices

### ✓ Recommended

1. **Use system environment variables for all keys**
   ```bash
   # Example: adding multiple API keys
   export GEMINI_API_KEY="..."
   export OPENAI_API_KEY="..."
   export AWS_ACCESS_KEY="..."
   ```

2. **Rotate API keys regularly**
   - Every 3–6 months
   - Immediately if abnormal usage is detected

3. **Use different keys for different projects** (optional)
   - Easier to track usage
   - Limits the blast radius of a single key compromise

4. **Back up environment variable configs**
   ```bash
   # Export config (store securely!)
   grep "export.*_KEY" ~/.zshrc > ~/my-env-backup.txt
   ```

### ✗ Avoid

- ❌ Hardcoding keys in code
- ❌ Committing `.zshrc` to Git
- ❌ Sending keys via email
- ❌ Exposing keys in screenshots
- ❌ Using the same key across multiple public projects

## 🛡️ Security Checklist

Before committing to GitHub, confirm:

- [ ] Running `grep -r "AIzaSy" .` produces no output
- [ ] `.env` file does not exist or is in .gitignore
- [ ] `run.sh` contains no hardcoded keys
- [ ] All documentation uses `your-api-key-here` as placeholder
- [ ] `git status` shows no sensitive files
- [ ] `.zshrc` is not in the Git repository

All ✅? You're safe to commit!

## 📊 Security Level Comparison

```
┌─────────────────────────────────────────────┐
│ Security Level: System Environment Variables │
├─────────────────────────────────────────────┤
│                                             │
│  Git leak risk          ████████████ 0%    │
│  Code leak risk         ████████████ 0%    │
│  Documentation leak     ████████████ 0%    │
│  Convenience            ████████████ 100%  │
│  Cross-project sharing  ████████████ 100%  │
│                                             │
└─────────────────────────────────────────────┘
```

## 🎉 Summary

You now have the most secure API key management approach:

✅ **API keys stored in system environment variables**
✅ **Project code contains absolutely no keys**
✅ **Safe to commit to GitHub**
✅ **Share the same key across projects**
✅ **Simple and fast setup on new machines**

---

**Need help?**
- System environment variable issues: see the "Managing API Keys" section in this document
- Git commit issues: see SECURITY.md
- Project usage issues: see README.md and QUICKSTART.md
