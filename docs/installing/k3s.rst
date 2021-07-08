==============
Installing K3s
==============

This section describes how to install K3s.

`K3s <https://k3s.io/>`_ is a lightweight Kubernetes distribution by Kubernetes vendor `Rancher <https://rancher.com/>`_. K3s is compatible with most Linux flavors and comes with a convenient multi-OS installer.

The LOCKSS Installer provides :program:`install-k3s`, a script that streamlines the installation and configuration of K3s for the purposes of running the LOCKSS system. To install, configure and check K3s:

.. _install-k3s:

1. In the ``lockss`` user's :file:`lockss-installer` directory, run the following command [#fnoptions]_ as ``root`` [#fnroot]_:

   .. code-block:: shell

      scripts/install-k3s

   (Typically, this is :file:`/home/lockss/lockss-installer/scripts/install-k3s`.)

2. The :program:`install-k3s` script is capable of detecting a variety of problematic situations with :program:`iptables`, :program:`firewalld`, and :program:`ufw` (firewall). If applicable, :program:`install-k3s` will display warning messages and prompt you to confirm before taking corrective action. Enter :kbd:`Y` for "yes" and :kbd:`N` for "no", or simply hit :kbd:`Enter` to accept the proposed answer (displayed in square brackets).

   .. caution::

      If you opt out of the proposed remediations, :program:`install-k3s` will proceed, but K3s is likely to malfunction without external intervention.

   .. admonition:: Troubleshooting

      For details, see:

      *  :doc:`/troubleshooting/iptables`

      *  :doc:`/troubleshooting/firewalld`

      *  :doc:`/troubleshooting/ufw`

3. The :program:`install-k3s` script is also capable of detecting a problematic situation with DNS resolution. If applicable, :program:`install-k3s` will display a warning message and the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses. A suggested default will be offered to you in square brackets, consisting of non-loopback addresses collected from your machine's :file:`resolv.conf` files; you can simply hit :kbd:`Enter` to accept the suggested default.

   .. admonition:: Troubleshooting

      For details, see :doc:`/troubleshooting/coredns`.

4. You will be prompted for a K3s state data directory:

   :guilabel:`K3s state data directory: [/var/lib/rancher/k3s]`

   K3s stores state data in :file:`/var/lib/rancher/k3s` by default, but if :file:`/var` is space-limited, you should specify a different directory as the K3s state data directory will grow to at least 5-10GB. Enter a directory path of your choice followed by :kbd:`Enter`, or simply hit :kbd:`Enter` to accept the default.

5. If `Rancher's K3s install script <https://get.k3s.io>`_ (which is invoked by :program:`install-k3s`) cannot recover from an error condition, it may display an error message with a suggested remediation before exiting. If applicable, perform the recommended action and re-run :program:`install-k3s`.

   .. admonition:: Troubleshooting

      For details, see :ref:`Troubleshooting the K3s Installer`.

.. _check-k3s:

6. The LOCKSS Installer provides :program:`check-k3s`, a tool to check that K3s is running and resolving DNS names properly. In the ``lockss`` user's :file:`lockss-installer` directory, run this command as the ``lockss`` user [#fnlockss]_:

   .. code-block:: shell

      scripts/check-k3s

   If all tests succeed, the last line of output will be ``STATUS: pass``.

   .. admonition:: Troubleshooting

      If :program:`check-k3s` fails (for example ``STATUS: fail`` or ``STATUS: fail (3 errors)``) or keeps retrying the same step many times without succeeding, see :doc:`/troubleshooting/k3s`.

.. _k3s-check-config:

7. K3s comes with :program:`k3s check-config`, a configuration and system checker. Run the following command as ``root`` [#fnroot]_:

   .. code-block:: shell

      k3s check-config

   If all tests succeed, the last line of output will be ``STATUS: pass``.

   .. important::

      On some operating systems, this checker may report an :program:`iptables` error message similar to ``iptables v1.8.4 (nf_tables): should be older than v1.8.0 or in legacy mode (fail)``, even though nothing is wrong. This is a known bug in the version of K3s used by LOCKSS 2.0-alpha4. If :program:`check-k3s` ran successfully previously, you may ignore this spurious error message. For details, see :ref:`iptables should be older than v1.8.0 or in legacy mode`.

   .. admonition:: Troubleshooting

      If this checker fails (for example ``STATUS: 1 (fail)``), see :ref:`Troubleshooting the K3s Configuration Checker`.

----

.. rubric:: Footnotes

.. [#fnoptions]

   If you invoke :program:`install-k3s` with the option :samp:`--k3s-data-dir={DATADIRPATH}`, the directory path :samp:`{DATADIRPATH}` will be used as your answer to the K3s state data directory question without an interactive prompt.

   If you invoke :program:`install-k3s` with the option ``--assume-yes``, :program:`install-k3s` will assume that the answer to every interactive yes/no question is :kbd:`Y` for "yes", and that the answer to the K3s state data directory question is the default :file:`/var/lib/rancher/k3s` (unless you also used the ``--k3s-data-dir``, which takes precedence).

.. [#fnroot]

   See :doc:`/appendix/root`.

.. [#fnlockss]

   See :doc:`/appendix/lockss`.
