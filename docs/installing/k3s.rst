==============
Installing K3s
==============

`K3s <https://k3s.io/>`_ is a certified `Kubernetes <https://kubernetes.io/>`_ distribution by `Rancher <https://rancher.com/>`_.

-----------------
Preliminary Steps
-----------------

Select your operating system below to see instructions on how to prepare for the installation of K3s.

.. tabs::

   .. group-tab:: AlmaLinux

      .. include:: k3s-firewalld.rst

   .. group-tab:: Arch Linux

      .. include:: k3s-iptables.rst

   .. group-tab:: CentOS

      .. include:: k3s-firewalld.rst

   .. group-tab:: Debian

      .. include:: k3s-iptables.rst

   .. group-tab:: Fedora

      .. include:: k3s-firewalld.rst

   .. group-tab:: Linux Mint

      .. include:: k3s-iptables.rst
      .. include:: k3s-ufw.rst

   .. group-tab:: OpenSUSE

      .. include:: k3s-firewalld.rst

   .. group-tab:: Oracle Linux

      .. include:: k3s-firewalld.rst

   .. group-tab:: RHEL

      .. include:: k3s-firewalld.rst

   .. group-tab:: Rocky Linux

      .. include:: k3s-firewalld.rst

   .. group-tab:: Ubuntu

      .. include:: k3s-iptables.rst
      .. include:: k3s-ufw.rst

------------------------------------------
Installing K3s With :program:`install-k3s`
------------------------------------------

1. Assuming you are in the :file:`lockss-installer` directory, run the following command  as ``root`` [#fnroot]_ :

   .. code-block:: shell

      scripts/install-k3s

2. CoreDNS, a component of a K3s-based Kubernetes cluster that deals with DNS resolution, does not work with DNS servers that run on a machine's loopback address. If both :file:`/etc/resolv.conf` and :file:`/run/systemd/resolve/resolv.conf` contain loopback addresses, you will see the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of IP addresses of non-loopback DNS servers to use for DNS resolution. A suggested default will be offered to you in square brackets, consisting of all non-loopback addresses collected from your :file:`resolv.conf` file; you can simply hit :kbd:`Enter` to accept it.

----

.. rubric:: Footnotes

.. [#fn1]

   Reference: https://rancher.com/docs/k3s/latest/en/installation/installation-requirements/#operating-systems

.. [#fnroot]

   See :doc:`/appendix/root`.
