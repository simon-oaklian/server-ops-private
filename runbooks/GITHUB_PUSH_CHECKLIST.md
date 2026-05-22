# GitHub Push Checklist

Before every push:

`ash
git status --short
git diff --cached --name-only
`

Search staged files for risky terms:

`ash
git diff --cached --name-only | xargs grep -nEi 'api[_-]?key|token|secret|password|private[_-]?key|cookie|oauth' || true
`

Review these are not staged:

- .env, .env.*
- *.db, *.sqlite, *.sqlite3
- *.log
- uploads/, storage/, 
ode_modules/, .next/
- Cloudflare credentials
- OAuth files
- customer leads or exports

Push only after the staged file list is clean.
