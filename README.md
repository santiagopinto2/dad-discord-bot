# Dad Bot

A Discord bot for when you need a dad joke to brighten up your day.

- Someone says "I'm hungry": the bot replies "Hi hungry, I'm Dad!" (also for "im" and curly apostrophes).
- "hi dad", "hey dad", "hello dad" (or the same with an @mention of the bot) get a greeting back.
- `!ping` (prefix from `PREFIX`, `!` by default) replies "pong", to check the bot is online.

## Running it

Needs Node.js and a `.env` file (gitignored) next to `index.js`:

```
TOKEN=<Discord bot token>
PREFIX=!
```

Then `npm install && npm start`.

It runs as the `dadbot` service in `/srv/santi/compose.yml` on Santi's server (`node:22`, this folder bind-mounted, `npm install && npm start` on every start). To update it there:

```
cd /srv/santi/dadbot && git checkout -- package-lock.json && git pull
docker compose -f /srv/santi/compose.yml up -d --force-recreate dadbot
```

The `git checkout` step is there because the container's `npm install` rewrites `package-lock.json`.
