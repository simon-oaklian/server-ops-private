# Server Inventory

Last reviewed: 2026-05-22
Host: enovation-server
Primary user: simon
SSH alias from local workstation: 	560
LAN host: 192.168.50.245
Disk: /dev/sda2, about 937G total, about 40G used at review time

## Running Service Summary

| Service | Public/Local Entry | Runtime | Main Directory | Notes |
|---|---:|---|---|---|
| Oaklian main site | oaklian.com, www.oaklian.com | Python app + static files | /var/www/oaklian | Production site content and admin pages |
| Oaklian SEO V4 generator | :8001 | Docker/FastAPI-style generator | /home/simon/AI-SEO-oaklian | Generates SEO articles and writes static output |
| Oaklian SEO web | :8080 | Docker Nginx | /home/simon/AI-SEO-oaklian/site | Cloudflare currently routes oaklian.com to this service |
| Oaklian CRM | :5001 local app | Python app | /var/www/crm-oaklian | Contains crm.db, logs, uploads |
| JNONO | jnono.com, www.jnono.com | Python app | /home/simon/jnono | Learning/member system |
| Pricvo/Deals | pricvo.com, www.pricvo.com | Next.js | /home/simon/deals | Uses SQLite storage |
| JZOZO/Recossi | jzozo.com, www.jzozo.com | Next.js | /var/www/recossi | Uses storage JSON/SQLite |
| n8n | :5678 | Docker | Docker volume 
8n_n8n_data | Automation workflows |
| OpenClaw | openclaw.oaklian.com | Docker | Docker volume openclaw_openclaw_data | Browser/agent tooling |
| Xiaohongshu MCP | :18060 | Docker | /home/simon/xhs-mcp | Has cookies/data directories; treat as sensitive |
| Ollama | :11434 | systemd | system service | Local model service |

## Listening Ports Observed

| Port | Observed Process/Container | Likely Purpose |
|---:|---|---|
| 22 | sshd | SSH access |
| 80 | nginx | Host-level HTTP routing |
| 4174 | /var/www/oaklian/app.py | Oaklian Python app |
| 5001 | /var/www/crm-oaklian/app.py | Oaklian CRM |
| 5173 | /home/simon/jnono/app.py | JNONO app |
| 5678 | Docker 
8n | n8n |
| 8000 | /home/simon/jnono/app.py or Python service observed | Check before changing |
| 8001 | Docker OAKLIAN-SEO-GENERATOR | SEO V4 backend |
| 8080 | Docker OAKLIAN-SEO-WEB | SEO static web |
| 8090 | Docker openclaw | OpenClaw |
| 18060 | Docker xiaohongshu-mcp | XHS MCP |
| 3017 | Next.js | Pricvo/Deals |
| 3100 | Next.js | JZOZO/Recossi |
| 11434 | Ollama | Local model API |

## Systemd Services Observed

- oaklian.service
- crm-oaklian.service
- jnono.service
- jzozo.service
- ecossi.service
- cloudflared.service
- cloudflared-deals.service
- cloudflared-jnono.service
- 
ginx.service
- docker.service
- 
8n runs as a Docker container, not a direct systemd app

## Docker Containers Observed

- OAKLIAN-SEO-DB - Postgres 16, volume i-seo-oaklian_seo_db
- OAKLIAN-SEO-GENERATOR - SEO V4 generator, bind mounts project and /var/www/oaklian
- OAKLIAN-SEO-WEB - Nginx serving /home/simon/AI-SEO-oaklian/site
- 
8n - n8n automation, volume 
8n_n8n_data
- openclaw - OpenClaw app
- openclaw-browser - browserless Chrome
- xiaohongshu-mcp - XHS MCP service

## Important Data Stores

Do not push these to GitHub in plaintext:

- /var/www/crm-oaklian/crm.db
- /home/simon/deals/storage/homedealio.sqlite
- /home/simon/jnono/data/jnono.db
- /var/www/recossi/storage/recossi.sqlite
- Docker volume i-seo-oaklian_seo_db
- Docker volume 
8n_n8n_data
- Docker volume openclaw_openclaw_data
- /home/simon/xhs-mcp/data/cookies.json
- /home/simon/secrets/
- Cloudflare tunnel JSON/cert files under /etc/cloudflared and /home/simon/.cloudflared
