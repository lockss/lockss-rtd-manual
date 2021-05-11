.. rubric:: Adjusting :program:`firewalld`

If :program:`iptables` is present on your system, it may be used by :program:`firewalld`, a firewall that will need an adjustment for K3s to run properly.

Rancher's K3s documentation (as of this writing) recommends disabling :program:`firewalld` altogether. However, it is relatively easy to add firewall rules to run K3s without disabling :program:`firewalld`, and we recommend this approach.

1. Check if :program:`firewalld` is installed and running, by running this command as ``root`` [#fnroot]_ :

   .. code-block:: shell

      firewall-cmd --state

2. If :program:`firewall-cmd` exists and reports :program:`firewalld` is running, run these commands as ``root`` [#fnroot]_ :

   .. code-block:: shell

      firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16

      firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16

      firewall-cmd --reload
