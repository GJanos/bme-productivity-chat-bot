# Productivity Chat Bot

A command-line productivity assistant powered by GPT that manages your schedule and
to-dos through natural language, integrating directly with the Google Calendar and
Google Tasks APIs.

**Tech stack:** Python · OpenAI API · Google Calendar API · Google Tasks API · OAuth 2.0

## Features

- **Conversational interface** — talk to the bot in plain language; it interprets intent
  via GPT and calls the right API.
- **Calendar integration** — read and manage events through the Google Calendar API.
- **Task integration** — manage to-dos through the Google Tasks API.
- **Conversation memory** — keeps a bounded, queue-like message history (preserving the
  initial system context) so the model stays coherent without unbounded growth.
- **Reminders** and configurable debug output via a `Config` layer.

## Project structure

```
├── main.py     # entry point: auth, client setup, chat loop
├── Config.py   # configuration / debug flags
└── events.ics  # sample calendar data
```

See `chatbotDocumentation.pdf` for a full writeup.

## Build & run

```bash
pip install openai google-api-python-client google-auth-oauthlib python-dotenv

# Required secrets (never commit these):
#   OPENAI_API_KEY        -> in a .env file
#   Google OAuth client   -> auth/credentials.json (token.json is created on first run)

python main.py
```

> Modifying the requested Google API scopes invalidates `auth/token.json` — delete it to
> re-authorize.

---

*Personal project pairing an LLM with the Google Workspace APIs to automate calendar and
task management from the terminal.*
