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

## 2026-05-22 GitHub Push Complete

Pushed the first four sanitized code repositories to GitHub private repositories:

- oaklian-site -> commit 31cd3fa19c6f3f965fecd6c11ab542619a9c0203
- oaklian-seo-v4 -> commit 179fce2a9b42bf07579516042e2d928e42525476
- oaklian-crm -> commit dffb6559d01fea0af458348c61603cb1f91cb03
- pricvo-deals -> commit b4d9ddf5deac378b07ea4923f1d284672a1a8c6

Each repository uses a separate GitHub deploy key with write access. Sensitive runtime files remain excluded by .gitignore.

## 2026-05-22 Sanitized Recossi and JNONO Backup Prep

Prepared sanitized backup repositories outside production directories:

- /home/simon/code-backups/recossi -> source /var/www/recossi, commit 79bd4e, excludes storage, SQLite/database files, .next, 
ode_modules, logs, env files, public uploads. Default/demo passwords were replaced with CHANGE_ME_* placeholders in the backup copy only.
- /home/simon/code-backups/jnono -> source /home/simon/jnono, commit 52ad296, excludes data/, question bank/database, images, backups, templates, logs, debug files, env files. Default/demo passwords were replaced with CHANGE_ME_* placeholders in the backup copy only.

Production data and source directories were not modified for these backups.

Clarification: the sanitized Recossi/JNONO commits were created from /home/simon/code-backups/... copies. Production data was not modified. Earlier inspection created empty local Git metadata in the original Recossi/JNONO directories; it has not been pushed and can be cleaned later after explicit confirmation.
