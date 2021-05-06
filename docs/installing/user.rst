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

---------------------------------------
Running Commands as the ``lockss`` User
---------------------------------------

.. important::

   Unless otherwise noted, commands shown in this manual should be issued as the ``lockss`` user.

If you are a user with :program:`sudo` privileges:

*  Start a Bash shell session as the ``lockss`` user by typing :samp:`sudo -u lockss /bin/bash`. Use the shell session as long as needed, then exit by typing :samp:`exit`.

*  Run a single command as the ``lockss`` user by typing :samp:`sudo -u lockss {/path/to/somecommand --with arguments}`.

If you are the ``root`` user:

*  Some systems with :program:`sudo` installed are configured so that ``root`` can use :program:`sudo` without a password, in which case you can use the options above.

*  Start a Bash shell session as the ``lockss`` user by typing :samp:`su -s /bin/bash lockss`. Use the shell session as long as needed, then exit by typing :samp:`exit`.

*  Run a single command as the ``lockss`` user by typing :samp:`sudo -s /bin/bash -c '{/path/to/somecommand --with arguments}' lockss`. Note the quotation marks for the :samp:`-c` argument.
