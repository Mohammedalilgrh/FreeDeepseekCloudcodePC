# Free Claude Code + DeepSeek — Setup Walkthrough

Everything is installed, configured, and backed up. Here's a complete guide.

---

## ✅ What Was Done

| Step | Result |
|------|--------|
| Cloned `Alishahryar1/free-claude-code` | ✅ `C:\Users\lraq laptop\.gemini\antigravity-ide\scratch\free-claude-code` |
| Configured DeepSeek API key | ✅ `~/.fcc/.env` and local `.env` |
| All Claude model tiers routed to DeepSeek | ✅ `deepseek/deepseek-chat` |
| `fcc-server` installed & tested | ✅ Boots on `http://127.0.0.1:8082` |
| `fcc-claude --version` confirmed working | ✅ Claude Code 1.4.0 |
| Created `fcc-run` shortcode | ✅ Normal mode |
| Created `fcc-skip` shortcode | ✅ Skip-permissions mode |
| Created `Desktop\fcc-backup` | ✅ Restore-ready backup |
| Created `Desktop\repo` | ✅ Push-ready Git repo |

---

## 🚀 How to Use the Shortcodes

Both shortcodes live in `C:\Users\lraq laptop\.local\bin\` which is already on your system PATH.  
Open **any Command Prompt or PowerShell window** and type:

### Normal Mode — `fcc-run`
```cmd
fcc-run
```
- Checks if `fcc-server` is running on port 8082. If not, **starts it automatically** in a new window.
- Launches Claude Code connected to your DeepSeek API key.
- Asks for permission before running any tool (safe default).

### Skip Permissions Mode — `fcc-skip`
```cmd
fcc-skip
```
- Same as above, but adds `--dangerously-skip-permissions`.
- Claude Code **never asks for permission** — it runs every command automatically.
- ⚠️ Use this only when you trust the task and want a fully automated experience.

> **You can also pass extra arguments:**
> ```cmd
> fcc-run --model claude-sonnet-4-5
> fcc-skip "build me a REST API"
> ```

---

## ⚙️ Configuration

Your DeepSeek key and model are stored in:
```
C:\Users\lraq laptop\.fcc\.env
```

To change settings (model, auth token, etc.), edit that file or open the **Admin UI** when the server is running:
```
http://127.0.0.1:8082/admin
```

**Current model routing:**
| Claude Tier | Routes to |
|-------------|-----------|
| Opus | `deepseek/deepseek-chat` |
| Sonnet | `deepseek/deepseek-chat` |
| Haiku | `deepseek/deepseek-chat` |
| Fallback | `deepseek/deepseek-chat` |

---

## 🛡️ Desktop\fcc-backup — Emergency Recovery

**Location:** `C:\Users\lraq laptop\Desktop\fcc-backup\`

If anything breaks, just double-click `restore.bat` inside this folder.  
It will copy everything back to where it belongs:

| Folder | Restores to |
|--------|-------------|
| `fcc-config\` | `~/.fcc/` (API key & settings) |
| `fcc-source\` | `~/.gemini/.../scratch/free-claude-code/` (source code) |
| `fcc-local-bin\` | `~/.local/bin/` (the `fcc-run` and `fcc-skip` shortcodes) |

---

## 📁 Desktop\repo — Push to Your Git Repo

**Location:** `C:\Users\lraq laptop\Desktop\repo\`

This folder is a **complete, pre-configured copy** of the repo.  
It includes your `.env`, shortcodes, and an `install-local.bat` helper.

**To push it to your own GitHub repo:**
```cmd
cd C:\Users\lraq laptop\Desktop\repo
git remote set-url origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git add .
git commit -m "Initial setup with DeepSeek"
git push
```

**If you ever clone it fresh on a new machine:**
```cmd
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
install-local.bat
```
That's it — `install-local.bat` runs the installer and registers both shortcodes automatically.

> [!CAUTION]
> Your `.env` file contains your DeepSeek API key. Make sure your GitHub repo is **private**, or remove the `.env` from the repo and use `.env.example` instead.

---

## 🔧 First-Time Run Checklist

1. Open a **new** Command Prompt or PowerShell window
2. Type `fcc-run` and press Enter
3. A new window opens running `fcc-server`
4. Claude Code launches — you're connected to DeepSeek!
5. To configure models, open `http://127.0.0.1:8082/admin` in your browser
