Launching your application
==========================

Command line
------------

Most applications on Linux can be launched from the command line, even if they
don't show output in the terminal. To allow this, you need an executable file in any
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

.. index:: desktop entry
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
:ref:`file association <file-assoc>`.

There are a number of other optional fields you can use. See the links below
for more information.

These desktop files are placed in an ``applications`` subdirectory of each
:ref:`XDG data directory <basedirs-data>`.
If you have to put it in place yourself, the normal locations
are:

* Per-user: ``~/.local/share/applications``
* System: ``/usr/local/share/applications``

.. seealso::
  
  `GNOME developer guide to desktop files <https://developer.gnome.org/integration-guide/stable/desktop-files.html.en>`_
  
  `Desktop Entry Specification <https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html>`_

.. _file-assoc:

File associations
-----------------

To use your application for opening files from the file manager, specify the
details in your :ref:`desktop file <desktop-file>`. In the ``Exec`` field, make
sure your launch command includes a placeholder like ``%F``::

    Exec=inkscape %F

``%F`` may be replaced by one or more file paths. Use lowercase ``%f`` if it can
only handle one path per command. ``%U`` and ``%u`` are similar, but they pass
URLs. Local files have URLs starting ``file://``, but the platform might also 
pass HTTP or FTP URLs to your application.

Then use the ``MimeType`` field to specify what MIME types it handles::

    MimeType=image/svg+xml;image/x-eps;

There may be other applications that support the same MIME type.
It's normally up to the user to pick the default application for a file type,
but if you have a good reason to change it, you can use a ``mimeapps.list``
file as described in the MIME associations specification.

.. seealso::

  `MIME application associations specification
  <https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-latest.html>`_

If the file format you want to open isn't already defined on the system, you'll
need to define a new MIME type for it.

.. _define-mime-type:

Define a MIME type
~~~~~~~~~~~~~~~~~~

A MIME type is meant to be a unique name for a file format, like ``image/png``
or ``text/x-makefile``. For new MIME types, the recommended format is
:samp:`application/vnd.{org_name}.{app_name}`, filling in the
organisation name and app or format name as appropriate (e.g. Libreoffice ODT
files are ``application/vnd.oasis.opendocument.text``). You can add ``+json``
or ``+xml`` to the end if your file format is based on one of these generic
data formats.

MIME types are added to the system with XML files like this:

.. code-block:: xml

  <?xml version="1.0" encoding="UTF-8"?>
  <mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/vnd.acme.frobulate">
        <comment>Frobulate file</comment>
        <glob pattern="*.frobulate"/>
    </mime-type>
  </mime-info>

The ``<glob>`` tag specifies a file extension for files with this MIME type.
Other fields can distinguish different file types sharing the same extension,
but it's best to pick a unique extension. There's no need to limit the extension
to three letters.

The filename of this XML file should start with the vendor name, e.g.
``acme-frobulate.xml``. Call ``xdg-mime install acme-frobulate.xml`` to install
it. This will copy it into a directory such as ``/usr/local/share/mime/packages``,
and rebuild the MIME database from all of these XML source files.

.. seealso::

  `Shared MIME-info database specification
  <https://specifications.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html>`_
