# Coolee Skills

A collection of efficiency skills for Claude Code, following the conventions and standards of `JimLiu/baoyu-skills`.

## Overview

This repository provides a curated set of skills designed to enhance your Claude Code workflow, covering content creation, AI generation, and utility automation tasks.

## Installation

To use these skills with Claude Code:

1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/coolee-skills.git
   ```

2. Follow the Claude Code documentation to add local skills to your configuration.

## Skills

### Content Skills

#### **coolee-leijun-speech**
Transforms any topic or text into a compelling Lei Jun-style keynote speech with data-driven narratives, grand storytelling, and emotional resonance. Perfect for product launches, presentations, and marketing content.

**Features:**
- Data-driven narratives with precise numbers and comparisons
- Grand storytelling with emotional connection
- Professional terminology creation
- Three-act structure (problem → solution → value reveal)
- Signature Lei Jun catchphrases and sentence patterns
- Outputs in Chinese (Simplified) by default

**Usage:**
- "用雷军风格写一个关于[主题]的演讲稿"
- "Write a Lei Jun-style speech about [topic]"
- "Convert this text to a Lei Jun keynote speech"

### Utility Skills

#### **coolee-claudian-updater**
Automatically updates the Claudian plugin for Obsidian by checking the latest version from GitHub and downloading updated files.

**Features:**
- Auto-detects Obsidian vault and Claudian plugin location
- Checks current vs. latest version from GitHub releases
- Creates automatic backups before updating
- Downloads and installs updates safely
- Provides rollback capability

**Usage:**
- "Update my Claudian plugin"
- "Check if Claudian needs updating"
- "Upgrade Claudian to the latest version"

## Development

See [CLAUDE.md](./CLAUDE.md) for development guidelines and project conventions.

**Key guidelines:**
- **Runtime**: Use Bun (`npx bun`) for all scripts and executions
- **Language**: TypeScript is preferred for all logic
- **Naming**: All skills must have the `coolee-` prefix (e.g., `coolee-my-skill`)
- **Descriptions**: All skill descriptions in `SKILL.md` must be written in the third person
- **Structure**: Skills are organized into categories under the `skills/` directory

## Directory Structure

```
coolee-skills/
├── skills/
│   ├── content-skills/          # Content creation and processing
│   │   └── coolee-leijun-speech/
│   ├── ai-generation-skills/    # AI-powered generation tools
│   └── utility-skills/          # General utility and maintenance
│       └── coolee-claudian-updater/
├── CLAUDE.md                    # Project guidelines and conventions
└── README.md                    # This file
```

## Contributing

Contributions are welcome! Please ensure:
1. Your skill follows the `coolee-` naming convention
2. Documentation is clear and uses third-person descriptions
3. Code follows the TypeScript/Bun conventions
4. Skills are placed in the appropriate category directory

## Roadmap

Planned skills:
- AI image generation tools
- Document processing utilities
- Version control automation
- More content creation assistants

## License

MIT

## Acknowledgments

Inspired by [JimLiu/baoyu-skills](https://github.com/JimLiu/baoyu-skills) - Special thanks for the excellent skill structure and conventions.
