tarpit
------

tarpit helps you make backups with [Tarsnap](http://www.tarsnap.com/).



USAGE
-----

List all backups with `tarpit`:

    $ tarpit
    documents
    misc
    var


Run a backup with `tarpit <backup>`:

    $ tarpit documents



SETUP
-----

Your backup configs are kept in `~/.tarpit/`. Files are regular shell
scripts which will be `source`d at run time. These scripts can contain
pretty much anything you like as long as a few variables are set:


* `ARCHIVE`

  The name of the archive.

* `FILES`

  An array of files and directories to include in the archive.

* `EXCLUDE` (optional)

  An array of patterns for Tarsnap to ignore.

* `KEYFILE` (optional)

  Path to the keyfile to use for this backup



EXAMPLES
--------

    # ~/.tarpit/documents
    ARCHIVE="docs-$(date +%Y-%m-%d)"
    FILES=(~/Documents)

    # ~/.tarpit/misc
    ARCHIVE="$(hostname)-misc-$(date +%Y-%m-%d)"
    FILES=(~/var/log ~/var/mail)
    EXCLUDE=(~/var/tmp)
    KEYFILE=/path/to/custom.key

    # ~/.tarpit/work
    SRC=~/Work
    DEST=/mnt/backups/Work
    EXCLUDE=(
      ~/Work/secret_project1
      ~/Work/secret_project2
    )
