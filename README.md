# massCode Importer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

massCode-Importer is a command-line tool designed to simplify the process of importing code snippets from your GitHub
Gists into [massCode](https://masscode.io/), a lightweight and cross-platform code snippet manager.

This tool converts your Gists into massCode-compatible snippets and tags for easy organization and access. It supports generating a **v3-compatible `db.json`** which allows for seamless migration into **massCode v4**.

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
- [Usage](#usage)
- [Importing into MassCode](#importing-into-masscode)
- [License](#license)

## Features

- Import code snippets from GitHub Gists into massCode.
- Automatically create tags based on the hashtags in your Gist descriptions.
- Convert Gist files into massCode snippet content (mapped to Fragments/Tabs).
- **Outputs multiple formats:**
    - `db.json` (Full database structure, ideal for Migration).
    - `snippets.json` (Raw snippets array).
    - `tags.json` and `folders.json`.

## Getting Started

### Prerequisites

Before you begin, make sure you have the following prerequisites installed on your system:

- [Node.js](https://nodejs.org/) (>= 14.0.0)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/) package manager

### Installation

1. Clone the repository:

```shell
git clone https://github.com/YourUsername/massCode-Importer.git
```

2. Change to the project's directory:

```shell
cd massCode-Importer
```

3. Install the required dependencies using npm or yarn:

```shell
npm install
# or
yarn install
```

## Usage

To use `massCode-Importer`, follow these steps:

1. Make sure you have set up your GitHub Gists with the necessary code snippets and descriptions.

2. Create a `.env` file in the project directory and add your GitHub token:

```shell
GITHUB_TOKEN=your_github_token_here
GITHUB_USERNAME=your_github_username_here
```

Replace `your_github_token_here` with your GitHub personal access token and `your_github_username_here` with your
GitHub username. Follow this [link](https://github.com/settings/tokens) to create the Classic Token. Select the `gist`
scope.

3. Run the importer:

```shell
npm start
```

The importer will fetch your GitHub Gists and generate the files in the project root.

## Importing into MassCode

### For MassCode v4 (Recommended)
This tool generates a `db.json` file compatible with the MassCode v3 schema, which the v4 Migration tool expects.

1. Open **massCode**.
2. Go to **Preferences > Storage**.
3. Click **Migrate**.
4. Select the folder containing your generated `db.json`.
5. MassCode will process the file and import all snippets, folders, and tags.

### Alternate Method (JSON Import)
You can also import just the snippets:
1. Open **massCode**.
2. Go to **File > Import > JSON**.
3. Select the generated `snippets.json`.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
