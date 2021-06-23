=======================
Troubleshooting CoreDNS
=======================

If both :file:`/etc/resolv.conf` and :file:`/run/systemd/resolve/resolv.conf` (files used to list the IP address of DNS servers) contain loopback addresses, CoreDNS (a component of the K3s Kubernetes cluster that handles DNS resolution) will not work properly [#fn1]_. If :program:`configure-dns` (a script called by :program:`install-k3s`) detects this situation, you will see a warning message and the following prompt [#fn2]_:

:guilabel:`IP address(es) of DNS resolvers, separated by ';'`

Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses. A suggested default will be offered to you in square brackets, consisting of non-loopback addresses collected from your machine's :file:`resolv.conf` files; you can simply hit :kbd:`Enter` to accept the suggested default.

.. tip::

   If the DNS settings of your system change after K3s is initially installed (for example if DNS servers are added or removed), run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/configure-dns

----

.. rubric:: Footnotes

.. [#fn1]

   References:

   *  https://coredns.io/plugins/loop/#troubleshooting-loops-in-kubernetes-clusters

.. [#fn2]

   See :doc:`/installing/k3s`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
