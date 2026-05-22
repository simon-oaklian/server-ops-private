# Safe Change Workflow

Use this procedure before changing production services.

## 1. Inspect

- Identify the service, directory, process, port, and public route.
- Read only the files relevant to the task.
- Check whether there are existing backups.

## 2. Explain

Before editing, state:

- What will be changed
- Why it is needed
- What will be backed up
- How it will be verified

## 3. Backup

Use a timestamped backup path such as:

`	xt
/home/simon/backups/<project>/<YYYYMMDD_HHMMSS>/
`

Do not overwrite older backups.

## 4. Modify Narrowly

- Keep edits scoped.
- Do not delete unrelated files.
- Avoid changing service startup unless the task requires it.

## 5. Verify

Examples:

`ash
curl -I https://example.com/path/
systemctl status service-name --no-pager
docker ps
`

## 6. Record

Update docs/CHANGELOG.md with backup location and verification result.
