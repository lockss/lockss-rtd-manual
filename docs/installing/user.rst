============================
Creating the ``lockss`` User
============================

The LOCKSS system runs under a system user named ``lockss``, which is in a system group named ``lockss``.

-----------------------------------------------------------------
Creating the ``lockss`` User With :program:`useradd`
-----------------------------------------------------------------

To create the ``lockss`` user and group, run this :program:`useradd` command (as ``root`` or with :program:`sudo`):

.. code-block:: shell

   useradd --system --user-group --create-home --shell=/bin/false lockss

.. _run-as-lockss:

---------------------------------------
Running Commands as the ``lockss`` User
---------------------------------------

Unless otherwise noted, most commands in this manual are intended to be run as the ``lockss`` user.

*  If you are logged in as a non-``root`` user with access to :program:`sudo`:

   *  You can use :program:`sudo` to start a Bash shell session as the ``lockss`` user.

      1. Run this command:

         .. code-block:: shell

            sudo -u lockss /bin/bash

         Depending on your system's :program:`sudo` configuration, you may be prompted for your :program:`sudo` password.

      2. Run commands as they are listed in the manual, for example:

         .. code-block:: shell

            scripts/start-lockss

      3. When you are done, exit the ``lockss`` shell session by typing ``exit`` or ``logout`` or hitting :kbd:`Ctrl + D`.

   *  Alternatively, you can use :program:`sudo` to run a single command as the ``lockss`` user. Add ``sudo -u lockss`` in front of the command listed in the manual. For example, if the command to be run as the ``lockss`` user is ``scripts/start-lockss``, you would type:

      .. code-block:: shell

         sudo -u lockss scripts/start-lockss

      Depending on your system's :program:`sudo` configuration, you may be prompted for your :program:`sudo` password.

*  If you are logged in as ``root``:

*FIXME later*

*  Some systems with :program:`sudo` installed are configured so that ``root`` can use :program:`sudo` without a password, in which case you can use the options above.

*  Start a Bash shell session as the ``lockss`` user by typing :samp:`su -s /bin/bash lockss`. Use the shell session as long as needed, then exit by typing :samp:`exit`.

*  Run a single command as the ``lockss`` user by typing :samp:`sudo -s /bin/bash -c '{/path/to/somecommand --with arguments}' lockss`. Note the quotation marks for the :samp:`-c` argument.
