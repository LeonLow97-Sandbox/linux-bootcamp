# Cron

- The `cron` service allows us to schedule commands ot run at regular intervals like:
    - Every 30 minutes
    - Every day at midnight
    - Every 1st of the month
    - Every December 15th
- [Set timer on crontab](https://crontab.guru/)

## Editing the crontab

- To setup a cron job, we need to edit the crontab configuration file.
- Rather than edit the files directly, it's best to use the `crontab -e` command.
- `crontab -l` to view what is written in crontab

## Cron Syntax

- `30 * * * * <command>` run a job at minute 30, every hour.
- `0 0 * * * <command>` run a job every day at midnight (when hour is 0 and minute is 0).
- `30 6 * * * <command>` run a job every day at 6:30 AM (when hour is 6 and minute is 30)
- `30 6 * * 1 <command>` run a job every monday at 6:30 AM
- `30 6 * 4 1 <command>` run a job every monday in April at 6:30 AM
- `0 0 1 * * <command>` run a job at midnight on the first of every month
- `0 0 * * 1-5 <command>` run a job at midnight every weekday (monday - friday)
- `*/5 * * * * <command>` run a job every 5 minutes

## Daily Backup Cron Job

- Set up command `my-backup` to run cronjob.
- Need to ensure the command is executable. Run `chmod +x my-backup`
- Run `my-backup` to run the backup.

```bash
#!/bin/bash

DATE=$(date +%d-%m-%Y)
BACKUP_DIR="/Users/leonlow/backups"

tar -cvzf $BACKUP_DIR/backup-$DATE.tar.gz /Users/leonlow/Desktop/Projects
```

- Setting up cronjob for the command, please input whatever timing you want the backup to occur.
    - `crontab -e`

```bash
* * * * * /Users/leonlow/bin/my-backup
```

- To untar the file
    - `tar -xvzf <filename>.tar.gz`
