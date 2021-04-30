To re-enable :program:`firewalld`, you will need to run commands as ``root`` or with :program:`sudo`.

To check if :program:`firewalld` is running, run this command:

.. code-block:: shell

   firewall-cmd --state

If it is not running, enable and start it by running this command:

.. code-block:: shell

   systemctl enable --now firewalld
