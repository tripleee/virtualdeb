virtualdeb
==========

This is an **experimental** and very **crude hack** which attempts to
help you resolve (a subset of) binary library dependencies in a
virtualenv on Debian-based distros.

The code assumes you have a Python virtualenv already set up, and that
`$VIRTUAL_ENV` points to it (as it will if you have activated it).
Alternatively, if `$VIRTUAL_ENV` is unset, the first command-line
argument should be the path to the virtualenv root.

This program downloads each named package as well as dependent
packages as `deb` files into the virtualenv and makes sure any files
in them within `lib` or `usr/lib` are in a directory on `LD_LIBRARY_PATH`.

Merely copying libraries into a directory in `LD_LIBRARY_PATH` is
obviously only viable for extremely simple libraries.  If the `deb`
package contains a `postinst` script or some other configuration
actions, or contains code which hardcodes locations in the `/usr` file
system, for example, this will obviously fail.

See also [stackoverflow.com/.../shared-library-in-a-virtualenv-on-debian-pip-install-fails][1]


  [1]: http://stackoverflow.com/questions/31066557/shared-library-in-a-virtualenv-on-debian-pip-install-fails
