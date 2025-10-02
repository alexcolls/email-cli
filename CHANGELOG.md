# Changelog

All notable changes to Email CLI will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2025-10-02

### Added
- 📤 Email sending functionality with SMTP support
  - Send emails using Gmail, Outlook, SendGrid, or other SMTP providers
  - Interactive and command-line send modes
  - Multi-line body support
  - Reply-To header using temporary email address
  - Python-based SMTP implementation for cross-platform compatibility
- ✨ Partial matching support for `email use` command
  - Match emails by username prefix
  - Smart matching with exact match priority
  - Multiple match detection and warnings
- ✨ Professional installation script (`install.sh`)
  - Automatic OS detection (Linux, macOS)
  - Shell detection (bash, zsh)
  - Dependency checking and installation (curl, jq, python3)
  - Symlink creation to `~/.local/bin/`
  - PATH configuration with automatic shell config updates
  - Colored output and progress indicators
  - Installation logging for troubleshooting
- 📝 Configuration management
  - `.env.sample` file with SMTP configuration examples
  - Support for multiple email providers (Gmail, Outlook, SendGrid, Mailgun)
  - Environment variable loading
  - Secure local credential storage in `~/.config/tempmail/.env`
- ♻️ Renamed command from `tempmail` to `email` for simpler usage
  - More intuitive command name
  - Easier to type and remember
- 📝 Added `.gitignore` file for repository cleanliness

### Changed
- Updated README.md with comprehensive documentation
  - Email sending instructions
  - SMTP configuration guide
  - Free provider options and setup steps
  - Enhanced command reference with aliases
  - Installation methods (install.sh, manual, alias)
  - Updated examples with send functionality
  - Version bumped to 1.1.0 in documentation

### Technical Details
- Script version: 1.1.0
- Core API: 1secmail.com for receiving emails
- SMTP support: Python's smtplib for sending
- Data storage: JSON-based in `~/.config/tempmail/`
- Dependencies: bash 4.0+, curl, jq, python3

## [0.0.1] - 2025-10-01

### Added
- 🎉 Initial release of Email CLI
- ✨ Temporary email creation using 1secmail.com API
  - Random email name generation with adjectives and nouns
  - Custom email name support
  - Domain selection from available domains
- 📋 Email list management
  - List all temporary emails with creation timestamps
  - Current email indicator
  - JSON-based storage in `~/.config/tempmail/emails.json`
- 📬 Inbox checking functionality
  - Check current or specific email inbox
  - Display message list with ID, from, subject, and date
  - Real-time message fetching via API
- 📖 Email reading capability
  - Read full email content by ID
  - Display headers and text body
  - Support for current or specific email
- 🔧 Email management commands
  - `create` - Create new temporary email
  - `list` - List all stored emails
  - `inbox` - Check inbox for messages
  - `read` - Read specific email by ID
  - `use` - Set current active email
  - `current` - Show current email
  - `delete` - Remove email from list
  - `clear` - Delete all emails
  - `help` - Show help message
- 🎨 Colored CLI output
  - Color-coded messages (green for success, red for errors, blue for info, yellow for warnings)
  - Emoji indicators for better UX
- 💾 Data persistence
  - Local storage in `~/.config/tempmail/`
  - Current email tracking
  - Email list with metadata (username, domain, creation date)

### Technical Details
- Written in Bash with JSON parsing via jq
- API integration with 1secmail.com
- Local data directory: `~/.config/tempmail/`
- No external dependencies beyond bash, curl, and jq
- Executable script: `email` (originally `tempmail`)

---

## Version Number Guide
- **0.0.x** - Initial development and core features
- **0.1.x** - First feature-complete version with send capability
- **0.x.0** - Minor version for significant new features
- **1.0.0** - Will be released when deemed production-ready by maintainer
