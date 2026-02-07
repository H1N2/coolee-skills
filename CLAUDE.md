# CLAUDE.md - Project Guidelines

## Project Overview
This repository is a collection of efficiency skills for Claude Code, following the conventions of `JimLiu/baoyu-skills`.

## Development Guidelines
- **Runtime**: Use Bun (`npx bun`) for all scripts and executions.
- **Language**: TypeScript is preferred for all logic.
- **Naming Convention**: All skills must have the `coolee-` prefix (e.g., `coolee-my-skill`).
- **Descriptions**: All skill descriptions in `SKILL.md` must be written in the third person (e.g., "Fetches..." instead of "I fetch...").
- **Structure**: Skills are organized into categories under the `skills/` directory.

## Directory Structure
- `skills/content-skills/`: Skills related to content creation and processing.
- `skills/ai-generation-skills/`: Skills that leverage AI for generation (images, text, etc.).
- `skills/utility-skills/`: General utility and maintenance skills.

## Command Reference
- `bun install`: Install dependencies.
- `bun test`: Run tests (if applicable).
