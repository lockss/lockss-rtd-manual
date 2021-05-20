=====================================
Running Commands as a Privileged User
=====================================

Some commands or scripts in this manual are intended to be run as a privileged user who can become ``root`` via :program:`sudo`. (You may be prompted for the user's :program:`sudo` password during their execution.)

Compared to running an entire command or script directly as ``root`` (see :doc:`root`), this approach has the security advantage of being granular -- only those portions of the command or script that require ``root`` privileges will have ``root`` privileges.
