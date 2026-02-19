# Git + Obsidian Guide

> How this vault is shared between partners using GitHub, and how it works alongside Obsidian.

---

## How It Works

This vault is both an **Obsidian vault** (a folder of markdown files you open in Obsidian) and a **GitHub repository** (version-controlled, shared between partners). These two things coexist in the same folder.

```
Your Computer                          GitHub
┌──────────────────────┐          ┌──────────────────┐
│ Money-Maker/         │  push →  │ jswillia/        │
│ ├── Dashboard.md     │  ← pull  │ money-maker      │
│ ├── Strategies/      │          │                  │
│ ├── .git/  (hidden)  │          │ (shared truth)   │
│ └── .obsidian/       │          └──────┬───────────┘
│                      │                 │
│  Obsidian reads      │          ┌──────▼───────────┐
│  these files and     │          │ Partner's        │
│  shows them as       │  push →  │ Computer         │
│  a pretty vault      │  ← pull  │ Money-Maker/     │
└──────────────────────┘          └──────────────────┘
```

**Key concept:** Obsidian doesn't know or care about git. It just reads and writes markdown files in the folder. Git tracks changes to those files and syncs them between partners. They are independent — neither interferes with the other.

---

## Repository

| Field | Value |
|---|---|
| **GitHub URL** | https://github.com/jswillia/money-maker |
| **Clone command** | `git clone https://github.com/jswillia/money-maker.git` |
| **Branch** | `main` |

---

## Setup for Jeff (Already Done)

The vault lives in your iCloud Obsidian folder:
```
/Users/jeffdev/Library/Mobile Documents/iCloud~md~obsidian/Documents/Money-Maker/
```

