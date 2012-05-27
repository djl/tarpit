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

tarpit reads from an INI-style config file called `~/.tarpit`. Each
section of this file corresponds to a single backup.


### Backup settings

* `name`

   The name of the archive to be created. Treated as an `strftime(3)` string.

* `files`

   A list of comma-separated files and directories to be included in the
   backup.

* `exclude` (optional)

   A list of files to exclude from a backup.


EXAMPLE
-------

    [documents]
    name = documents-%Y-%m-%d
    files = /home/bob/Documents

    [misc]
    name = misc-%Y-%m-%d
    files = /home/bob/misc, /home/bob/this, /home/bob/that

    [var]
    name = var-%Y-%m-%d
    files = /home/bob/var
    exclude = /home/bob/var/tmp
