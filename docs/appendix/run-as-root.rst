============================
Running Commands as ``root``
============================

*FIXME this is not really the right title*

Some commands or scripts in this manual are intended to be run as a user that can become ``root`` via :program:`sudo`. (You may be prompted for the user's :program:`sudo` password during their execution.)

This approach has the security advantage that portions of the command or script that do not strictly require ``root`` privileges will be less prone to causing damage if they do not behave as expected for some reason.

Alternatively, you can run such commands or scripts as ``root``, either directly if you are logged in as ``root`` or by invoking the command with :program:`sudo` if you are not. If you proceed in this fashion, all portions of the command or script will have ``root`` privileges.
