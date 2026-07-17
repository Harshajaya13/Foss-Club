# 🛠️ Software & Applications: The Installation Hub

### *Where does Linux install user software and package libraries?*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *Where do applications go when installed?*

In Windows, third-party applications are installed inside `C:\Program Files\Application-Name`. This contains the app's executables, assets, libraries, and logs in one block.

Linux takes a different approach: **it groups files by type rather than by application.** 

When you install a tool, its executable binary goes into a "binary" folder, its library files go into a "library" folder, and its help manuals go into a "manual" folder. This guide shows you where user applications live and how they are structured.

---

## 📂 The Application Folders

### 1. `/usr` (Unix System Resources)
*   **What it is:** The **largest** and most important directory on a Linux machine. It contains user-installed applications, compiler libraries, and development tools. 
*   **The Key Subfolders:**
    *   **`/usr/bin`:** Where the executables of almost all user packages (like Python, Git, GCC, or Node.js) are placed.
    *   **`/usr/lib`:** Shared library blocks required by user applications.
    *   **`/usr/local`:** **This is the sandbox for compiling code manually.** When you build software from source, it is placed in `/usr/local` (e.g. `/usr/local/bin` for executables) so it never overwrites verified system files in `/usr/bin`.
    *   **`/usr/include`:** Header files (`.h`) used for compiling C/C++ projects.

---

### 2. `/opt` (Optional Applications)
*   **What it is:** A directory reserved for large, third-party proprietary software (e.g. Google Chrome, VS Code, Slack, or Spotify).
*   **Why it exists:** These applications do not follow the standard Linux layout of splitting binaries and libraries. Instead, they bundle all their files inside a single folder (e.g., `/opt/google/chrome`), keeping them completely isolated.

---

### 3. `/srv` and `/snap`
*   **`/srv` (Service Data):** Contains server data served to remote users (like FTP folders or raw web files).
*   **`/snap` (Snap Containers):** Created by Ubuntu to store containerized Snap packages, isolating them from the rest of the host system.

---

> [!TIP]
> **Next Step:** Head over to **[05 - Virtual Systems (05 - Virtual Systems.md)](05%20-%20Virtual%20Systems.md)** to explore how the Linux kernel interfaces with active hardware and running memory.
>
> ⬅️ Or return to **[The Filesystem Map (00 - The Filesystem Map.md)](00%20-%20The%20Filesystem%20Map.md)**.
