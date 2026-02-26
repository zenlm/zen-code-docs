# Zen Code Docs

Documentation translation tool for software projects, powered by Zen LM.

Zen Code Docs automatically syncs documentation from GitHub repositories, translates technical content using Zen AI, and builds a multilingual Nextra documentation site.

## Features

- **Multi-language support**: Translate to Chinese (zh), German (de), French (fr), Russian (ru), Japanese (ja)
- **Zen AI translation**: High-quality technical document translation via Zen API
- **Nextra integration**: Generates a modern documentation site automatically
- **Git synchronization**: Keeps translations in sync with source repositories
- **Smart translation**: Preserves code blocks, links, and technical terms
- **Parallel processing**: Translates multiple languages concurrently

## Installation

```bash
npm install -g @zen/code-docs
```

## Quick Start

1. Initialize a new translation project:

   ```bash
   zen-docs init
   ```

2. Configure environment variables:

   ```bash
   cp .env.example .env
   # Edit .env and add your Zen API key
   ```

3. Sync source repository documents:

   ```bash
   zen-docs sync
   ```

4. Translate documents:

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

Initialize a new translation project with interactive configuration. Sets up project structure, copies Nextra template, and creates configuration files.

### `sync [options]`

Sync source repository documents and automatically translate changes.

- `-f, --force`: Force sync all documents (ignores previous sync records)

### `translate [options]`

Translate documents to target languages.

- `-l, --language <lang>`: Specify target language (zh, de, fr, ru, ja)
- `-f, --file <file>`: Specify single file to translate

### `config`

View and manage project configuration interactively.

### `status`

Show current project status, configuration, and environment setup.

## Configuration

```json
{
  "source": {
    "repo": "https://github.com/your-org/your-project",
    "docsDir": "docs",
    "branch": "main"
  },
  "target": {
    "languages": ["zh", "de", "fr", "ru", "ja"]
  },
  "zen": {
    "apiBase": "https://api.zenlm.org/v1",
    "model": "zenlm/zen-max"
  }
}
```

## Environment Variables

```bash
ZEN_API_KEY=your-api-key
ZEN_API_BASE=https://api.zenlm.org/v1
```

## How It Works

1. **Sync**: Clones or pulls the source repository and extracts docs
2. **Diff**: Identifies changed or new files since last sync
3. **Translate**: Sends markdown content to Zen API in parallel across languages
4. **Preserve**: Code blocks, links, and technical identifiers are passed through unchanged
5. **Build**: Generates Nextra pages with language switcher

## Links

- Models: [huggingface.co/zenlm](https://huggingface.co/zenlm)
- Docs: [zenlm.org](https://zenlm.org)

## License

Apache 2.0 — Copyright 2024 Zen LM Authors