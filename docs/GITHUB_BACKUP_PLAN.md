# GitHub Backup Plan

Last reviewed: 2026-05-22

## Phase 1: Operations Documentation

Repository: server-ops-private
Source: /home/simon/server-ops-private
Status: prepared locally, safe to push after GitHub SSH access is granted.

Contents:

- Sanitized server map
- Service/domain mapping
- Backup policy
- Secret handling policy
- Runbooks
- Redacted config templates

## Phase 2: Oaklian Site

Repository: oaklian-site
Source: /var/www/oaklian

Exclude:

- oaklian.log
- content/leads.json
- uploads/ unless separately reviewed
- any .env or real secret files
- __pycache__/, *.pyc, old bulky backups

Special note: Oaklian is connected to SEO V4 publishing. Before major work, confirm whether the active public route is served through Cloudflare to port 8080, port 4174, or both.

## Phase 3: SEO V4

Repository: oaklian-seo-v4
Source: /home/simon/AI-SEO-oaklian

Exclude:

- .env and all .env.bak*
- uploads/
- logs/
- database volumes
- generated static output if treated as deploy artifact
- secret credentials under generator/secrets/

Review before push:

- generator/app.py
- generator/publisher.py
- generator/prompts/
- generator/static/
- docker-compose.yml must be redacted or converted to example if it contains secrets

## Phase 4: CRM

Repository: oaklian-crm
Source: /var/www/crm-oaklian

Exclude:

- crm.db
- uploads/
- crm.log
- customer exports, PDFs, private documents
- any real .env

## Phase 5: Pricvo/Deals

Repository: pricvo-deals
Source: /home/simon/deals

Exclude:

- .env.local
- .next/
- 
ode_modules/
- storage/
- logs

## Phase 6: JNONO

Repository: jnono
Source: /home/simon/jnono

Exclude:

- data/jnono.db
- images/ unless intentionally public
- logs
- backup archives
- Mac resource fork files ._*

## Phase 7: Recossi/JZOZO

Repository: ecossi
Source: /var/www/recossi

Exclude:

- .next/
- 
ode_modules/
- storage/
- logs
- real env/secrets

## GitHub Access Needed

The server currently has an SSH key, but GitHub does not accept it yet. Add the server public key to GitHub before pushing.

Recommended: add as a deploy key with write access to this private repository, or add it to the account SSH keys if you want the server to push multiple repositories.
