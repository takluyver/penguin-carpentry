User Interface options
======================

As with many things in the open source world, there are a range of options.
What follows is a summary of the main ones.

Desktop style: GTK or Qt
------------------------

If you want a traditional desktop style application - buttons, menus, toolbars,
and so on, the main options are GTK and Qt. They're written in C and C++
respectively, so you can make very efficient apps, but they also have bindings
to higher-level languages like Python.

If your app will also run on Windows/Mac, go with Qt; its cross platform support
is stronger than GTK. If you're writing just for Linux, it's mostly a matter of
taste. GTK apps look more native in the GNOME desktop, whereas Qt apps fit
better in KDE, but both toolkits work with either desktop.

.. seealso::
  
  `Qt 5 documentation <https://doc.qt.io/qt-5/>`_
  
  `GTK+ 3 reference manual <https://developer.gnome.org/gtk3/stable/>`_
  
  `Python GTK+ 3 tutorial <http://python-gtk-3-tutorial.readthedocs.io/en/latest/index.html>`_
