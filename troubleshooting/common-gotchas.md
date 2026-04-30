# Common Gotchas — Symptom → Fix Lookup

> **How to use this doc:** Find your symptom in the table of contents below. Read the "Tell Claude this prompt" line. Paste it. Done.
>
> **The principle:** You don't have to memorize fixes. You just need the vocabulary to describe what you're seeing. This doc gives you the vocabulary; your AI employee does the fixing.
>
> **Last verified:** 2026-04-29.
>
> **Freshness note.** OS dialogs, plugin marketplace UIs, vendor permissions, and pricing all evolve. If a gotcha here doesn't match what you're seeing, ask your AI employee: *"Run the research-and-discernment routine on [symptom]."* The course skill researches live state and answers in the context of your setup. This doc is a starting point, not the final word.

## Table of contents

- [Top 10 course-killers (read these first)](#top-10-course-killers)
- [Install gotchas](#install-gotchas)
- [Permission gotchas (Mac and Windows)](#permission-gotchas)
- [Account / subscription gotchas](#account--subscription-gotchas)
- [Tab / mode gotchas](#tab--mode-gotchas)
- [Plugin install gotchas](#plugin-install-gotchas)
- [GitHub gotchas](#github-gotchas)
- [File path / iCloud gotchas](#file-path--icloud-gotchas)
- [Conversation / context gotchas](#conversation--context-gotchas)
- [Cross-vendor confusion (Claude vs Codex)](#cross-vendor-confusion)

---

## Top 10 course-killers

These are the gotchas most likely to make you quit. If something feels broken, check these first.

1. **You're in the wrong tab.** The Code tab is where everything in this course happens — not Chat, not Cowork. If `/plugin` doesn't autocomplete, click "Code" at the top center.
2. **You're on the Free tier.** The Code tab requires a paid plan. If you click Code and see an upgrade prompt, we recommend starting with Max at $100/month (Claude Code pricing is in flux; Max is the stable bet).
3. **Plugin install fakes success in Chat tab.** Always verify by typing `/` after install — you should see `/superpowers:*` skills. If you don't, the install was fake.
4. **GitHub 2FA is mandatory** as of May 2, 2026. Install GitHub Mobile on your phone before signup.
5. **macOS clicked "Don't Allow" on a folder permission.** Restart Claude. When prompted again, click Allow.
6. **Windows is missing Git for Windows.** The Code tab silently fails without it. Install from git-scm.com/downloads/win and restart Claude.
7. **The GitHub CAPTCHA escalated on failure.** Refresh the page. If it persists, use "Continue with Google."
8. **Verification email is in Promotions/Junk.** Check those folders before clicking "resend."
9. **You're using `CLAUDE.md` in Codex (or `AGENTS.md` in Claude).** Each tool reads a specific filename. Keep both files in sync, or copy one to the other when you switch tools.
10. **Conversation got too long.** Start a new chat. Tell the new chat: *"Read CLAUDE.md and the context folder, then catch up on where I am — I just hit a context limit."*

---

## Install gotchas

### macOS Gatekeeper blocks first launch
- **Symptom:** Double-clicking Claude.app shows *"'Claude' is an app downloaded from the Internet. Are you sure?"*
- **Root cause:** macOS quarantines newly-downloaded apps; Anthropic is a verified developer so this only appears once.
- **Fix:** Click Open. This dialog is normal on first launch and won't appear again.
- **OS:** Mac

### Windows SmartScreen warns on installer
- **Symptom:** *"Microsoft Defender SmartScreen prevented an unrecognized app from starting."*
- **Root cause:** SmartScreen sometimes flags Electron apps until reputation accrues, even with a signed installer.
- **Fix:** Click "More info" → "Run anyway."
- **OS:** Windows

### Windows Code tab silently fails without Git for Windows
- **Symptom:** Open the Code tab on Windows, pick a folder, send first message — session never starts or errors with non-obvious text.
- **Root cause:** Code tab requires `git` on PATH. macOS ships it; Windows does not.
- **Fix (before opening Code tab on Windows):** Install Git for Windows from `https://git-scm.com/downloads/win`. Restart Claude. Required, not optional.
- **OS:** Windows

### MSIX vs .exe Windows installer confusion
- **Symptom:** You found an `.msix` installer and got "Add-AppxPackage" PowerShell errors.
- **Root cause:** Two valid Windows downloads exist; the consumer `.exe` is what you want.
- **Fix:** Use the consumer Windows installer (.exe Setup) from `claude.com/download` — not the .msix enterprise package.
- **OS:** Windows

### Linux is not supported
- **Symptom:** You're on Linux, click Download, get nothing native.
- **Root cause:** Anthropic ships Claude Desktop only for macOS and Windows.
- **Fix:** Switch to a Mac or Windows machine for this course. The CLI alternative exists but isn't what we teach.
- **OS:** Linux

---

## Permission gotchas

### macOS: Claude can't access folders
- **Symptom:** Claude says it can't read or write files in your working folder.
- **Root cause:** macOS hasn't granted Claude file access yet, OR you clicked "Don't Allow" on a permission prompt earlier.
- **Tell Claude this:** *"Walk me through granting you file access on macOS. Tell me what System Settings panel to open and what permissions to toggle."*
- **Fix:** Open System Settings → Privacy & Security → Files and Folders → Claude → toggle on the relevant folders. Or for broadest access: Privacy & Security → Full Disk Access → add and enable Claude. Restart Claude.
- **OS:** Mac

### macOS: per-folder consent dialogs feel scary
- **Symptom:** Claude pops multiple "would like to access files in your X folder" dialogs during the first fetch.
- **Root cause:** macOS 14/15 (Sonoma/Sequoia) require per-folder consent; there is no global "allow everything" outside Full Disk Access.
- **Fix:** Click OK to anything Claude asks for during install and the first folder pick. macOS being careful, not Claude being broken.
- **OS:** Mac

### Windows: Controlled Folder Access blocks Claude (corporate laptops)
- **Symptom:** On a work laptop, Claude can't write to Documents or Desktop.
- **Root cause:** IT enabled Controlled Folder Access. Claude isn't on the allow-list.
- **Fix:** Ask IT to add Claude to Windows Security → Virus & threat protection → Allow an app through Controlled folder access. (If you don't have IT and you have admin yourself, you can do it from the same panel.)
- **OS:** Windows

### Permission prompts during fetch get "Deny" by reflex
- **Symptom:** You clicked Deny on the "Allow Claude to run X" prompt; Claude reports a fetch failure.
- **Root cause:** Non-technical instinct is to deny prompts as suspicious.
- **Fix:** Click Allow for every command Claude asks about during the GitHub fetch. You're approving Claude to do work *on your behalf*, not granting blanket access. To redo: tell Claude *"Try the fetch again — I'll click Allow this time."*
- **OS:** both

---

## Account / subscription gotchas

### Free tier blocks the Code tab (THE big one)
- **Symptom:** Click Code tab → see an upgrade-to-Pro prompt instead of a folder picker.
- **Root cause:** Code tab is Pro+ only. The whole course lives in the Code tab.
- **Fix (before Module 3 starts):** Open Settings (⌘, on Mac, Ctrl+, on Windows). Confirm a paid badge (Pro, Max, or Team Premium) in your Account section. If you see "Free," upgrade now. We recommend Max at $100/month — Anthropic has been flipping Claude Code between Pro ($20/mo) and Max ($100/mo) tiers, so Max is the stable bet that won't surprise you mid-course.
- **OS:** both

### Sign-in tokens expire silently
- **Symptom:** Installed Claude weeks ago, opens it for the course, gets re-prompted to log in mid-walkthrough.
- **Root cause:** Auth tokens age out. No notification before expiry.
- **Fix (Module 1 pre-flight):** Sign out and back in once before we start, just to confirm credentials still work.
- **OS:** both

### Codex Free is a trial, not a workspace
- **Symptom:** Try the Module 6 Codex tour on Free Codex and hit caps within the demo.
- **Root cause:** Codex Free is a sample; image-gen + cloud thread + computer use blow through the trial budget fast.
- **Fix:** For the Module 6 parallel-test, ChatGPT Plus ($20) is the realistic minimum. Free works for the 5-minute tour only.
- **OS:** both

---

## Tab / mode gotchas

### Three-tab UI confuses "where am I?"
- **Symptom:** Type in a tab thinking you're "in your AI employee" and get generic chat.
- **Root cause:** The Chat | Cowork | Code tabs at top center are non-obvious, and switching tabs can lose focus.
- **Fix:** Look at the top center: you want the **Code** tab highlighted for everything in this course. The first thing you do every session is click "Code."
- **OS:** both

### Chat tab fakes plugin install success
- **Symptom:** In Chat tab: *"Install Superpowers"* → Claude says "Installed!" — but slash menu doesn't show `/superpowers:*` skills.
- **Root cause:** `/plugin` is a Code-tab/CLI feature. In Chat tab, Claude hallucinates success. (Confirmed bug `anthropics/claude-code#42142`.)
- **Tell Claude this (after switching tabs):** *"List the slash commands now available in this session that begin with /superpowers:. If none appear, the install did not take."*
- **Fix:** Always switch to the Code tab before any plugin work. Verify by typing `/` after install.
- **OS:** both

### Plugins don't sync to Cowork or Remote sessions
- **Symptom:** Plugin works in Local session but not in Remote/Cowork.
- **Root cause:** Plugins load only in Local and SSH sessions.
- **Fix:** Default to Local sessions throughout the course.
- **OS:** both

---

## Plugin install gotchas

### "Did the install actually work?" — three signals
- **Tell Claude this:** *"Show me three signals that the plugin is active: (1) the slash autocomplete entries it added, (2) the /plugin Installed-tab status, (3) the output of /help."*
- This is the trust-building verification you should do after every plugin install.

### GSD requires two commands (third-party marketplace)
- **Symptom:** Asked to install GSD and got "plugin not found."
- **Root cause:** GSD lives in `jnuyens/gsd-plugin`, a community marketplace not pre-added.
- **Tell Claude this:** *"Please add the GSD plugin marketplace from jnuyens/gsd-plugin and then install the gsd plugin for me."*
- **OS:** both

### `/reload-plugins` required to activate new skills
- **Symptom:** Install succeeded but `/superpowers:*` skills don't appear in autocomplete.
- **Root cause:** Slash menu cache stale until reload.
- **Tell Claude this:** *"Run /reload-plugins and then list the new slash commands available."*
- **OS:** both

### Don't use `--dangerously-skip-permissions`
- **Warning:** If a tutorial tells you to add `--dangerously-skip-permissions`, ignore it. The Code tab handles permissions correctly without it. The flag disables ALL permission prompts globally — catastrophic for non-technical users.
- **OS:** both

---

## GitHub gotchas

### 2FA mandatory at signup (post-May 2, 2026)
- **Symptom:** Sign up, get forced through 2FA before reaching the dashboard.
- **Root cause:** GitHub enforcement extends to all new accounts.
- **Fix:** Install the **GitHub Mobile** app on your phone before Module 1. Scan QR code, tap "Approve." Don't use SMS — GitHub is phasing it out. Save your recovery codes somewhere safe (note in 1Password, screenshot in Photos, etc.).
- **OS:** both

### Arkose CAPTCHA rage-quit
- **Symptom:** Fail the rotate-the-image puzzle, get a stricter version, fail again, want to throw the laptop.
- **Root cause:** Arkose escalates difficulty on failure.
- **Fix:** Refresh the page. If it keeps escalating, switch to "Continue with Google" — bypasses the puzzle entirely.
- **OS:** both

### Verification email lands in Promotions/Junk
- **Symptom:** Wait 5 minutes for the launch code; never arrives in primary inbox.
- **Root cause:** Gmail Promotions tab; Outlook Junk folder; corporate spam filters.
- **Fix:** Check Gmail's Promotions tab and Outlook's Junk folder. If still missing after 5 min, click "Resend code" — or switch to a personal Gmail address.
- **OS:** both

### Native GitHub integration says "I can't access this repo"
- **Symptom:** Claude reports it can't read the repo even after you signed in.
- **Root cause:** You signed in but didn't connect this specific repository.
- **Tell Claude this:** *"In Claude Desktop, open Settings → Connectors → GitHub → Connect repository. Walk me through adding github.com/aiai-mastermind/your-first-ai-employee."*
- **Fix:** Settings → Connectors → GitHub → Connect repository, paste URL, authorize.
- **OS:** both

### "Clone" vs "fetch" prompt phrasing
- **Symptom:** Claude downloads files but they don't end up in your working folder.
- **Root cause:** Without the right prompt, Claude may fetch file contents into the conversation instead of writing them to disk.
- **Tell Claude this:** *"Use the filesystem MCP to copy the templates folder from the connected repo into our working directory at [path]. Don't just read the files into our chat — actually write them to disk. Confirm by listing what's now in the working folder."*
- **OS:** both

---

## File path / iCloud gotchas

### iCloud-only files won't load
- **Symptom:** Your working directory is in iCloud and Claude says files aren't loading.
- **Root cause:** iCloud sometimes keeps files cloud-only.
- **Fix:** Open Finder, navigate to your working directory. Look for the cloud icon next to file names. Right-click → "Download Now" to force local copies. Better: move the working directory to a non-iCloud location like `~/ai-employee/`.
- **OS:** Mac

### "I can't find the folder" — path confusion
- **Symptom:** Claude says it can't find a path you specified.
- **Tell Claude this:** *"Show me the absolute path of the file you're looking for. Then list everything in the directory above that path. Help me figure out where the file actually is."*
- **OS:** both

---

## Conversation / context gotchas

### Claude lost track mid-mission
- **Symptom:** Mid-Mission 1 (or 2), Claude starts contradicting earlier work, forgets the brief, or asks for info you already gave.
- **Root cause:** Conversation hit the context window limit.
- **Tell Claude this (in a NEW chat):** *"Read CLAUDE.md, AGENTS.md, the context folder, and any files in 01-strategy/. Then catch up on where we are in Mission 1 — I had to start a new chat because the old one ran out of room. Pick up from where we left off."*
- **Fix:** Periodically save progress as files (Claude can do this — *"Save a progress doc at progress.md summarizing what we've done and what's left"*). Then a new chat can resume.
- **OS:** both

---

## Cross-vendor confusion

### `CLAUDE.md` vs `AGENTS.md`
- **Symptom:** You set up your "brain file" for Claude (`CLAUDE.md`). Then you switch to Codex Desktop for the Module 6 tour. Codex doesn't see it.
- **Root cause:** Claude Desktop reads `CLAUDE.md`. Codex (and Cursor, and others) read `AGENTS.md`. Same shape, different filename.
- **Fix:** Keep both files in your project folder. Or, if you want one source of truth: keep the canonical content in `AGENTS.md` (the open standard) and have `CLAUDE.md` say *"See AGENTS.md."*
- **OS:** both

### Codex starts in Agent mode by default
- **Symptom:** Codex's first response to a casual question runs an actual command you didn't expect.
- **Root cause:** Codex's default mode is "do things" not "talk." Different from Claude Desktop.
- **Fix (Module 6 pre-flight):** Open Codex Settings and turn on "approve every action" so it asks before executing.
- **OS:** both

---

## When something isn't on this list

Claude is the help system. Tell your AI employee:

> *"I'm on Module [X] of Your First AI Employee. I'm trying to [what you're trying to do]. What's happening is [exactly what you see — error message verbatim if there is one]. I tried [whatever you tried]. Help me figure out the next step."*

That single prompt resolves 80% of unlisted issues.
