User Interface options
======================

As with many things in the open source world, there are a range of options.
What follows is a summary of the main ones.

Desktop style: GTK or Qt
------------------------

If you want a traditional desktop style application - buttons, menus, toolbars,
and so on, the main options are **GTK** and **Qt**. They're written in C and C++
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

Web tech: Electron or browser
-----------------------------

**Electron** is a framework to create desktop applications using HTML and
Javascript. You can easily create attractive, cross platform applications
using familiar web development techniques, and a lot of new applications have
been written with it. But Electron apps tend to use a lot of memory, so there's
a pushback from some users.

A lightweight alternative for some applications is to run a small web server
on localhost and use a browser to display an HTML interface. It's hard to
integrate this nicely with the desktop, though, and you need to pay attention to
security so that other websites open in the browser can't touch it.

.. seealso::
  
  `Electron home page <https://electronjs.org/>`_

Game style
----------

Game interfaces tend to be drawn with a different set of tools. High-performance
graphics will use **OpenGL** or its replacement, **Vulkan**, but there are many
frameworks and engines built around these to provide more convenient APIs, such
as **SDL** and **pygame**.

.. note::
  
  I don't know this area well! If you can expand and improve this section,
  please contribute.
