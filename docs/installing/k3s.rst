==============
Installing K3s
==============

`K3s <https://k3s.io/>`_ is a certified `Kubernetes <https://kubernetes.io/>`_ distribution by `Rancher <https://rancher.com/>`_.

------------------------------
Running :program:`install-k3s`
------------------------------

The LOCKSS Installer provides :program:`install-k3s`, a script that streamlines the installation and configuration of K3s for the purposes of running the LOCKSS system. To install and configure K3s with :program:`install-k3s`:

1. Run the following script (found in the :file:`lockss-installer` directory) as ``root`` [#fnroot]_:

   .. code-block:: shell

      scripts/install-k3s

   Typically, this means running ``/home/lockss/lockss-installer/scripts/install-k3s`` as root [#fnroot]_.

2. If your system is running :program:`iptables` version 1.8.0 in ``nf_tables`` mode via the alternatives mechanism, it needs to be switched to ``legacy`` mode via alternatives. If :program:`install-k3s` detects that this is necessary, you will see the prompt:

   :guilabel:`Switch iptables to legacy mode via alternatives?`

   Enter :kbd:`Y` to perform the change.

   .. caution::

      If you opt out of this change, :program:`install-k3s` will continue but K3s is likely to malfunction without external intervention. If the requisite conditions are present, the remediation attempted by :program:`install-k3s` is equivalent to:

      .. code-block:: shell

         update-alternatives --set iptables /usr/sbin/iptables-legacy

         update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy

         update-alternatives --set arptables /usr/sbin/arptables-legacy

         update-alternatives --set ebtables /usr/sbin/ebtables-legacy

         iptables --flush

      References:

      * https://rancher.com/docs/k3s/latest/en/known-issues/

      * https://github.com/k3s-io/k3s/issues/116 (especially https://github.com/k3s-io/k3s/issues/116#issuecomment-624770403)

3. If your system is running the :program:`firewalld` firewall, it is necessary to add the 10.42.0.0/16 and 10.43.0.0/16 subnets to its ``trusted`` zone. If :program:`install-k3s` detects that :program:`firewalld` is running, you will see the prompt:

   :guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

   Enter :kbd:`Y` to perform the change.

   .. caution::

      If you opt out of this change, :program:`install-k3s` will continue but K3s is likely to malfunction without external intervention. The remediation attempted by :program:`install-k3s` is equivalent to:

      .. code-block:: shell

         firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16

         firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16

         firewall-cmd --reload

      For operating systems in the RHEL family (CentOS, Rocky Linux, AlmaLinux...), the action recommended by the K3s manual is to disable :program:`firewalld`, but :program:`install-k3s` takes the lighter approach above, commonly used in the K3s community.

      References:

      * https://github.com/k3s-io/k3s/issues/1556 (especially https://github.com/k3s-io/k3s/issues/1556#issuecomment-604112415)

      * https://rancher.com/docs/k3s/latest/en/installation/installation-requirements/#operating-systems

      * https://rancher.com/docs/k3s/latest/en/advanced/#additional-preparation-for-red-hat-centos-enterprise-linux

4. If your system is running the :program:`ufw` firewall, it is necessary to allow traffic from the 10.42.0.0/16 and 10.43.0.0/16 subnets. If :program:`install-k3s` detects that :program:`ufw` is active, you will see the prompt:

   :guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

   Enter :kbd:`Y` to perform the change.

   .. caution::

      If you opt out of this change, :program:`install-k3s` will continue but K3s is likely to malfunction without external intervention. The remediation attempted by :program:`install-k3s` is equivalent to:

      .. code-block:: shell

         ufw allow from 10.42.0.0/16 to any

         ufw allow from 10.43.0.0/16 to any

         ufw reload

      References:

      * https://github.com/k3s-io/k3s/issues/1280 (especially https://github.com/k3s-io/k3s/issues/1280#issuecomment-663269728)

5. If both :file:`/etc/resolv.conf` and :file:`/run/systemd/resolve/resolv.conf` (files used to list the IP address of DNS servers) contain loopback addresses, CoreDNS (a component of the K3s Kubernetes cluster that handles DNS resolution) will not work properly. If :program:`install-k3s` detects that this is the case, you will see the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of IP addresses of non-loopback DNS servers to use for DNS resolution. A suggested default will be offered to you in square brackets, consisting of all non-loopback addresses collected from your :file:`resolv.conf` file; you can simply hit :kbd:`Enter` to accept the suggested default.

-----------
Testing K3s
-----------

*FIXME future scripts/test-dns or whatever*

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.
