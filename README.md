# Rsync time backup

Time Machine style backup with rsync. Should work on Linux, Mac OS X and Windows with Cygwin.

# Installation

	git clone https://github.com/laurent22/rsync-time-backup

# Usage

	rsync_tmbackup.sh <source> <destination> [excluded-pattern-path]

## Examples
	
* Backup the home folder to backup_drive
	
		rsync_tmbackup.sh /home /mnt/backup_drive  

* Backup with exclusion list:
	
		rsync_tmbackup.sh /home /mnt/backup_drive excluded_patterns.txt
	
## Exclude file

An optional exclude file can be provided as a third parameter. It should be compabible with the `--exclude-from` parameter of rsync. See [this tutorial] (https://sites.google.com/site/rsync2u/home/rsync-tutorial/the-exclude-from-option) for more information.

# Features

* Each backup is on its own folder named after the current timestamp. Files can be copied and restored directly, without any intermediate tool.

* Files that haven't changed from one backup to the next are hard-linked to the previous backup so take very little extra space.

* Safety check - the backup will only happen if the destination has explicitely been marked as a backup destination.

* Resume feature - if a backup has failed or was interrupted, the tool will resume from there on the next backup.

* Exclude file - support for pattern-based exclusion via the `--exclude-from` rsync parameter.

* The application is one bash script that can be easily edited.

# TODO

* Check if there's enough space in the destination before doing the backup. Also automatically delete old backups.

* Manage the backups in a way similar to Time Machine - hourly backups for the past 24 hours; daily backups for the past month; weekly backups for the previous months.

# Comments

* https://news.ycombinator.com/item?id=6623514
