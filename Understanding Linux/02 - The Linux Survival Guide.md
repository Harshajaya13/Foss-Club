# 🚲 The Linux Survival Guide

### *The absolute bare-minimum rules and instincts to survive and troubleshoot in the terminal.*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Mindset: The Bicycle vs. The Race Bike

When you first install Linux, it is easy to look at customized desktop screenshots (race bikes) and think you need to build that immediately. 

But you cannot ride a race bike if you don't know how to balance. 

Think of basic terminal navigation (moving files, editing text) as a **simple bicycle**. It is slower, it has no fancy gear selectors, and it is basic—but the balance you learn on it is identical. Once you know how to balance, you can step up to any race bike (Docker containers, custom tiling window managers, servers) without falling over.

This guide contains the rules, concepts, and self-help recovery procedures you need to navigate the command line with confidence.

---

## 🛑 1. The 3 Golden Rules of System Survival

Linux has no safeguards. Unlike Windows or macOS, which pop up warnings saying *"Are you sure?"*, Linux assumes you are an expert and will execute *exactly* what you type—even if it destroys the entire system.

### ⚠️ Rule 1: Never paste commands you don't understand

If you copy a command from a forum or website to solve a bug, check what each word does first. A common internet prank is telling beginners to run:

```bash
# WARNING: Do NOT run this!
rm -rf /
```

Here is what this command actually does:
*   `rm` = remove files
*   `-r` = recursively (delete folders and their contents)
*   `-f` = force (don't ask for permission and ignore warnings)
*   `/` = the root folder (your entire hard drive)

> [!WARNING]
> **Executing this deletes every single file on your system and your hard drive instantly.**

---

### 🔑 Rule 2: Respect the power of `sudo` (Superuser Do)

`sudo` is the equivalent of "Run as Administrator." It bypasses all system locks and modifications blocks.

If a command fails and the system says `Permission denied`, **don't immediately prefix it with `sudo`.** Ask yourself: *Why is it denied? Am I trying to edit a system config I shouldn't be touching?* 

> [!CAUTION]
> **Only use `sudo` when installing software or editing global configurations. Never use it to run normal scripts or build code.**

---

### 📦 Rule 3: Don't run arbitrary installer scripts

Many tools tell you to download and run setup scripts directly from their website:

```bash
# Be extremely careful with this pattern:
curl -sSL https://some-website.com/install.sh | sh
```

This downloads a raw shell file from the web and executes it directly on your processor. If the website gets hacked, the script could deploy malware.

> [!WARNING]
> **Only run setup pipelines from verified, trusted open-source vendors. Verify the script contents before pipe-linking to your shell.**

---

## 🔍 2. The Survival Instinct: How to Help Yourself

When something goes wrong, you do not need to search Google immediately. Linux has built-in help manuals.

### 💡 1. The `--help` Flag (Quick Cheat Sheet)

Almost every CLI command has a built-in helper menu showing you its arguments:

```bash
# Print a quick list of options for the grep command
grep --help
```

### 📖 2. The `man` Command (The Official Manual)

If you want to read the full, detailed manual for a tool:

```bash
# Open the system documentation manual page for the cd command
man cd
```

*(Press `q` to exit the manual reader.)*

### ⚠️ 3. Read the Error Message (It is not a black box)

When a command fails, Linux prints a message explaining *why*. Read it instead of closing the window:

*   ❌ **`Command not found`:** The software is not installed, or you misspelled it.
*   ❌ **`Permission denied`:** You are trying to read or modify a file owned by the administrator. Use `sudo` or check file ownership.
*   ❌ **`No such file or directory`:** You typed a filename or path that doesn't exist. Check your spelling using `ls`.

---

## ⚙️ 3. Configuration: Where Settings Live

Beginners often get confused about where Linux saves settings because there is no central system Registry app like in Windows.

> **In Linux, everything is a text file.** 

User application settings are stored in your home folder (`~/`):

*   📁 **`~/.config/`**: The standard directory where modern apps (Starship, Neovim, Kitty) store their settings in folders.
*   📄 **`~/.bashrc` / `~/.zshrc`**: Configuration files that load your personal environment settings every time you open a terminal shell.
*   🗺️ **The `$PATH` Variable:** A list of system directory folders. When you type `ls`, your shell searches these folders to locate the executable file. If you break this variable, your terminal won't find basic commands!

---

## 🩹 4. Recovery: What to Do When You Break Things

The biggest fear beginners have is: *"I broke something, now I need to wipe my computer and reinstall Linux."*

**Almost everything can be fixed without reinstalling.** Keep these recovery strategies in mind:

### 🛠️ Scenario A: You broke your shell config (`PATH` is broken)

If you edited `.bashrc` or `.zshrc` and now every basic command (like `ls` or `nano`) says `Command not found`:

*   *Why it happened:* You accidentally wiped or broke your `$PATH` environment variable.
*   *The Recovery:* Since the shell doesn't know where commands are, call the absolute path to your editor to open and fix the file:
    ```bash
    /usr/bin/nano ~/.bashrc
    ```
    (Or `/usr/bin/nano ~/.zshrc`). Delete the broken lines, save, close the terminal, and reopen it!

### 🛠️ Scenario B: You accidentally deleted a project file

If you are inside a Git repository, don't close your shell! Restore the file instantly:

```bash
git checkout -- file_name.py
```

### 🛠️ Scenario C: The terminal window fails to launch

If you misconfigured your terminal settings or graphics themes and the app crashes on startup, open a standard TTY command-line prompt. Press:

```text
Ctrl + Alt + F3
```

This switches you to a full-screen, hardware-rendering text prompt where you can log in, edit configuration files, or reinstall packages. Press `Ctrl + Alt + F2` or `F1` to return to your normal desktop.

---

> [!TIP]
> **Next Step:** Now that you know how to balance, keep yourself safe, and recover when things break, head over to **[The Linux Roadmap (01 - The Roadmap.md)](../Building%20Your%20Foundation/01%20-%20The%20Roadmap.md)** to locate your career path and start building your foundation.
