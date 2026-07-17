# 📝 Text Processing: Manipulating Streams

### *How do I search, slice, modify, and process text streams directly from the command line?*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *Filtering large outputs and text logs*

When working on a system, you are frequently faced with massive dumps of text—system logs, lists of active connections, tabular outputs, or raw database structures. 

If you are trying to find a single error code in a 5,000-line server log, or need to extract a column of usernames from a configuration file, scrolling manually is impossible. Knowing how to use **Text Processing** tools allows you to filter, modify, and clean text dynamically using pipelines.

---

## 🚀 The Text Processing Utilities

These tools process text streams line-by-line, passing their outputs to each other using **Pipes (`|`)**.

### 1. `jq` (JSON Parser)
*   **Why it exists:** JSON is the standard language of web APIs and configuration profiles, but it is printed as single-line strings. `jq` parses and formats it.
*   **Examples:**
    ```bash
    # Pretty-print a raw JSON file
    cat api.json | jq .
    
    # Extract only the "status" value from a JSON response
    cat api.json | jq '.status'
    ```

### 2. `sed` and `awk` (Stream Editors)
*   **Why it exists:** They are lightweight, scriptable editors designed to find, replace, and print specific columns of text without opening a graphical window.
*   **When would I actually use this?** You probably won't use these on day one. But the moment you need to rename a variable across 50 configuration environment files, or extract specific usernames from a system-wide pass list, these two commands will save you hours of manual clicking and editing.
*   **Examples:**
    *   *Search & Replace (`sed`):* Replace every instance of "development" with "production" in a file:
        ```bash
        # -i               → Edit the file in-place (directly modify it instead of printing to screen)
        # s/old/new/g      → s = substitute, old = search term, new = replacement, g = do it globally (all matches per line)
        sed -i 's/development/production/g' config.env
        ```
    *   *Column Extraction (`awk`):* Print only the first column (usernames) of your system pass list:
        ```bash
        # -F:              → Use ":" as the field separator (the passwd file fields are separated by colons)
        # {print $1}       → Print only the first column (the username)
        cat /etc/passwd | awk -F: '{print $1}'
        ```

### 3. `cut`, `sort`, and `uniq` (Filter & Sort)
*   **Why it exists:** Used to extract specific characters or fields, sort outputs alphabetically or numerically, and remove duplicate entries.
*   **Examples:**
    *   *Extract characters (`cut`):* Print only characters 1 to 10 of a log line:
        ```bash
        cat log.txt | cut -c 1-10
        ```
    *   *De-duplicate (`uniq`):* Sort a list of IP logs and count the unique occurrences of each IP address:
        ```bash
        cat ip_logs.txt | sort | uniq -c
        ```

### 4. `xargs` (Pass Arguments)
*   **Why it exists:** Standard commands often output text, but other commands expect file arguments. `xargs` converts standard input lines into arguments for execution.
*   **Example:**
    ```bash
    # Find all backup files and delete them instantly
    find . -name "*.bak" | xargs rm
    ```

---

## 🚀 Next Step

Head over to **[File Utilities (07 - File Utilities.md)](07%20-%20File%20Utilities.md)** to learn how to inspect file contents, view directory structures, and package files from the terminal.
