# 📧 Email CLI - Temporary Email Manager

A powerful command-line tool for creating and managing temporary/disposable email addresses.

## Features

✨ **Create temporary email addresses** - Generate random or custom email names  
📬 **Check inbox** - View received emails in real-time  
📖 **Read emails** - Read full email content from the terminal  
📋 **Manage multiple emails** - Store and switch between multiple temporary addresses  
🗑️ **Delete emails** - Clean up your email list  
🎨 **Colorful interface** - Easy-to-read colored output  

## Installation

1. Clone or copy the repository:
```bash
cd ~/labs
git clone <repo-url> email-cli
cd email-cli
```

2. Make the script executable (already done):
```bash
chmod +x tempmail
```

3. Add to PATH (optional):
```bash
sudo ln -s /home/kali/labs/email-cli/tempmail /usr/local/bin/tempmail
```

Or add an alias to your `.zshrc`:
```bash
echo "alias tempmail='/home/kali/labs/email-cli/tempmail'" >> ~/.zshrc
source ~/.zshrc
```

## Usage

### Create a new temporary email
```bash
./tempmail create
```

You'll be prompted to enter a custom name or press Enter for a random one.

### List all your emails
```bash
./tempmail list
```

### Check inbox
```bash
./tempmail inbox
```

Or check a specific email:
```bash
./tempmail inbox user@domain.com
```

### Read a specific email
```bash
./tempmail read <email-id>
```

### Set current email
```bash
./tempmail use user@domain.com
```

### Show current email
```bash
./tempmail current
```

### Delete an email from your list
```bash
./tempmail delete user@domain.com
```

### Clear all emails
```bash
./tempmail clear
```

## Commands Reference

| Command | Alias | Description |
|---------|-------|-------------|
| `create` | - | Create a new temporary email |
| `list` | `ls` | List all stored emails |
| `inbox` | `check` | Check inbox for messages |
| `read` | `show` | Read a specific email by ID |
| `use` | `set` | Set an email as current |
| `current` | - | Show current active email |
| `delete` | `del`, `rm` | Delete email from list |
| `clear` | - | Delete all emails |
| `help` | `-h`, `--help` | Show help message |

## Examples

**Create a custom email:**
```bash
$ ./tempmail create
Enter email name (leave empty for random): mytest123
✅ Email created successfully!
📧 Email: mytest123@1secmail.com
```

**Check your inbox:**
```bash
$ ./tempmail inbox
📬 Checking inbox for: mytest123@1secmail.com

📨 Found 2 message(s):

ID: 12345
From: noreply@example.com
Subject: Welcome!
Date: 2025-10-01 17:00:00
---
```

**Read an email:**
```bash
$ ./tempmail read 12345
📖 Reading email ID: 12345 from mytest123@1secmail.com

From: noreply@example.com
To: mytest123@1secmail.com
Subject: Welcome!
Date: 2025-10-01 17:00:00

Hello! Welcome to our service...
```

## How It Works

The tool uses the [1secmail.com](https://www.1secmail.com/) API to create temporary email addresses. These emails:

- ⏱️ Are temporary and will expire
- 🆓 Are completely free
- 🔓 Require no registration
- 📨 Can receive emails instantly
- ⚠️ **Cannot send emails** (receive-only)

## Data Storage

All email addresses are stored locally in:
- `~/.config/tempmail/emails.json` - List of your emails
- `~/.config/tempmail/current_email` - Currently active email

## Requirements

- `bash` (version 4.0+)
- `curl` (for API requests)
- `jq` (for JSON parsing)

Install requirements on Kali Linux:
```bash
sudo apt-get install curl jq
```

## Notes

⚠️ **Important Limitations:**
- Emails are temporary and may be deleted by the service
- No guarantees on email delivery or storage
- Cannot send emails (receive-only)
- Best for testing, signups, and temporary needs
- Not suitable for important communications

## Version

Current version: **1.0.0**

## License

Free to use and modify.

## Contributing

Feel free to submit issues or pull requests!

---

Made with ❤️ for quick and easy temporary email management
