Icons
=====

You probably want to install at least one icon for your application's
:ref:`desktop launcher <desktop-file>`. If you're :ref:`defining a file type
<define-mime-type>` to be used with your application, you'll want an icon
for that too.

Icon file formats
-----------------

Icons on Linux are stored in standard image formats: PNG for bitmap icons,
and SVG for vector icons. You can provide either format, or both.

If you use bitmap icons, you'll need to provide several files with different
resolutions. The most important one for applications and file types is a
48 × 48 pixel square, and 16, 32 and 64 pixel square shapes are also common.
You can provide any other sizes you like, and you can also make double
resolution icons for high-DPI displays - e.g. a double resolution icon for
a 32 pixel square would have 64 × 64 pixels, and may be visually simpler
than a standard 64 × 64 pixel icon.

If a desktop wants to show an icon at a size for which it doesn't have a file,
it will scale another size up or down. It may not look perfect, but the icon
is still clearly recognisable.

File locations
--------------

Icons are organised under an ``icons`` subdirectory of each
:ref:`XDG data directory <basedirs-data>`. So the default locations are:

* Per-user: ``~/.local/share/icons``
* System: ``/usr/local/share/icons``

Within each ``icons`` directory are a number of theme directories.
The only one you need to care about as an application author is ``hicolor``;
this is used whenever the user's preferred theme doesn't have a particular icon.
You can investigate the others if you're keen enough to make several different
versions of each icon.

Within each theme are directories for different icon sizes in pixels,
e.g. ``48x48``.
Vector icons have a separate directory called ``scalable`` at this level.

Within each size directory are different categories. The two most relevant
for application authors are ``apps`` for application icons, and ``mimetypes``
for file types. Finally, these category directories hold the icon files.

So the path of an installed icon file looks something like this::

    /usr/share/icons/hicolor/48x48/apps/firefox.png

.. seealso::

  `Icon theme specification
  <standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html>`_
  
  `Icon naming specification
  <https://specifications.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html>`_

