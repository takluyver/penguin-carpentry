Storing data
============

When the user deliberately saves or exports a file, they'll normally select
where it should go. Data that you want to store 'invisibly' is divided into a
few categories:

- **Cache**: Data that can be regenerated or redownloaded if necessary
- **Configuration**
- **Runtime**: Transient objects your application uses while it's running
- **Application data**: Everything else

.. seealso::

  `XDG base directory specification <https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html>`_

.. _basedirs-cache:

Cache
-----

Cached data is stored in a single folder, controlled by an environment variable.
It's a good idea to make a subdirectory for your application.

.. envvar:: XDG_CACHE_HOME

  A path to a directory where cache data should be stored.
  If empty or unset, the default is ``~/.cache``.

.. _basedirs-config:
.. _basedirs-data:

Configuration & application data
--------------------------------

Both configuration and application data have an ordered list of directories to
look in. If you're storing data at runtime, you should write to the appropriate
'home' location, which is also the highest priority location to look for files.
The other locations allow config/data files to be installed systemwide.

If your application will need more than a single file in either of these
categories,
it's a good idea to use a subdirectory to group together the files it uses.

.. envvar:: XDG_CONFIG_HOME

  A path to a directory where config data should be stored.
  If empty or unset, the default is ``~/.config``.

.. envvar:: XDG_CONFIG_DIRS

  A colon-separated list of directories to look for config files,
  in addition to ``XDG_CONFIG_HOME``.
  If empty or unset, the default is ``/etc/xdg``.

.. envvar:: XDG_DATA_HOME

  A path to a directory where application data should be stored.
  If empty or unset, the default is ``~/.local/share``.

.. envvar:: XDG_CONFIG_DIRS

  A colon-separated list of directories to look for application data files,
  in addition to ``XDG_DATA_HOME``.
  If empty or unset, the default is ``/usr/local/share/:/usr/share/``.

.. _basedirs-runtime:

Runtime data
------------

Runtime data is stored in a single directory. This is meant for communication
and synchronisation between different components of your application. It has
some special guarantees and limitations:

- The directory must support special filesystem objects like named pipes
  and unix sockets.
- Each user has their own runtime directory, and it is only accessible to them.
- Runtime data is not shared between computers, whereas your home directory
  may be shared using something like NFS.
- The directory is deleted when the user logs out, and files not modified in
  six hours may be removed even while logged in
  (set the *sticky bit* to prevent that).
- It may be kept purely in memory, so don't try to store lots of data here.

.. envvar:: XDG_RUNTIME_DIR

  The path of a directory to store runtime data.
  There is no default; if it's not set, the desktop has not set up a runtime
  directory.
