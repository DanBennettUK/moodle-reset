#### This script is to automatically restore a site from supplied backup files.

[![Build Status](https://travis-ci.org/DanBennettUK/moodle-reset.svg?branch=master)](https://travis-ci.org/DanBennettUK/moodle-reset)


## Installation

1. Navigate to your Moodle directory (e.g. `/var/www/html/moodle`)
2. Clone GIT repository `git clone https://github.com/DanBennettUK/moodle-reset.git`
3. Party???

---

## Usage

-   To backup the site in it's current state:

```sh
$ php reset_moodle.php --backup
```

The default backup file for the data directory is called `moodledata.tar.gz`.
The default backup file for the database is called `dump.sql`.

These will be generated by the above backup command.

-   To restore the site in it's current state:

```sh
$ php reset_moodle.php --restore
```

This will restore the site from the default backup files created as above.

You can also restore your own custom backups by specifying the location of both Moodledata and the SQL dump with the following flags:

`--moodledata="/path/of/moodledata.tar.gz"`
`--database="/path/of/database.sql"`

-   To update on restore:

```sh
$ php reset_moodle.php --restore --update
```

This will run a `git pull` and the update script within Moodle. Providing you have Moodle installed as a GIT repository.

---

## Notes:

-   This will also work against Totara, however the backup file will still be called "moodledata"
-   You can rename the default backup files if you wish, just ensure you specify them in the command when running the restore
-   Maintenance mode is enabled and disabled throughout the backup and restore processes
-   SELinux permissions also get fixed if enabled.
-   If you cancel the restore, rename `index.backup.php` to `index.php` to restore the Moodle site.