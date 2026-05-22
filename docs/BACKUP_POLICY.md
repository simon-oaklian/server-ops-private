# Backup Policy

Last reviewed: 2026-05-22

## Backup Categories

### Category A: Safe for GitHub private repositories after review

- Application source code
- Static pages and templates
- Build scripts
- Redacted config templates
- Documentation and runbooks
- .env.example files with fake values only

### Category B: Do not push to GitHub; backup encrypted/offsite

- SQLite databases: *.db, *.sqlite, *.sqlite3
- Postgres dumps
- Customer leads and CRM exports
- User uploads and private media
- Cookies/session files
- Cloudflare tunnel credentials
- OAuth client/token JSON files
- API keys, webhook secrets, passwords
- Production .env files
- Logs containing customer or token data

### Category C: Do not backup unless needed

- 
ode_modules/
- .next/
- Python __pycache__/
- temporary cache folders
- old duplicate .bak files after a retention review

## Recommended GitHub Repository Layout

Create separate private repositories:

| Repository | Source Directory | Purpose |
|---|---|---|
| server-ops-private | /home/simon/server-ops-private | Sanitized ops docs and runbooks |
| oaklian-site | /var/www/oaklian | Oaklian source/static site, excluding leads/uploads/logs/secrets |
| oaklian-seo-v4 | /home/simon/AI-SEO-oaklian | SEO generator code, excluding .env, uploads, DB volume, logs |
| oaklian-crm | /var/www/crm-oaklian | CRM code, excluding crm.db, uploads, logs, private exports |
| pricvo-deals | /home/simon/deals | Next.js project, excluding .env.local, .next, node_modules, SQLite storage |
| jnono | /home/simon/jnono | JNONO code, excluding database, images/uploads, logs |
| ecossi | /var/www/recossi | Next.js project, excluding .env, .next, node_modules, storage |

## Before Each Git Push

Run:

`ash
git status --short
git diff --cached --name-only
`

Look for and remove:

- .env or .env.*
- files containing KEY, TOKEN, SECRET, PASSWORD, COOKIE, PRIVATE
- *.db, *.sqlite, *.log
- uploads/, storage/, 
ode_modules/, .next/

## Encrypted Backup Recommendation

For databases and private runtime data, use a separate encrypted archive workflow, for example:

`ash
# Example only; choose a strong passphrase and secure storage.
tar -czf project-data-YYYYMMDD.tar.gz path/to/db path/to/uploads
# Then encrypt before offsite storage.
`

Do not store encrypted backup passphrases inside GitHub.
