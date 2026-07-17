# 🔌 Terminal Multiplexers: Persistent Sessions

### *How do I run background server tasks and manage grids without losing my connection?*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *Connection drops and terminal grid limitations*

If you are logged into a remote server via SSH and running a script that takes 5 hours to finish:
*   *What happens if your home internet drops for 2 seconds?*
*   *What happens if you accidentally close your laptop lid?*

The shell session is terminated, and your script dies immediately. 

Furthermore, opening 5 terminal windows just to see logs, edit config files, and run local code creates desktop clutter. 

A **Terminal Multiplexer** solves both problems. It splits a single terminal window into a grid of panels (panes) and runs your shells inside background sessions that survive connection drops.

```
+-------------------------------------------------+
|  Multiplexer Session (survives disconnects)     |
|                                                 |
|   +-------------------+---------------------+   |
|   |  Pane 1 (Editor)  |  Pane 2 (Server Run)|   |
|   |  [Editing code]   |  [Starting server]  |   |
|   |                   |                     |   |
|   +-------------------+---------------------+   |
|   |  Pane 3 (Logs Tracker)                  |   |
|   |  [Tracking server errors]               |   |
|   +-----------------------------------------+   |
+-------------------------------------------------+
```

---

## 🚀 The Choices: Multiplexer Utilities

### 1. `tmux` (The Industry Standard)
*   **What it is:** The classic, lightweight terminal multiplexer pre-configured on almost every Unix server in the world.
*   **Why it exists:** Built in 2009, it is highly stable and resource-efficient. It uses keyboard prefix commands (e.g. `Ctrl + B`) to control panes and sessions.
*   **Good for:** Server administrators and DevOps engineers who configure remote systems daily.

### 2. `Zellij` (The Modern Rust Alternative)
*   **What it is:** A modern, visual multiplexer written in Rust.
*   **Why it exists:** Unlike `tmux` which requires memorizing shortcuts, Zellij displays an interactive help bar at the bottom showing active commands. It supports layouts, tab panels, and float windows out-of-the-box.
*   **Good for:** Users who want a visual, mouse-supporting grid system without configuration.

---

## 🛠️ Concepts & Workflow (Using Tmux)

### 1. Sessions, Windows, and Panes
*   **Session:** An active workspace. You can have multiple independent sessions running in the background.
*   **Window:** A screen tab inside your session.
*   **Pane:** A visual split (vertical or horizontal) inside a window.

### 2. Core Commands
*   **Create session:** Start a new background workspace named "build":
    ```bash
    tmux new -s build
    ```
*   **Detach from session:** Disconnect from the workspace to close your window safely while keeping scripts running. Press:
    ```text
    Ctrl + B, then D
    ```
*   **Reattach to session:** Connect back to your background workspace later:
    ```bash
    tmux attach -t build
    ```
*   **List sessions:** See what sessions are currently active in the background:
    ```bash
    tmux ls
    ```
