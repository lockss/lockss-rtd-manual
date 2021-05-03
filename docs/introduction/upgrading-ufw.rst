To check if :program:`ufw` is running, run this command:

.. code-block:: shell

   sudo ufw status

If it is not running, enable and start it by running this command:

.. code-block:: shell

   sudo systemctl disable --now ufw
