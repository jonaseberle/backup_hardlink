## What does it do? / Features
‹backup_hardlink› does incremental (fast) backups and only uses space for changed files.

Backups are not put into a file but kept as a whole filesystem tree so can be accessed quickly. 

It picks up unfinished backups.

It increases the time between kept older backups by default (logarithmic). How quickly the interval shall raise is configurable by an initial value and a multiplier. The default curve is around "1 for each day of the last week, then at least 1 each week".

It can automatically delete backups older than a defined timespan (e.g., 90 days).


## Requirements
* rsync on both sides 
* on the receiver side: a filesystem capable of hardlinks (e.g., EXT4)
* on the receiver side: screen (for asynchroneous janitor-operations on the file store)
* bash, nice, ionice, tr, grep
* either local backups or SSH connection (preferable via public key) from sender to receiver


## How to
Feel free to ask me to clarify things or append documentation.

To kick it off, copy `backup-hardlink.conf.template` to where you keep configuration files (e.g. `/etc/backup-hardlink.conf`) and fill in the configuration variables with the help of the comments. To get it running, LOCAL_DIRS and the BACKUP_* variables are all you need

