# Crontab

Scheduling a recurring task using cron.

## Example

```
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```

| Field | Value | Meaning |
|---|---|---|
| Minute | `0` | At minute 0 |
| Hour | `*/12` | Every 12 hours |
| Day of month | `*` | Every day |
| Month | `*` | Every month |
| Day of week | `*` | Every day of the week |
| Command | `cp -R /home/cmnatic/Documents /var/backups/` | Recursively copies the `Documents` folder to `/var/backups/` |

**In plain English:** every 12 hours, back up `/home/cmnatic/Documents` to `/var/backups/`.
