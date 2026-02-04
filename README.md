# MassCode Importer (Fixed & v4 Migration Ready)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Maintenance](https://img.shields.io/badge/maintained-yes-green.svg)]()
[![MassCode](https://img.shields.io/badge/massCode-v4%20Compatible-purple.svg)](https://masscode.io/)

A specialized tool to bridge the gap between **GitHub Gists** and **[massCode v4](https://masscode.io/)**. 

> **? The Problem:** MassCode v4 lacks a reliable "Import Gist" or "Import Snippets JSON" feature.
> **? The Solution:** This tool generates a **MassCode v3 compatible storage file**. You then use MassCode v4's **"Migrate"** feature to adopt this data, instantly importing all your gists with folders, tags, and multi-file fragments intact.

## Key Fixes in this Fork
*   ? **Migration Schema:** Generates the exact legacy `db.json` schema required by the v4 migration engine.
*   ? **Fragment Mapping:** Automatically converts multi-file Gists into MassCode "Fragments" (Tabs).
*   ? **Zero-Crash logic:** Fixes the `TypeError: undefined (reading 'forEach')` common in other importers.

## Getting Started

### Prerequisites
*   **Node.js** (v14+)
*   **npm** or **yarn**

### Installation
```bash
git clone https://github.com/6BCC2C3896/massCode-Importer.git
cd massCode-Importer
npm install
```

## Configuration

1.  Create a `.env` file:
    ```ini
    GITHUB_TOKEN=ghp_your_classic_token_here
    GITHUB_USERNAME=your_username
    ```
2.  **Token Note:** Use a [Classic Token](https://github.com/settings/tokens) with the `gist` scope enabled.

## Usage

Run the generator:
```bash
npm start
```
The tool will create a `db.json` file in your project root.

---

## ? Importing into MassCode v4 (The Default Solution)

Since standard snippet import is unreliable in v4, follow these steps to use the **Migration** method:

1.  **Run this tool** to ensure `db.json` exists in your `massCode-Importer` folder.
2.  Open **massCode v4**.
3.  Go to **Preferences**.
4.  Select the **Storage** tab.
5.  Find the **Migrate** button.
6.  **Selection:** When the file picker opens, select the **`db.json`** file directly.
7.  MassCode will detect the database, convert it to the new v4 SQLite format, and your Gists will appear instantly.

## Troubleshooting

| Issue | Solution |
| :--- | :--- |
| **`TypeError: ... (reading 'forEach')`** | You are likely using an old version of the importer. This fork fixes this specifically for MassCode v4. |
| **Syntax highlighting missing** | Ensure your Gist files have proper extensions (e.g., `.js`, `.py`). |

## License
MIT