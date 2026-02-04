# MassCode Importer (Fixed & v4 Compatible)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Maintenance](https://img.shields.io/badge/maintained-yes-green.svg)]()
[![MassCode](https://img.shields.io/badge/massCode-v4%20Compatible-purple.svg)](https://masscode.io/)

A robust command-line tool to import code snippets from **GitHub Gists** into **[massCode](https://masscode.io/)**.

> **? Why use this fork?**
> The original repository is outdated and does not generate the necessary files for MassCode v4.
> **This version fixes:**
> *   ? **Missing Files:** Correctly generates `snippets.json`, `db.json`, `tags.json`, and `folders.json`.
> *   ? **v4 Compatibility:** Generates a legacy schema compatible with the **MassCode v4 Migration** tool (fixes the `TypeError: undefined` crash).
> *   ? **Multi-file Gists:** Correctly maps Gist files to MassCode Fragments (Tabs).

## Features

*   **Seamless GitHub Sync:** Fetches all your public and secret Gists.
*   **Smart Tagging:** Automatically creates tags in massCode based on `#hashtags` found in Gist descriptions.
*   **Language Detection:** Maps file extensions to massCode languages.
*   **Migration Ready:** Generates a `db.json` perfect for restoring a full library.
*   **Portability:** Zero-dependency output (just JSON files).

## Getting Started

### Prerequisites

*   **Node.js** (v14 or higher)
*   **npm** or **yarn**

### Installation

1.  Clone this repository:
    ```bash
    git clone https://github.com/6BCC2C3896/massCode-Importer.git
    cd massCode-Importer
    ```

2.  Install dependencies:
    ```bash
    npm install
    ```

## Configuration

1.  Create a `.env` file in the project root:
    ```bash
    # Windows
    copy .env.example .env
    # Linux/Mac
    cp .env.example .env
    ```

2.  Edit `.env` with your GitHub credentials:
    ```ini
    GITHUB_TOKEN=ghp_your_classic_token_here
    GITHUB_USERNAME=your_username
    ```

    > **Token Note:** Generate a **Classic Token** [here](https://github.com/settings/tokens).
    > *   Select scope: `gist` (required to read your gists).

## Usage

Run the importer script:

```bash
npm start
```

### Output Files
The script will generate the following in your project folder:
*   `db.json`: **(Recommended)** The full database structure. Use this for "Migrating".
*   `snippets.json`: Just the snippets array. Use this for "Import JSON".
*   `tags.json`: All unique tags found.
*   `folders.json`: Folder structure based on languages.

---

## Importing into MassCode v4

There are two ways to get your data into MassCode.

### Method 1: Full Migration (Recommended)
*Best for initializing a new MassCode instance or doing a full restore.*

1.  Open **massCode**.
2.  Navigate to **Preferences** (Settings icon) > **Storage**.
3.  Click the **Migrate** button.
4.  Select the folder where your generated `db.json` is located.
5.  MassCode will read the file, convert the schema, and populate your library.

### Method 2: Direct Import
*Best for adding snippets to an existing library without overwriting.*

1.  Open **massCode**.
2.  Go to **File** > **Import** > **JSON**.
3.  Select the generated `snippets.json` file.
4.  Your Gists will appear as new snippets.

## Troubleshooting

| Error | Cause | Solution |
| :--- | :--- | :--- |
| `TypeError: ... (reading 'forEach')` | Using an incompatible `db.json` schema. | **Use this fork!** We fixed the schema to match what MassCode expects. |
| `GitHub token is missing` | `.env` file not found or empty. | Ensure `.env` exists in root and contains `GITHUB_TOKEN`. |
| `401 Unauthorized` | Invalid Token. | Regenerate your GitHub Classic Token. |

## Contributing

We welcome pull requests! Please ensure any changes to the data model (`src/model/snippet.ts`) are tested against the MassCode migration tool.

## License

MIT