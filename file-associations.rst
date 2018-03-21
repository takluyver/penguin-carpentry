File associations
=================

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

If the file format you want to open isn't already defined on the system, you'll
need to define a new MIME type for it.

.. _define-mime-type:

Define a MIME type 
------------------

A MIME type is meant to be a unique name for a file format, like ``image/png``
or ``text/x-makefile``. For new MIME types, the recommended format is
:sample:`application/vnd.{org_name}.{app_name}`, filling in the
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

The ``glob`` tag specifies a file extension for files with this MIME type.
Other fields can distinguish different file types sharing the same extension,
but it's best to pick a unique extension. There's no need to limit the extension
to three letters.

The filename of this XML file should start with the vendor name, e.g.
``acme-frobulate.xml``. Call ``xdg-mime install acme-frobulate.xml`` to install
it. This will copy it into a directory such as ``/usr/local/share/mime/packages``,
and rebuild the MIME database from all of these XML source files.
