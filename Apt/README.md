Provides read access to APT repositories.

This plugin is a rewrite of PackageInfo using the `python-apt` library instead
of parsing `apt-cache`'s console output.

## Usage

To use it, you must set `$DATADIR/aptdir/etc/apt/sources.list` (where $DATADIR is
configured with `supybot.directories.data`, which defaults to $BOTDIR/data`)
to the list of sources you want to use. See `man sources.list` for supported
format.

You should also either allow insecure sources, or add keys to the trusted
store yourself.

Example:

```
deb [trusted=yes] http://archive.ubuntu.com/ubuntu bionic main universe
deb-src [trusted=yes] http://archive.ubuntu.com/ubuntu bionic main universe
deb [trusted=yes] http://deb.debian.org/debian buster main
deb-src [trusted=yes] http://deb.debian.org/debian buster main
deb [trusted=yes] http://deb.debian.org/debian stretch-backports main
deb-src [trusted=yes] http://deb.debian.org/debian stretch-backports main
```

The bot will then take care of updating these sources, based on the value of
`supybot.plugins.Apt.cache.updateInterval`.
