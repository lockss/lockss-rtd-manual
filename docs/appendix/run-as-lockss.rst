=======================================
Running Commands as the ``lockss`` User
=======================================

Unless otherwise noted, most commands in this manual are intended to be run as the ``lockss`` user. This section describes how to run commands as the ``lockss`` user.

.. contents:: Topic Overview
   :local:
   :depth: 1

--------------------------------
User With :program:`sudo` Access
--------------------------------

This section describes how to run commands as the ``lockss`` user if you are logged in as a user (``root`` or non-``root``) with access to :program:`sudo`.

*  You can use :program:`sudo` to start a Bash shell session as the ``lockss`` user and run any number of commands:

   1. Run this command [#fn1]_ :

      .. code-block:: shell

         sudo -u lockss /bin/bash

   2. Run commands as they are listed in the manual, for example:

      .. code-block:: shell

         scripts/start-lockss

   3. When you are done, exit the ``lockss`` shell session by typing ``exit`` or ``logout`` or hitting :kbd:`Ctrl + D`.

*  Alternatively, you can use :program:`sudo` to run a single command as the ``lockss`` user:

   1. Add the following in front of the command listed in the manual [#fn1]_ :

      .. code-block:: shell

         sudo -u lockss ...

      For example, if the command to be run as the ``lockss`` user is ``scripts/start-lockss --wait``, you would type:

      .. code-block:: shell

         sudo -u lockss scripts/start-lockss --wait

---------------------------------------
``root`` Without :program:`sudo` Access
---------------------------------------

This section describes how to run commands as the ``lockss`` user if you are logged in as ``root`` but your system does not have :program:`sudo` or does not let ``root`` access :program:`sudo`.

is not set up to let ``root`` access :program:`sudo`

*  You can use :program:`su` to start a Bash shell session as the ``lockss`` user and run any number of commands:

   1. Type this command:

      .. code-block:: shell

         su -s /bin/bash lockss

   2. Run commands as they are listed in the manual, for example:

      .. code-block:: shell

         scripts/start-lockss

   3. When you are done, exit the ``lockss`` shell session by typing ``exit`` or ``logout`` or hitting :kbd:`Ctrl + D`.

*  Alternatively, you can use :program:`su` to run a single command as the ``lockss`` user:

   1. Put the command listed in the manual in quotation marks in the following command:

      .. code-block:: shell

         su -s /bin/bash -c '...'

      For example, if the command to be run as the ``lockss`` user is ``scripts/start-lockss --wait``, you would type:

      .. code-block:: shell

         su -s /bin/bash -c 'scripts/start-lockss --wait'

      You will need to take care if the command itself contains single quotation marks [#fn2]_ .

----

.. rubric:: Footnotes

.. [#fn1]

   Depending on your system's :program:`sudo` configuration, you may be prompted for the user's :program:`sudo` password.

.. [#fn2]

   If the command contains single quotation marks but no double quotation marks, use ``-c "..."`` instead of ``-c '...'``. If the command contains a mix of single and double quotation marks, use ``-c "..."`` and also add a backslash in front of each double quotation mark in the command like so: ``\"``.
