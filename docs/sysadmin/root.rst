============================
Running Commands as ``root``
============================

Some commands or scripts in this manual are intended to be run as ``root``. This section describes two methods for doing so.

-------------------------------------------------
Running Commands as ``root`` With :program:`sudo`
-------------------------------------------------

If you are logged in as a user who can run commands as ``root`` via :program:`sudo`, simply add the following in front of the command listed in the manual [#fn1]_:

.. code-block:: shell

   sudo ...

For example, if the command listed in the manual is ``iptables -F``, you would type ``sudo iptables -F``.

-------------------------------------
Running Commands Directly as ``root``
-------------------------------------

If you are logged in as ``root`` directly, you can simply run the command as listed in the manual, for example ``iptables -F``.

----

.. rubric:: Footnotes

.. [#fn1]

   Depending on your system's :program:`sudo` configuration, you may be prompted for the user's :program:`sudo` password.
