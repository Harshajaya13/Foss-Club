# ⚙️ System Monitoring: Tracking Resource Health

### *Why is my server running slow? How do I track down memory leaks and disk space fillers?*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *Visualizing system metrics without desktop managers*

On headless servers, remote cloud instances, or developer workstations, you need to understand resource bounds:
*   *Which application is consuming 99% of my CPU?*
*   *Do I have memory leaks filling up my RAM?*
*   *Why did my Nvidia GPU training run run out of memory (OOM)?*
*   *What folder is filling up my disk storage partition?*

Linux tracks these metrics inside virtual system files, but reading them raw is challenging. System monitoring utilities translate these statistics into live dashboards.

---

## 🚀 The Monitoring Toolkit

Here are the primary system resource diagnostics utilities developers run:

### 1. `htop` (Interactive Process Monitor)
*   **Why it exists:** A visual upgrade to the standard `top` command. It lists all active processes, CPU cores loads in colored bars, and memory pools.
*   **Good for:** Killing frozen applications and sorting processes by CPU or memory usage.
*   **Key command:** Press `F6` to sort processes, or `F9` to terminate (kill) a selected task.

### 2. `btop` (The Modern Terminal Dashboard)
*   **Why it exists:** An extremely responsive dashboard displaying detailed widgets for CPU, RAM, Network speeds, Disks usage, and active Process hierarchies in a single screen.
*   **Good for:** Users who want a terminal monitoring center that is visually striking and detailed.

### 3. `nvtop` (Neat Visual GPU Monitor)
*   **Why it exists:** Monitors graphics card (GPU) metrics. It displays GPU processor loads, memory consumption, temperature curves, and active CUDA processes.
*   **Good for:** AI/ML engineers running model training scripts on GPUs (Nvidia/AMD).

### 4. `ncdu` (NCurses Disk Usage Analyzer)
*   **Why it exists:** Analyzes directories to locate file space leaks. It displays folders sorted by size, letting you navigate directories inside your terminal to locate large logs or caches.
*   **Good for:** Cleaning up disk storage space.
*   **Example:**
    ```bash
    # Scan current folder directory sizes
    ncdu
    ```

### 5. `duf` (Disk Usage Utility)
*   **Why it exists:** A color-coded alternative to `df`. It displays system storage partitions, mount points, and usage percentages.
