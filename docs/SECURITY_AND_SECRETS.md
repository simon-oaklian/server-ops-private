# Security and Secrets Policy

Last reviewed: 2026-05-22

## Never Commit

- Production .env files
- API keys
- OAuth client secrets or token files
- Cloudflare tunnel certs/JSON credentials
- SSH private keys
- Cookies/session files
- Database files or dumps
- Customer leads, CRM exports, estimate PDFs, uploaded documents
- Logs that may contain personal or token data

## Known Sensitive Areas

Do not copy these raw files into GitHub:

- /etc/cloudflared/
- /home/simon/.cloudflared/
- /home/simon/secrets/
- /home/simon/xhs-mcp/data/
- /var/www/crm-oaklian/crm.db
- /var/www/crm-oaklian/uploads/
- /var/www/oaklian/content/leads.json
- /var/www/oaklian/oaklian.log
- /home/simon/AI-SEO-oaklian/.env
- /home/simon/deals/.env.local
- /home/simon/deals/storage/
- /home/simon/jnono/data/
- /var/www/recossi/storage/

## Current Risk Notes

Some production configs contain inline passwords, API keys, or tunnel credentials. Do not publish raw copies. Longer-term improvement:

1. Move secrets to .env files or systemd EnvironmentFile= paths.
2. Keep .env files out of Git.
3. Create .env.example files with fake values.
4. Rotate secrets that have been copied into old notes, screenshots, or chat history.
5. Use GitHub secret scanning and keep all repositories private.

## Redaction Format

When documenting a secret-bearing config, use placeholders:

`	xt
API_KEY=<REDACTED>
WEBHOOK_SECRET=<REDACTED>
CLOUDFLARE_TUNNEL_TOKEN=<REDACTED>
ADMIN_PASSWORD=<REDACTED>
`
