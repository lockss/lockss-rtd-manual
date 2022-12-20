=======================================
Running Commands as the ``lockss`` User
=======================================

Unless otherwise noted, most commands in this manual are intended to be run as the ``lockss`` user (oftentimes in the ``lockss`` user's :file:`lockss-installer` directory). This section describes two methods for doing so.

---------------------------------------------------
Running Commands as ``lockss`` With :program:`sudo`
---------------------------------------------------

If you are logged in as a user who can run commands as ``lockss`` via :program:`sudo`:

*  You can start a Bash shell session as the ``lockss`` user and run any number of commands in it:

   1. Run this command [#fn1]_:

      .. code-block:: shell

         sudo -i -u lockss

      .. tip::

         You can also use the slightly shorter version ``sudo -iu lockss``.

   2. Run commands as they are listed in the manual, for example ``scripts/start-lockss --wait``.

   3. When you are done, exit the ``lockss`` shell session by typing ``exit`` or ``logout`` or hitting :kbd:`Ctrl + D`.

*  Alternatively, you can use :program:`sudo` to run a single command as the ``lockss`` user.

   Add the following in front of the command listed in the manual [#fn1]_:

   .. code-block:: shell

      sudo -u lockss ...

   For example, if the command listed in the manual is ``scripts/start-lockss --wait``, you would type ``sudo -u lockss scripts/start-lockss --wait``.

-------------------------------------------------
Running Commands as ``lockss`` With :program:`su`
-------------------------------------------------

If you are logged in as ``root`` but your system does not have :program:`sudo` (or does not let ``root`` use :program:`sudo`), you can use :program:`su` instead:

*  You can use :program:`su` to start a Bash shell session as the ``lockss`` user and run any number of commands in it:

   1. Type this command:

      .. code-block:: shell

         su lockss

   2. Run commands as they are listed in the manual, for example ``scripts/start-lockss --wait``.

   3. When you are done, exit the ``lockss`` shell session by typing ``exit`` or ``logout`` or hitting :kbd:`Ctrl + D`.

*  Alternatively, you can use :program:`su` to run a single command as the ``lockss`` user:

   Put the command listed in the manual in quotation marks in the following way:

   .. code-block:: shell

      su -c '...' lockss

   For example, if the command to be run as the ``lockss`` user is ``scripts/start-lockss --wait``, you would type ``su -c 'scripts/start-lockss --wait' lockss``.

   .. caution::

      You will need to take care if the command itself contains quotation marks [#fn2]_ .

----

.. rubric:: Footnotes

.. [#fn1]

   Depending on your system's :program:`sudo` configuration, you may be prompted for the user's :program:`sudo` password.

.. [#fn2]

   If the command contains quotation marks, use ``-c "..."`` instead of ``-c '...'``, and add a backslash in front of each double quotation mark in the command (``\"`` instead of ``"``); single quotation marks in the command are unchanged.
