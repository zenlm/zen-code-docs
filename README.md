# Zen Code Docs — Multilingual Documentation Builder

A tool for syncing and translating technical documentation into multiple languages, with AI-powered translation via Zen models and a Nextra-based documentation site.

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org/)

## Features

- **GitHub sync**: Automatically pulls documentation from any GitHub repository
- **AI translation**: High-quality technical translation via Zen models (preserves code blocks, links, and formatting)
- **Multi-language**: Supports Chinese (zh), German (de), French (fr), Russian (ru), Japanese (ja)
- **Nextra docs site**: Generates a modern Next.js documentation site with language switching
- **Parallel processing**: Translates multiple languages concurrently
- **Incremental sync**: Tracks changes and only retranslates updated files

## Installation

```bash
npm install -g @zen/code-docs
```

## Quick Start

1. Initialize a project:

   ```bash
   zen-docs init
   ```

2. Configure environment variables:

   ```bash
   cp .env.example .env
   # Edit .env — set ZEN_API_KEY and source repo URL
   ```

3. Sync source documentation:

   ```bash
   zen-docs sync
   ```

4. Translate:

   ```bash
   zen-docs translate
   ```

5. Start the documentation site:

   ```bash
   npm install
   npm run dev
   ```

## Commands

### `init`

Initialize a new translation project. Sets up directory structure, Nextra template, and config files.

### `sync [options]`

Sync documentation from the source GitHub repository.

- `-f, --force` — Force sync all documents (ignore previous sync records)

### `translate [options]`

Translate documents to target languages.

- `-l, --language <lang>` — Target a specific language (zh, de, fr, ru, ja)
- `-f, --file <file>` — Translate a single file

### `config`

View and manage project configuration interactively.

### `status`

Show current project status and environment setup.

## Configuration

`translation.config.json` (created during `init`):

```json
{
  "name": "my-docs",
  "sourceRepo": "https://github.com/your-org/your-repo.git",
  "docsPath": "docs",
  "sourceLanguage": "en",
  "targetLanguages": ["zh", "de", "fr", "ru", "ja"],
  "outputDir": "content"
}
```

## Environment Variables

```env
# Required: Zen API key
ZEN_API_KEY=your_api_key

# Optional: API endpoint (defaults to local vLLM)
ZEN_BASE_URL=http://localhost:8000/v1
ZEN_MODEL=zenlm/zen-coder
ZEN_MAX_TOKENS=4000
```

## Project Structure

After initialization:

```
├── content/
│   ├── en/           # Source language (synced from repo)
│   ├── zh/           # Chinese translations
│   ├── de/           # German translations
│   ├── fr/           # French translations
│   └── ru/           # Russian translations
├── app/              # Next.js app directory
│   ├── [lang]/       # Dynamic language routing
│   └── layout.tsx
├── .source-docs/     # Raw synced documentation
├── translation.config.json
├── translation-changelog.json
├── last-sync.json
└── package.json
```

## How It Works

1. **Sync** — Clones/updates the source repository and detects changed files
2. **Parse** — Markdown is parsed while preserving structure and metadata
3. **Translate** — Content is segmented and translated via Zen models, with smart handling of code blocks and technical terms
4. **Generate** — Translated content is organized into a Nextra multilingual docs site
5. **Serve** — Next.js serves the documentation with language switching

## Links

```bash
npm install
npm run build
npm run dev   # watch mode
npm test
```

## Links

- **Zen LM**: https://zenlm.org
- **Models**: https://huggingface.co/zenlm
- **GitHub**: https://github.com/zenlm
- **Hanzo AI**: https://hanzo.ai

## License

Apache 2.0
