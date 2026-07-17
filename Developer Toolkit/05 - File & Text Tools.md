# 📝 File & Text Utilities

### *How do I view, edit, parse, and package files directly from the command line?*

> [!IMPORTANT]
> **"Clarity before Complexity. Don't learn everything—learn what matters for your journey."**

---

## ❓ The Problem: *Working with structured text in the terminal*

When working on code or maintaining servers, you frequently inspect system config profiles, scan JSON APIs, replace text patterns in batch logs, or compress project directories.

Standard tools like `cat` simply print raw, uncolored text, which is hard to scan. Extracting deep keys from a 10,000-line JSON payload without a visual interface is frustrating. Knowing how to leverage text filters and parsers allows you to handle files inside the terminal shell instantly.

---

## 🚀 The File and Text Utilities

### 1. `bat` (A Colored `cat`)
*   **Why it exists:** An alternative to `cat` that adds automatic programming syntax highlighting, line numbers, and Git integration (highlighting modified lines).
*   **Example:**
    ```bash
    # View code file with syntax coloring
    bat script.py
    ```

### 2. `jq` (Command-Line JSON Parser)
*   **Why it exists:** A lightweight processor designed to parse, filter, slice, and map JSON text.
*   **Example:**
    ```bash
    # Pretty-print a raw JSON file
    cat api_response.json | jq .
    
    # Extract only the "status" value from a JSON dictionary
    cat api_response.json | jq '.status'
    ```

### 3. `sed` and `awk` (Stream Editors)
*   **Why it exists:** Command-line text manipulators used to find, replace, filter, and modify text streams in bulk.
*   **Examples:**
    *   *Search and Replace:* Change every occurrence of "localhost" to "127.0.0.1" inside a text file instantly:
        ```bash
        sed -i 's/localhost/127.0.0.1/g' config.env
        ```
    *   *Filter Columns:* Print only the first column (usernames) of your system pass file:
        ```bash
        cat /etc/passwd | awk -F: '{print $1}'
        ```

### 4. `tar` and `zip` (Archivers)
*   **Why it exists:** Used to package multiple files into a single archive directory for backup or storage transmission.
*   **Examples:**
    *   *Create tarball:* Package a project folder into a `.tar.gz` archive:
        ```bash
        tar -czvf project.tar.gz project/
        ```
    *   *Extract tarball:* Extract compressed archive contents:
        ```bash
        tar -xzvf project.tar.gz
        ```
