.. rubric:: Adjusting :program:`ufw`

If :program:`iptables` is present on your system, it may be used by :program:`ufw`, a firewall that will need an adjustment for K3s to run properly.

It is relatively easy to add firewall rules to run K3s with :program:`ufw`.

1. Check if :program:`ufw` is installed and active, by running this command as ``root`` [#fnroot]_ :

   .. code-block:: shell

      ufw status

2. If :program:`ufw` exists and reports it is active, run these commands as ``root`` [#fnroot]_ :

   .. code-block:: shell

      ufw allow from 10.42.0.0/16 to any

      ufw allow from 10.43.0.0/16 to any

      ufw reload
