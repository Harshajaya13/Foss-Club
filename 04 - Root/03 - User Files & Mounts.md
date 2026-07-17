# 🧑 User Files & Mounts: Accessing Your Data

### *Understanding your personal sandbox space and how external drives attach to Linux.*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *Where are my personal files and flash drives?*

If you are used to Windows, your files live under `C:\Users\username`. External USB drives show up as new letters like `D:` or `E:`.

In Linux, there are no drive letters. All files—including your documents, projects, and external filesystems—must exist as folders under the single Root directory (`/`). 

This guide details your personal sandbox space and shows you where external storage drives connect to your system.

---

## 📂 The User & Mount Directories

### 1. `/home` (Your Personal Sandbox)
*   **What it is:** The directory containing home folders for all normal users. For example, if your username is `harsha`, your personal files live in:
    ```text
    /home/harsha/
    ```
    This holds your personal folders: `Downloads`, `Documents`, `Desktop`, code repositories, and configuration files.
*   **Beginner's Take:** **You own this space.** You do not need `sudo` to create, modify, or delete files inside your own `/home/username` directory. It is completely safe to edit.

---

### 2. `/root` (The Administrator's Sandbox)
*   **What it is:** The home directory for the super administrator (`root`). It is separate from the normal `/home` directory for security purposes.
*   **Beginner's Take:** You cannot open or see files inside `/root` without using `sudo`.

---

### 3. `/media` and `/mnt` (Storage Mount Points)
*   **What they are:** Since there are no drive letters, when you plug a USB flash drive or external SSD into your machine, Linux attaches (mounts) that drive's contents to a folder.
    *   **`/media`:** Used for **automatic** mounts. When you plug in a USB stick on a desktop distribution, it automatically appears as a subdirectory inside `/media/username/USB-Name`.
    *   **`/mnt`:** Used for **manual** mounts. System administrators use this folder to temporarily link external hard drives, network storage filesystems, or server mounts.

---

> [!TIP]
> **Next Step:** Head over to **[04 - Software & Applications](04%20-%20Software%20%26%20Applications.md)** to see where applications and manual compilers store software.
