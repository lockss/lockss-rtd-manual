=====================================
Running Commands as a Privileged User
=====================================

Some commands or scripts in this manual are intended to be run as a privileged user who can run commands as ``root`` via :program:`sudo`. (You may be prompted for the user's :program:`sudo` password during their execution.)

This approach has the security advantage that portions of the command or script that do not strictly require ``root`` privileges will be less prone to causing damage if they do not behave as expected for some reason.

Alternatively, you can run such commands or scripts as ``root`` (see :doc:`root`), but all portions of the command or script will have ``root`` privileges.
