# Abhisek MD

A lightweight, plugin-based WhatsApp automation framework customized and maintained by **Abhisek Praharaj**.

> **Notice:** This project uses an unofficial WhatsApp Web client. Use only for personal, consent-based automation. Account restrictions or bans are possible, and you must follow WhatsApp's terms and applicable law.

## Features

- Plugin-based command architecture
- Single and multi-session configuration
- Group administration utilities
- Media and format conversion tools
- AFK, filters, scheduled actions, and message statistics
- PDF and social-media utilities (depending on plugin/API availability)
- Runtime configuration through environment variables
- SQLite for local deployments and PostgreSQL support for cloud deployments
- PM2-based process management

**Command availability depends on the installed plugins, external APIs, permissions, and WhatsApp protocol compatibility. Use `.list` to inspect commands exposed by the running bot and `.info <command>` for command details.**

## Prerequisites

- Node.js 20+
- Git
- FFmpeg (required by several media features)
- Yarn
- PM2 (recommended)
- PostgreSQL `DATABASE_URL` for cloud deployments; local SQLite is used when it is omitted

## Installation

```bash
npm install -g yarn pm2
git clone https://github.com/praharaj03/raganork-md.git
cd raganork-md
yarn install
```

## Configuration

Create a `.env` file in the project root. Start from `.env.example`:

```env
SESSION=RGNK~YOUR_SESSION_VALUE
BOT_NAME=Abhisek MD
HANDLERS=.,!
SUDO=919876543210
LANGUAGE=en
TZ=Asia/Kolkata
# DATABASE_URL=postgresql://user:password@host:5432/database
```

Never commit `.env`, session strings, API keys, database credentials, or authentication-state files. A session string can provide access to the linked WhatsApp account.

## Run

```bash
npm start
```

Useful PM2 commands:

```bash
pm2 status
pm2 logs abhisek-md
pm2 restart abhisek-md
pm2 stop abhisek-md
```

## Built-in discovery commands

The command registry provides:

- `.list` — display available commands grouped by category
- `.info <command>` — show a command's description, usage, and restrictions
- `.alive` — check whether the bot is running
- `.setalive` — configure the alive message (owner-only)

Other commands are supplied by individual plugins and may require administrator, owner, API, or media permissions.

## Project structure

```text
abhisek-md/
├── plugins/     # Feature plugins
├── core/        # Bot, database, session, and message handling
├── config.js    # Runtime configuration
├── index.js     # Entry point
├── main.js      # Application bootstrap
└── package.json # Dependencies and scripts
```

## Responsible use and security

- Do not send spam, unsolicited bulk messages, or harassment.
- Do not expose pairing codes, session strings, logs, or authentication files.
- Restrict owner/admin commands carefully.
- Review third-party APIs before enabling a plugin.
- Pin and regularly review dependencies; keep Baileys and related packages updated.
- Prefer Meta's official WhatsApp Cloud API for production or commercial messaging.

## License

GPL-3.0. See [LICENSE](LICENSE).

## Credits

Original framework: [souravkl11/raganork-md](https://github.com/souravkl11/raganork-md)

WhatsApp connectivity: [Baileys](https://github.com/WhiskeySockets/Baileys)