- Obsidian picks it up automatically (it's in the same folder as your other vaults)
- Git is already initialized with GitHub remote
- You edit in Obsidian, then push changes to GitHub

---

## Setup for Partner (New)

### Step 1: Install Prerequisites

1. **Install Obsidian** — https://obsidian.md (free)
2. **Install Git** — likely already installed. Check: open Terminal and type `git --version`
3. **Install GitHub CLI** (optional but helpful) — `brew install gh` then `gh auth login`

### Step 2: Clone the Vault

Open Terminal and run:

```bash
# Choose where you want the vault on your computer
# Example: in your home folder
cd ~

# Clone the repo
git clone https://github.com/jswillia/money-maker.git

# This creates a "money-maker" folder with the entire vault
```

### Step 3: Open in Obsidian

1. Open Obsidian
2. Click **"Open another vault"** (bottom left vault icon)
3. Click **"Open folder as vault"**
4. Navigate to the `money-maker` folder you just cloned
5. Click **Open**
6. You should see the Dashboard as the home page

### Step 4: You're Done

The vault is now on your computer. Obsidian will show all the notes, strategies, logs, and research. You can browse, edit, and add notes just like any Obsidian vault.

To stay in sync with Jeff, you'll use the git commands below.

---

## Daily Workflow: Staying in Sync

### The Golden Rule

**Always pull before you start working. Always push when you're done.**

### Before You Start Working (30 seconds)

Open Terminal, navigate to your vault folder, and pull:

```bash
cd ~/money-maker    # or wherever you cloned it
git pull
```

This downloads any changes Jeff (or the system) has made since your last pull. If there are no changes, it says "Already up to date."

### After You've Made Changes (1 minute)

After editing notes in Obsidian (updating your portfolio, logging revenue, etc.):

```bash
cd ~/money-maker
git add -A
git commit -m "Update revenue tracker for week 3"
git push
```

That's it. Three commands:
1. `git add -A` — stage all your changes
2. `git commit -m "description"` — save them with a description
3. `git push` — upload to GitHub

### Commit Message Examples

Keep them short and descriptive:
- `"Update revenue tracker for week 3"`
- `"Add new Gumroad product to catalog"`
- `"Weekly review notes - Feb 28"`
- `"Update partner portfolio numbers"`
- `"Log decision: killed Strategy 5"`

---

## What If We Edit the Same File?

This is called a **merge conflict**. It's rare if you follow the pattern below, but here's how to handle it:

### How to Avoid Conflicts (Easy)

| Jeff edits | Partner edits | No conflict |
|---|---|---|
| Strategy notes | Partner - Portfolio.md | Different files = safe |
| Revenue Tracker | Partner - Portfolio.md | Different files = safe |
| Decision Log | Partner - Portfolio.md | Different files = safe |
| Dashboard | Dashboard | **Same file = possible conflict** |

**Best practice:** Each partner primarily edits their own portfolio note and leaves strategy/system notes to Jeff (who runs Claude Code sessions). This almost eliminates conflicts.

### If a Conflict Happens

When you `git pull` and see a conflict:

```
CONFLICT (content): Merge conflict in Logs/Revenue Tracker.md
Automatic merge failed; fix conflicts and then commit the result.
```

1. Open the conflicted file in any text editor (or Obsidian)
2. Look for conflict markers:
```
<<<<<<< HEAD
Your version of the text
=======
Jeff's version of the text
>>>>>>> origin/main
```
3. Edit the file to keep what you want (remove the `<<<`, `===`, `>>>` markers)
4. Save the file
5. Then:
```bash
git add -A
git commit -m "Resolve merge conflict in Revenue Tracker"
git push
```

### Nuclear Option (If Confused)

If you get confused by a conflict and want to start fresh:

```bash
# Throw away your local changes and match GitHub exactly
git checkout -- .
git pull
```

**Warning:** This discards any changes you made that weren't pushed yet.

---

## What Gets Synced (and What Doesn't)

The `.gitignore` file controls what GitHub tracks:

### Synced (Shared Between Partners)

- All markdown notes (strategies, logs, research, guides)
- CLAUDE.md
- Dashboard.md
- `.obsidian/app.json` and `.obsidian/appearance.json` (shared settings)

### NOT Synced (Stays on Your Computer Only)

- `.obsidian/workspace.json` — your current open tabs, pane layout
- `.obsidian/plugins/` — your installed Obsidian plugins
- `.obsidian/themes/` — your Obsidian theme
- `.DS_Store` — macOS junk files

This means each partner can have their own Obsidian plugins, themes, and layout without interfering with each other.

---

## Useful Git Commands Reference

| What You Want | Command |
|---|---|
| Get latest changes | `git pull` |
| See what you've changed | `git status` |
| See the actual changes | `git diff` |
| Save and upload changes | `git add -A && git commit -m "message" && git push` |
| See commit history | `git log --oneline` |
| Undo changes to a file | `git checkout -- filename.md` |
| See who changed what | `git log --oneline -- "path/to/file.md"` |

---

## Optional: Obsidian Git Plugin (Auto-Sync)

If you want Obsidian to handle git automatically (no Terminal needed):

1. Open Obsidian Settings → Community Plugins → Browse
2. Search for **"Obsidian Git"** by Vinzent
3. Install and Enable
4. Configure:
   - **Auto pull interval:** 10 minutes
   - **Auto push interval:** 10 minutes
   - **Auto commit message:** `"vault backup: {{date}}"`
   - **Pull on startup:** Enabled

This makes the vault auto-sync every 10 minutes. You'll never need to open Terminal for git commands. Both partners can install this independently.

**Caveat:** Auto-commits create many small commits. If you prefer clean commit history, use manual git commands instead.

---

## Troubleshooting

### "Permission denied" when pushing

Your GitHub account needs collaborator access to the repo. Jeff adds you:
```bash
# Jeff runs this:
gh repo edit jswillia/money-maker --add-collaborator PARTNER_GITHUB_USERNAME
```

Or go to GitHub → repo Settings → Collaborators → Add people.

### "Your local changes would be overwritten by merge"

You have uncommitted changes and are trying to pull. Either:
```bash
# Option A: Commit your changes first, then pull
git add -A && git commit -m "save my changes" && git pull

# Option B: Stash your changes, pull, then unstash
git stash && git pull && git stash pop
```

### Obsidian shows "File not found" after pull

Obsidian sometimes takes a moment to notice new files. Close and reopen the vault, or click on the file tree to refresh.

### "Everything is messed up, help"

The nuclear reset — makes your local copy match GitHub exactly:
```bash
cd ~/money-maker
git fetch origin
git reset --hard origin/main
```

**Warning:** This deletes ALL local changes that weren't pushed. Use as last resort.

---

## How This Works with Claude Code

When Jeff runs a Claude Code session to build strategies or n8n workflows, Claude Code reads and writes files in this vault. After a session:

1. Jeff reviews the changes in Obsidian
2. Jeff pushes to GitHub:
   ```bash
   git add -A && git commit -m "Claude Code: built Kalshi weather bot" && git push
   ```
3. Partner pulls on their machine:
   ```bash
   git pull
   ```
4. Partner sees all the new/updated notes in their Obsidian

The build artifacts, strategy updates, and system changes all flow through git.
