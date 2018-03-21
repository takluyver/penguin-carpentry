Launching your application
==========================

Command line
------------

Most applications on Linux can be launched from the command line, even if they
don't run in the terminal. To allow this, you need an executable file in any
of the directories listed in the :envvar:`PATH` environment variable.
These will often end in ``bin``, such as ``/usr/local/bin``.

.. topic:: Executable files
  :class: note
  
  On Unix, an executable file is one with the 'execute bit' set in its
  permissions. You can make a file executable with this command::
    
    chmod +x path/to/file
  
  The file should be either a compiled 'binary', or a text script. Scripts need
  to start with a 'shebang', a line that identifies the interpreter to run
  the script with. For example::
    
    #!/usr/bin/python3

The command is the filename. By convention, it should be lower case. If you
want to use more than one word, separate them with hyphens, e.g.
``chromium-browser``.

.. _desktop-file:

Desktop launcher
----------------

To add your application to the desktop launcher or applications menu, you need
a desktop entry file, with a ``.desktop`` extension. It contains something like
this::
  
  [Desktop Entry]
  Version=1.0
  Type=Application
  
  # The name will be displayed
  Name=Inkscape
  # Translations are possible: they're used depending on the system locale
  Name[hi]=इंकस्केप
  
  # See the icon section for how this is looked up.
  Icon=inkscape
  
  # The command to launch your application. %F is for file paths to open.
  Exec=inkscape %F
  
  # File types it can open; see file associations.
  MimeType=image/svg+xml;...

Your application's desktop entry is also used for
:doc:`file association <file-associations>`.

There are a number of other optional fields you can use. See the links below
for more information.

These desktop files are placed in an ``applications`` subdirectory of each XDG
data directory. If you have to put it in place yourself, the normal locations
are:

* Per-user: ``~/.local/share/applications``
* System: ``/usr/local/share/applications``

.. seealso::
  
  `GNOME developer guide to desktop files <https://developer.gnome.org/integration-guide/stable/desktop-files.html.en>`_
  
  `Desktop Entry Specification <https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html>`_
