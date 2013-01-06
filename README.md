sbt (SyncML Backup Tool)
========================

The command-line ``sbt`` tool allows you to perform a complete backup
of a server that exposes its data via
[SyncML](http://en.wikipedia.org/wiki/SyncML). It does this by
querying the server what data stores it contains, then requesting all
the content, and storing it opaquely and format agnostically in a
local directory. During a ``restore`` operation, it simply tells the
server to delete all of its data and uploads the previously downloaded
version.

Usage
=====

Typical usage comprises first doing a ``backup`` and then at some
point a ``restore``. sbt does, however, also support doing a
``discover`` operation (which simply describes the remote server's
storage structure) and a ``sync`` operation, which tells sbt to
resolve changes to a snapshot that have been made since the last
backup or sync.

``sbt backup`` call:

``` shell
$ sbt --server URL --username USERNAME --password PASSWORD backup DIRECTORY

example:
$ sbt -s https://example.com/funambol/ds -u guest -p guest backup ./backups/latest
```

Then, to restore the server to that snapshot, simply use the ``restore`` command:

``` shell
$ sbt restore DIRECTORY

example:
$ sbt restore ./backups/latest
```

Other supported commands:

``` shell
$ sbt --help            # shows a help screen with all supported options
$ sbt discover DIR      # displays the storage structure of the remote server
$ sbt sync DIR          # brings the DIRectory and the remote server into sync
```

Enjoy!
