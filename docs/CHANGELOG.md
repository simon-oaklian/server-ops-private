# Operations Changelog

## 2026-05-22

- Created server-ops-private repository structure locally on the server.
- Added sanitized server inventory, service map, backup policy, security policy, and GitHub backup plan.
- Confirmed GitHub repository exists but server SSH key is not yet authorized by GitHub.
- Earlier same day: restored high-traffic Oaklian SEO article URL and added it to sitemap.

## Change Log Rules

For every future production change, record:

- Date/time
- Project
- Files/directories changed
- Backup location
- Verification command/result
- Rollback note

## 2026-05-22 Code Backup Prep

Prepared local Git repositories and first commits:

- /var/www/oaklian -> oaklian-site, commit 31cd3fa, excludes leads, uploads, logs, IndexNow key, backups, privacy originals.
- /home/simon/AI-SEO-oaklian -> oaklian-seo-v4, commit 179fce2, excludes .env, secrets, uploads, logs, generated site, production compose; includes redacted compose example.
- /var/www/crm-oaklian -> oaklian-crm, commit dffb65, excludes database, uploads, logs, generated/customer documents, backups.
- /home/simon/deals -> pricvo-deals, commit b4d9dd, excludes .env.local, .next, 
ode_modules, storage SQLite.

Deferred because source contains hardcoded default/demo passwords that should be refactored or sanitized first:

- /var/www/recossi
- /home/simon/jnono

No business services were restarted. No runtime databases, logs, customer uploads, tokens, keys, or production .env files were committed.
