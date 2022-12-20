=====================================
Running Commands as a Privileged User
=====================================

Some commands or scripts in this manual are intended to be run **as a privileged user** who can become ``root`` and ``lockss`` via :program:`sudo`.

Compared to running an entire command or script directly as ``root``, this approach has the security advantage of being granular -- only those portions of the command or script that require ``root`` privileges will have ``root`` privileges, and only those commands that need to read or write files as the ``lockss`` user will be run as the ``lockss`` user.

To run a command in this context, simply type the command listed in the manual. Depending on your system's :program:`sudo` configuration, you may be prompted for the user's :program:`sudo` password.
