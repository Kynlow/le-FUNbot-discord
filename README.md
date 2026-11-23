# FUNbot

> Tournament brackets made easy, right in your Discord chat.

FUNbot is a Discord bot that runs video game tournaments directly inside a server. Admins open a tournament and choose its format, teams register through Discord, and the bot builds the bracket and tracks match results.

## Status

🚧 **Work in progress.** The project structure and configuration are in place; the tournament features are being built step by step (see the roadmap below).

## Tech stack

- [Node.js](https://nodejs.org/)
- [discord.js](https://discord.js.org/) v14
- [dotenv](https://github.com/motdotla/dotenv)

## Prerequisites

- Node.js 18 or higher (check the discord.js documentation for the exact requirement of the version you install)
- A Discord account and a server where you can add bots
- An application and a bot created in the [Discord Developer Portal](https://discord.com/developers/applications)

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/FUNbot.git
   cd FUNbot
   ```

2. Install the dependencies:

   ```bash
   npm install
   ```

3. Create your environment file from the template:

   ```bash
   cp .env.example .env
   ```

   On Windows (Command Prompt), use `copy .env.example .env` instead.

4. Fill in the values in `.env` (see below).

## Configuration

| Variable        | Description                                  | Where to find it                                         |
| --------------- | -------------------------------------------- | -------------------------------------------------------- |
| `DISCORD_TOKEN` | Your bot's secret token                      | Developer Portal → your app → **Bot** tab → Reset Token |
| `CLIENT_ID`     | Your application's ID                        | Developer Portal → **General Information**               |
| `GUILD_ID`      | ID of the test server where commands deploy  | Discord (Developer Mode on) → right-click server → Copy Server ID |

> ⚠️ Never commit your `.env` file or share your token. If it leaks, reset it immediately in the Developer Portal.

### Inviting the bot to your server

In the Developer Portal, generate an invite link with the `bot` and `applications.commands` scopes and the permissions *Send Messages*, *Embed Links* and *Attach Files*, then open it and select your server.

## Usage

Register the slash commands on your server (run this again whenever a command definition changes):

```bash
npm run deploy
```

Start the bot:

```bash
npm start
```

## Project structure

```
FUNbot/
├── src/
│   ├── index.js              # Bot entry point
│   ├── deploy-commands.js    # Registers slash commands with Discord
│   ├── commands/             # Slash command definitions and handlers
│   ├── events/               # Discord event handlers
│   ├── logic/                # Tournament and bracket logic (no Discord code)
│   ├── render/               # Bracket rendering (text and image)
│   └── storage/              # Data persistence
├── tests/                    # Unit tests
├── .env.example              # Environment variables template
└── package.json
```

The code is split into three layers: Discord interface (`commands`, `events`), pure tournament logic (`logic`) and rendering (`render`), so each part can be developed and tested independently.

## Roadmap

- [x] Project setup and configuration
- [ ] Bot connection and slash commands
- [ ] Tournament creation and team registration
- [ ] Bracket generation (byes, random seeding)
- [ ] Match results and winner advancement
- [ ] Bracket image rendering
- [ ] Data persistence
- [ ] Unit tests
- [ ] Hosting and public demo server

## License

To be defined.