# Lola's - Trading Bot (Repository bundle)

This repository bundle contains a complete starter trading-bot system intended to run on a VPS (e.g. DigitalOcean).
It includes:

- Flask webhook backend (Kraken integration)
- Trade executor with dynamic position sizing
- Notifier (Telegram)
- Web UI for basic setup (PayPal email, API keys)
- Dockerfile and docker-compose for one-command deploy
- Setup script for VPS

**Important:** I cannot host this for you. You must run the code on a server you control. The bundle is a starting point — test extensively in paper mode before using real funds.

## Quick steps (summary)
1. Upload files to GitHub or copy to your VPS.
2. Create a Droplet on DigitalOcean (Ubuntu 22.04).
3. SSH into the droplet and run `setup_bot.sh` (or copy files and run `docker compose up -d`).
4. Edit `backend/.env` before starting containers to add your Kraken API keys and Telegram credentials.
5. Open `http://YOUR_DROPLET_IP/` on your smartphone to access the Web UI.

Read the full README (below) for exact commands and explanations.


---

## Full instructions (step-by-step)

1. Create a Droplet (DigitalOcean) with Ubuntu 22.04 (1vCPU/2GB). Note the IP.
2. Upload this repository bundle to the droplet or clone from GitHub after you upload it there.
3. SSH into the droplet (using Termux/Blink/Termius on mobile).
4. Place the repo files into `/opt/lolas-trading-bot` or clone into that directory.
5. Edit `backend/.env` and add your Kraken API keys, Telegram credentials and a FERNET_KEY (generate with Python's cryptography.Fernet).
6. Run the setup script:
   ```
   sudo /opt/lolas-trading-bot/setup_bot.sh
   ```
7. After containers are up, open `http://YOUR_DROPLET_IP/` on your smartphone to access the UI.
8. Create TradingView alerts pointing to `http://YOUR_DROPLET_IP/webhook` with JSON payloads similar to the examples in the earlier conversation.

## Important security notes
- Never paste API secrets into web forms. Put them only in `backend/.env` on your server.
- Test using small amounts or a paper/ demo account before using real funds.
- Review Kraken API permissions (limit to required rights) and revoke keys if compromised.

