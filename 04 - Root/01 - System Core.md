# ⚙️ System Core: Where the OS Lives

### *Understanding the core files, binaries, and libraries that power the Linux system.*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *How does Linux launch basic commands?*

When you open a terminal window and type `ls`, `cd`, or `cat`, how does the computer run them? Where are those utilities stored on your disk?

When your computer boots up, how does it know how to interact with the CPU or load basic commands? This is where the core machinery lives—the brain and organs of your operating system.

In Windows, program executables are scattered inside different subdirectories under `C:\Program Files`. In Linux, the core commands are grouped inside standardized system folders so the operating system can run them immediately on boot.

---

## 📂 The Core System Folders

### 1. `/bin` and `/sbin` (System Binaries)
*   **What they are:** "Bin" stands for **binary** (compiled machine executables). These folders contain the actual programs you run in the shell.
    *   **`/bin`:** Contains essential user CLI commands that are available to all users on the system (e.g. `ls`, `cp`, `mv`, `cat`, `pwd`, `mkdir`).
    *   **`/sbin`:** "System Binaries." Contains utilities for system administration and maintenance (e.g. `fdisk` for partitions, `iptables` for firewall, `reboot`, `shutdown`). These usually require `sudo` privileges to run.
*   **Beginner's Take:** When you type `ls`, your shell searches `/bin` to find the executable file.

---

### 2. `/lib` and `/lib64` (System Libraries)
*   **What they are:** "Lib" stands for **library**. When programmers write software, they reuse shared building blocks (like graphics libraries or math algorithms) instead of coding them from scratch. 
    *   These shared blocks are stored in `/lib` (for 32-bit systems) or `/lib64` (for 64-bit systems). They are equivalent to `.dll` files on Windows or `.dylib` files on macOS.
*   **Beginner's Take:** If you install an application and it crashes on startup with the error *"missing shared library"*, it means the system cannot find a required file in `/lib`.

---

### 3. `/boot` (Bootloader Files)
*   **What it is:** Contains the crucial files required to boot your computer. This holds:
    *   **The Linux Kernel:** The central engine of the operating system.
    *   **The GRUB Bootloader:** The startup menu you see when you turn your PC on, allowing you to choose which OS to run.
*   **Beginner's Take:** **Do not touch this directory.** Deleting files in `/boot` will brick your computer and prevent your operating system from booting next time.

---

> [!TIP]
> **Next Step:** Head over to **[02 - Configuration & Logs (02 - Configuration & Logs.md)](02%20-%20Configuration%20%26%20Logs.md)** to learn where Linux stores settings and records system logs.
>
> ⬅️ Or return to **[The Filesystem Map (00 - The Filesystem Map.md)](00%20-%20The%20Filesystem%20Map.md)**.
