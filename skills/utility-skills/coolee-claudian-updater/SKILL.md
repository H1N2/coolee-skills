---
name: claudian-updater
description: Automatically update the Claudian plugin for Obsidian by checking the latest version from GitHub and downloading updated files. Use when the user wants to update Claudian, check for Claudian updates, or mentions "update Claudian plugin" or "upgrade Claudian".
---

# Claudian Updater

This Skill helps you automatically update the Claudian plugin for Obsidian to the latest version from GitHub.

## What it does

1. Locates your Obsidian installation and Claudian plugin directory
2. Checks the current installed version
3. Fetches the latest version from GitHub releases
4. Compares versions and determines if an update is needed
5. Downloads and installs the update with automatic backup
6. Provides clear feedback on the update process

## Quick start

Simply ask:
- "Update my Claudian plugin"
- "Check if Claudian needs updating"
- "Upgrade Claudian to the latest version"

## Instructions

### Step 1: Locate Obsidian and Claudian plugin

1. **Ask the user for the Obsidian vault path** or attempt to find it automatically:
   - Windows: Check `%APPDATA%\Obsidian` or common vault locations
   - macOS: Check `~/Library/Application Support/obsidian`
   - Linux: Check `~/.config/obsidian`

2. **Locate the Claudian plugin directory**:
   - Path pattern: `[vault]/.obsidian/plugins/claudian/`
   - Verify the directory contains `manifest.json`, `main.js`, and `styles.css`

3. If automatic detection fails, ask the user to provide the full path to their Obsidian vault.

### Step 2: Read current version

1. Read the `manifest.json` file from the Claudian plugin directory
2. Extract the `version` field value (e.g., "1.2.3")
3. Display the current version to the user

Example:
```bash
# Read manifest.json
cat "[vault]/.obsidian/plugins/claudian/manifest.json"
```

Parse the JSON and extract:
```json
{
  "version": "1.2.3"
}
```

### Step 3: Fetch latest version from GitHub

1. Use the GitHub API to get the latest release information:
   - API endpoint: `https://api.github.com/repos/YishenTu/claudian/releases/latest`
   - Extract the `tag_name` field (e.g., "v1.2.4" or "1.2.4")

2. Normalize version strings by removing 'v' prefix if present

Example:
```bash
# Fetch latest release info
curl -s https://api.github.com/repos/YishenTu/claudian/releases/latest
```

### Step 4: Compare versions

1. Compare the current version with the latest version
2. Determine if an update is needed:
   - If versions match: Inform user they're up to date
   - If latest > current: Proceed with update
   - If current > latest: Warn that local version is newer (unusual case)

3. Display both versions clearly to the user

### Step 5: Backup existing files (if updating)

Before downloading new files, create a backup:

1. Create a backup directory: `[vault]/.obsidian/plugins/claudian/backup-[timestamp]/`
2. Copy the three files to the backup directory:
   - `main.js` → `backup-[timestamp]/main.js`
   - `manifest.json` → `backup-[timestamp]/manifest.json`
   - `styles.css` → `backup-[timestamp]/styles.css`

3. Confirm backup was successful before proceeding

Example:
```bash
# Create backup
mkdir -p "[vault]/.obsidian/plugins/claudian/backup-20260207-143022"
cp "[vault]/.obsidian/plugins/claudian/main.js" "[vault]/.obsidian/plugins/claudian/backup-20260207-143022/"
cp "[vault]/.obsidian/plugins/claudian/manifest.json" "[vault]/.obsidian/plugins/claudian/backup-20260207-143022/"
cp "[vault]/.obsidian/plugins/claudian/styles.css" "[vault]/.obsidian/plugins/claudian/backup-20260207-143022/"
```

### Step 6: Download updated files

1. Download the three required files from the latest GitHub release:
   - `main.js`: `https://github.com/YishenTu/claudian/releases/download/[version]/main.js`
   - `manifest.json`: `https://github.com/YishenTu/claudian/releases/download/[version]/manifest.json`
   - `styles.css`: `https://github.com/YishenTu/claudian/releases/download/[version]/styles.css`

2. Save each file to a temporary location first
3. Verify each download completed successfully (check file size > 0)

Example:
```bash
# Download files
curl -L -o /tmp/main.js "https://github.com/YishenTu/claudian/releases/download/v1.2.4/main.js"
curl -L -o /tmp/manifest.json "https://github.com/YishenTu/claudian/releases/download/v1.2.4/manifest.json"
curl -L -o /tmp/styles.css "https://github.com/YishenTu/claudian/releases/download/v1.2.4/styles.css"
```

### Step 7: Install updated files

1. Move the downloaded files to the plugin directory, replacing the old files:
   - `/tmp/main.js` → `[vault]/.obsidian/plugins/claudian/main.js`
   - `/tmp/manifest.json` → `[vault]/.obsidian/plugins/claudian/manifest.json`
   - `/tmp/styles.css` → `[vault]/.obsidian/plugins/claudian/styles.css`

2. Verify each file was copied successfully

Example:
```bash
# Install new files
mv /tmp/main.js "[vault]/.obsidian/plugins/claudian/main.js"
mv /tmp/manifest.json "[vault]/.obsidian/plugins/claudian/manifest.json"
mv /tmp/styles.css "[vault]/.obsidian/plugins/claudian/styles.css"
```

### Step 8: Verify installation

1. Read the new `manifest.json` to confirm the version was updated
2. Check that all three files exist and have reasonable file sizes
3. Display success message with:
   - Old version number
   - New version number
   - Backup location
   - Instruction to restart Obsidian

### Step 9: Provide restart instructions

Inform the user:
```
✅ Claudian plugin successfully updated from v1.2.3 to v1.2.4

Backup saved to: [vault]/.obsidian/plugins/claudian/backup-20260207-143022/

⚠️  Please restart Obsidian for the changes to take effect.
```

## Error handling

Handle these common scenarios:

1. **Obsidian vault not found**: Ask user to provide the vault path manually
2. **Claudian plugin not installed**: Inform user and offer installation instructions
3. **Network errors**: Provide clear error message and suggest checking internet connection
4. **Download failures**: Keep backup intact, don't delete old files
5. **Permission errors**: Suggest running with appropriate permissions or checking file ownership
6. **GitHub API rate limits**: Inform user and suggest waiting or using authentication

If any error occurs after backup is created, inform the user that their original files are safe in the backup directory.

## Rollback procedure

If the user wants to rollback to the previous version:

1. Locate the most recent backup directory
2. Copy files from backup back to the plugin directory
3. Confirm rollback was successful
4. Remind user to restart Obsidian

## Best practices

- Always create a backup before updating
- Verify downloads before replacing files
- Check file sizes to ensure downloads completed
- Provide clear feedback at each step
- Never delete backups automatically
- Handle version string variations (with/without 'v' prefix)

## Platform considerations

### Windows
- Use proper path separators: `\` or `/` (both work)
- Common vault locations: `%USERPROFILE%\Documents\ObsidianVault` or `%APPDATA%\Obsidian`

### macOS
- Vault locations: `~/Documents/ObsidianVault` or `~/Library/Mobile Documents/iCloud~md~obsidian`

### Linux
- Vault locations: `~/Documents/ObsidianVault` or `~/.config/obsidian`

## Example usage

**Scenario 1: Successful update**
```
User: "Update my Claudian plugin"