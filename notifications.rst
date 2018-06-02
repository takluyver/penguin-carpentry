Notifications
=============

.. image:: _static/notification-example.png
   :align: center

Use desktop notifications to tell the user about something happening while your
app is in the background, e.g. a new message arriving.
On some desktops, notifications can also have clickable buttons.

Use notifications carefully,
because they can easily distract a user who's trying to focus.
The desktop may have controls to disable all notifications from an application,
but you could also offer the user more fine-grained controls.

Wrapper libraries like *libnotify* make it easy to send notifications with a
couple of lines of code. If you need to dig deeper, look at the specification
linked below.

.. seealso::

  `Desktop notifications in Arch Linux wiki <https://wiki.archlinux.org/index.php/Desktop_notifications>`_
  (with examples in many programming languages)

  `Desktop notifications specification <https://developer.gnome.org/notification-spec/>`_
