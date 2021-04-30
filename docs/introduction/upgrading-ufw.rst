To re-enable :program:`ufw`, you will need to run commands as ``root`` or with :program:`sudo`.

To check if :program:`ufw` is running, run this command:

.. code-block:: shell

   ufw status

If it is not running, enable and start it by running this command:

.. code-block:: shell

   systemctl disable --now ufw
