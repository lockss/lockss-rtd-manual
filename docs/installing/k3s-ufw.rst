This operating system uses :program:`ufw` for firewalling.

It is relatively easy to add firewall rules to run K3s with :program:`ufw`.

1. Check if :program:`ufw` is installed and running, by running this command as ``root`` [#fnroot]_ :

   .. code-block:: shell

      ufw status

2. If :program:`ufw` exists and reports it is running, run these commands as ``root`` [#fnroot]_ :

   .. code-block:: shell

      ufw allow from <node_ip> to any port 6443 *FIXME*

      ufw allow from 10.42.0.0/16 to any

      ufw allow from 10.43.0.0/16 to any

      ufw reload
