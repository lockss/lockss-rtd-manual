============================
Running Commands as ``root``
============================

Some commands or scripts in this manual are intended to be run as ``root``.

.. contents:: Topic Overview
   :local:
   :depth: 1

--------------------------------
User With :program:`sudo` Access
--------------------------------

If you are logged in as a user who can run commands as ``root`` via :program:`sudo`, simply add the following in front of the command listed in the manual [#fn1]_ :

.. code-block:: shell

   sudo ...

For example, if the command to be run as ``root`` is ``iptables -F``, you would type:

.. code-block:: shell

   sudo iptables -F

-------------
``root`` User
-------------

If you are logged in as ``root`` directly, you can simply run the command listed in the manual.

----

.. rubric:: Footnotes

.. [#fn1]

   Depending on your system's :program:`sudo` configuration, you may be prompted for the user's :program:`sudo` password.
