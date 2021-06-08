==============
Installing K3s
==============

`K3s <https://k3s.io/>`_ is a certified `Kubernetes <https://kubernetes.io/>`_ distribution by `Rancher <https://rancher.com/>`_.

------------------------------------------
Installing K3s With :program:`install-k3s`
------------------------------------------

The LOCKSS Installer provides :program:`install-k3s`, a script that streamlines the installation and configuration of K3s for the purposes of running the LOCKSS system. To install and configure K3s with :program:`install-k3s`:

1. In the ``lockss`` user's :file:`lockss-installer` directory, run the following command as ``root`` [#fnroot]_:

   .. code-block:: shell

      scripts/install-k3s

   (Typically, this is :file:`/home/lockss/lockss-installer/scripts/install-k3s`.)

2. If your system is running :program:`iptables` version 1.8.0 or later in ``nf_tables`` mode via Alternatives, as can be the case in some Debian or Ubuntu systems, :program:`iptables` needs to be switched to ``legacy`` mode via Alternatives. If :program:`install-k3s` detects that this is necessary, you will see the prompt:

   :guilabel:`Switch iptables to legacy mode via Alternatives?`

   Enter :kbd:`Y` to perform the change.

   .. caution::

      If you opt out of this change, :program:`install-k3s` will proceed, but K3s is likely to malfunction without external intervention. See :doc:`/troubleshooting/iptables`.

3. If your system is running the :program:`firewalld` firewall, it is necessary to add K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) to :program:`firewalld`'s ``trusted`` zone. If :program:`install-k3s` detects that :program:`firewalld` is running, you will see the prompt:

   :guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

   Enter :kbd:`Y` to perform the change.

   .. caution::

      If you opt out of this change, :program:`install-k3s` will continue but K3s is likely to malfunction without external intervention. See :doc:`/troubleshooting/firewalld`.

4. If your system is running the :program:`ufw` firewall, it is necessary to allow traffic from K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) via :program:`ufw`. If :program:`install-k3s` detects that :program:`ufw` is active, you will see the prompt:

   :guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

   Enter :kbd:`Y` to perform the change.

   .. caution::

      If you opt out of this change, :program:`install-k3s` will continue but K3s is likely to malfunction without external intervention. See :doc:`/troubleshooting/ufw`.

5. If both :file:`/etc/resolv.conf` and :file:`/run/systemd/resolve/resolv.conf` (files used to list the IP address of DNS servers) contain loopback addresses, CoreDNS (a component of the K3s Kubernetes cluster that handles DNS resolution) will not work properly. If :program:`install-k3s` detects that this is the case, you will see the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of IP addresses of non-loopback DNS servers to use for DNS resolution. A suggested default will be offered to you in square brackets, consisting of non-loopback addresses collected from your :file:`resolv.conf` files; you can simply hit :kbd:`Enter` to accept the suggested default.

   .. important::

      If the DNS settings of your system change after K3s is initially installed (for example if DNS servers are added or removed), you will need to run :program:`configure-dns`, a script called by :program:`install-k3s`. See :doc:`/troubleshooting/coredns`.

6. In most cases [#fn6a]_, you will be prompted for a K3s state data directory:

   :guilabel:`K3s state data directory: [/var/lib/rancher/k3s]`

   K3s stores state data in :file:`/var/lib/rancher/k3s` by default, but if :file:`/var` is space-limited, you should specify a different directory as the K3s state data directory will grow to at least 5-10GB. Enter a directory path of your choice followed by :kbd:`Enter`, or simply hit :kbd:`Enter` to accept the default.

7. If Rancher's K3s install script (https://get.k3s.io) cannot recover from an error condition, it may display an error message with a suggested remediation before exiting. If applicable, perform the recommended action and re-run :program:`install-k3s`.

------------
Checking K3s
------------

After :program:`install-k3s` runs successfully, two tools are at your disposal to ensure K3s is configured correctly and operating properly:

1. The LOCKSS Installer provides a tool to help you check that K3s is running and resolving DNS names properly. In the ``lockss`` user's :file:`lockss-installer` directory, run this command as the ``lockss`` user [#fnlockss]_:

   .. code-block:: shell

      scripts/check-k3s

   If all tests succeed, the last line of output will be ``STATUS: pass``.

   .. important::

      If :program:`check-k3s` fails (for example ``STATUS: fail`` or ``STATUS: fail (3 errors)``) or keeps retrying the same step many times without succeeding, see :doc:`/troubleshooting/k3s`.

2. K3s comes with a configuration and system checker, :program:`k3s check-config`. Run the following command as ``root`` [#fnroot]_:

   .. code-block:: shell

      k3s check-config

   If all tests succeed, the last line of output will be ``STATUS: pass``. If some tests fail, the output will be (for example) ``STATUS: 1 (fail)``).

   .. important::

      Generally, when this checker fails, there is something worth investigating and fixing. However in some cases, the checker complains about a problem that has since been resolved in K3s, or that does not actually prevent K3s from working. If this checker fails, see :doc:`/troubleshooting/k3s` for guidance.

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.

.. [#fnlockss]

   See :doc:`/appendix/lockss`.

.. [#fn6a]

   If you invoke :program:`install-k3s` with the option :samp:`--k3s-data-dir={DATADIRPATH}`, the directory path :samp:`{DATADIRPATH}` will be used as your answer with an interactive prompt.

   Otherwise, if you invoke :program:`install-k3s` with the option :samp:`--assume-yes`, the default directory path :file:`/var/lib/rancher/k3s` will be used as your answer without an interactive prompt.
