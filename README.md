# Stand Reminder

A simple PWA that reminds users to stand and move at random intervals.

## Project Structure

```text
.
├─ public/
│  ├─ index.html
│  ├─ manifest.json
│  └─ sw.js
├─ server.js
├─ package.json
└─ package-lock.json
```

## Features

- Random work/break intervals
- Vibration + audio + browser notifications
- Daily stats in `localStorage`
- PWA install support (service worker + manifest)

## Prerequisites

- Node.js 22+

## Local Development

```bash
npm install
npm start
```

Server default:

- URL: `http://127.0.0.1:3001`
- HOST: `127.0.0.1`
- PORT: `3001`

## LAN/Public Binding

To allow access from other devices in the same network:

```bash
npm run start:public
```

This starts the server on `0.0.0.0:3001`.

## Deploy on Linux Server

```bash
git clone <your-repo-url>
cd StandReminder
npm ci
HOST=127.0.0.1 PORT=3001 npm start
```

Recommended production setup:

- Run Node with `HOST=127.0.0.1`
- Put Nginx/Caddy in front for HTTPS and public traffic
- Keep only port `80/443` open in firewall

## Security Notes

- Static files are served from `public/` only
- Do not store secrets in this repository
- Use HTTPS in production
