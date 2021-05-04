To check if :program:`firewalld` is running, run this command:

.. code-block:: shell

   sudo firewall-cmd --state

If it is not running, enable and start it by running this command:

.. code-block:: shell

   sudo systemctl enable --now firewalld
