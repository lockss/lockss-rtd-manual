For this family of operating systems, Rancher recommends [#fn2]_ disabling :program:`firewalld`.

Issue the following command as a user with the ability to use :program:`sudo` to run commands as ``root`` [#fn3]_ :

.. code-block:: shell

   sudo firewall-cmd --state

If :program:`firewalld` is running, stop and disable it with this second command:

.. code-block:: shell

   sudo systemctl disable --now firewalld
