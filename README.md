# 📧 Email CLI - Temporary Email Manager

A powerful command-line tool for creating and managing temporary/disposable email addresses.

## Features

✨ **Create temporary email addresses** - Generate random or custom email names  
📬 **Check inbox** - View received emails in real-time  
📖 **Read emails** - Read full email content from the terminal  
📤 **Send emails** - Send emails using your own SMTP account (optional)  
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

3. Run the install script:
```bash
./install.sh
```

Or manually add to PATH:
```bash
sudo ln -s /home/kali/labs/email-cli/email /usr/local/bin/email
```

Or add an alias to your `.zshrc`:
```bash
echo "alias email='/home/kali/labs/email-cli/email'" >> ~/.zshrc
source ~/.zshrc
```

### Optional: Enable Email Sending

To send emails (not just receive), you need to configure SMTP:

1. Copy the sample config:
```bash
cp .env.sample ~/.config/tempmail/.env
```

2. Edit the config file:
```bash
nano ~/.config/tempmail/.env
```

3. Choose one of these **FREE** options:

**Option 1: Gmail (Easiest)**
- Go to: https://myaccount.google.com/apppasswords
- Generate an App Password (16 characters)
- Use these settings:
  ```
  SMTP_HOST=smtp.gmail.com
  SMTP_PORT=587
  SMTP_USER=your-gmail@gmail.com
  SMTP_PASS=your-16-char-app-password
  FROM_NAME=Your Name
  ```

**Option 2: Outlook/Hotmail (Free)**
  ```
  SMTP_HOST=smtp-mail.outlook.com
  SMTP_PORT=587
  SMTP_USER=your-email@outlook.com
  SMTP_PASS=your-password
  FROM_NAME=Your Name
  ```

**Option 3: SendGrid (100 emails/day free)**
- Sign up at: https://sendgrid.com
- Create an API Key
- Use:
  ```
  SMTP_HOST=smtp.sendgrid.net
  SMTP_PORT=587
  SMTP_USER=apikey
  SMTP_PASS=your-sendgrid-api-key
  FROM_NAME=Your Name
  ```

**That's it!** Now you can send emails with `email send`

## Usage

### Create a new temporary email
```bash
email create
```

You'll be prompted to enter a custom name or press Enter for a random one.

### List all your emails
```bash
email list
```

### Check inbox
```bash
email inbox
```

Or check a specific email:
```bash
email inbox user@domain.com
```

### Read a specific email
```bash
email read <email-id>
```

### Send an email (if SMTP configured)

**Interactive mode:**
```bash
email send
```
You'll be prompted for recipient, subject, and body.

**Quick send:**
```bash
email send friend@example.com "Hello!" "How are you?"
```

**Multi-line body:**
```bash
email send friend@example.com "My Subject"
# Then type your message and press Ctrl+D when done
```

### Set current email
```bash
email use user@domain.com
# Or use partial match:
email use user
```

### Show current email
```bash
email current
```

### Delete an email from your list
```bash
email delete user@domain.com
```

### Clear all emails
```bash
email clear
```

## Commands Reference

| Command | Alias | Description |
|---------|-------|-------------|
| `create` | - | Create a new temporary email |
| `list` | `ls` | List all stored emails |
| `inbox` | `check` | Check inbox for messages |
| `read` | `show` | Read a specific email by ID |
| `send` | `compose` | Send an email (requires SMTP config) |
| `use` | `set` | Set an email as current (supports partial match) |
| `current` | - | Show current active email |
| `delete` | `del`, `rm` | Delete email from list |
| `clear` | - | Delete all emails |
| `help` | `-h`, `--help` | Show help message |

## Examples

**Create a custom email:**
```bash
$ email create
Enter email name (leave empty for random): mytest123
✅ Email created successfully!
📧 Email: mytest123@1secmail.com
```

**Check your inbox:**
```bash
$ email inbox
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
$ email read 12345
📖 Reading email ID: 12345 from mytest123@1secmail.com

From: noreply@example.com
To: mytest123@1secmail.com
Subject: Welcome!
Date: 2025-10-01 17:00:00

Hello! Welcome to our service...
```

**Send an email:**
```bash
$ email send friend@example.com "Quick hello" "Just testing!"
📤 Sending email...
✅ Email sent successfully!
   To: friend@example.com
   Subject: Quick hello
```

## How It Works

The tool uses the [1secmail.com](https://www.1secmail.com/) API to create temporary email addresses.

**Receiving emails:**
- ⏱️ Temporary addresses that will expire
- 🆓 Completely free
- 🔓 No registration required
- 📨 Receive emails instantly

**Sending emails (optional):**
- 📤 Uses your own SMTP account (Gmail, Outlook, SendGrid, etc.)
- 🆓 Free tier available on all major providers
- 🔒 Your credentials stored locally in `~/.config/tempmail/.env`
- ✉️ Emails sent from your real address (temp email in Reply-To)

## Data Storage

All data is stored locally in `~/.config/tempmail/`:
- `emails.json` - List of your temporary emails
- `current_email` - Currently active email
- `.env` - SMTP credentials (optional, for sending)

## Requirements

**Core requirements:**
- `bash` (version 4.0+)
- `curl` (for API requests)
- `jq` (for JSON parsing)

**For sending emails (optional):**
- `python3` (usually pre-installed)

Install requirements on Kali Linux:
```bash
sudo apt-get install curl jq python3
```

## Notes

⚠️ **Important:**
- Temporary emails may be deleted by the service
- No guarantees on email delivery or storage
- Sending requires your own SMTP account (optional)
- Best for testing, signups, and temporary needs
- Not suitable for important communications
- SMTP credentials are stored locally and never shared

## Version

Current version: **1.1.0**

### Changelog
- **v1.1.0**: Added email sending with SMTP support, partial matching for `use` command
- **v1.0.0**: Initial release with receive-only functionality

## License

Free to use and modify.

## Contributing

Feel free to submit issues or pull requests!

---

Made with ❤️ for quick and easy temporary email management
