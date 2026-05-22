# T560 Server Operations

Private operations repository for the T560 enovation-server.

This repository is for sanitized documentation, service maps, backup policy, and runbooks only. It must not contain real tokens, API keys, passwords, database dumps, customer leads, cookies, private keys, or production .env files.

## Contents

- docs/SERVER_INVENTORY.md - host, services, ports, directories, runtime notes
- docs/SERVICE_MAP.md - domain to Cloudflare/Nginx/service mapping
- docs/BACKUP_POLICY.md - what belongs in GitHub vs encrypted/offsite backups
- docs/SECURITY_AND_SECRETS.md - sensitive data handling rules
- docs/GITHUB_BACKUP_PLAN.md - project-by-project GitHub plan
- docs/CHANGELOG.md - operations change log
- unbooks/ - step-by-step maintenance procedures
- config-templates/ - redacted example configs only

## Golden Rules

1. Push documentation and source code only after reviewing git status.
2. Never push real .env, tokens, keys, cookies, databases, logs, customer leads, or uploaded files.
3. Before server changes: inspect, explain, backup, modify narrowly, verify, record.
4. Each production project should eventually have its own private GitHub repository.
