tarpit
------

tarpit helps you make backups with [Tarsnap](http://www.tarsnap.com/).



USAGE
-----

List backup names with `tarpit`:

    $ tarpit
    documents
    misc
    var


Run a backup with `tarpit <backup>`:

    $ tarpit documents



SETUP
-----

Configs are just directories kept in `~/.config/tarpit`. Each
directory must contain a file called `config`. This is a regular shell
script which will be sourced at run time. This file must contain the
following variables:

* `NAME`

  The name of the archive.

* `FILES`

  An array of files to be excluded in the archive.

* `EXCLUDE` (optional)

  An array of files or directories to be excluded from the archive.

* `KEYFILE` (optional)

  Path to the keyfile to use for this backup



HOOKS
-----

`tarpit` supports running custom actions at a few points. Just place
the following files in your config directories (i.e next to your
`config` file) and make them executable:


* `pre`

  Will be run immediately before Tarsnap is called. If this exits with
  a non-zero status, the backup will be halted.

* `post`

  Will be run immediately after Tarsnap is called.



EXAMPLES
--------

See `examples` for example configurations.
