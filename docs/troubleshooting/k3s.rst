===================
Troubleshooting K3s
===================

This section offers troubleshooting information when the K3s installer or the K3s configuration checker fail.

---------------------------------
Troubleshooting the K3s Installer
---------------------------------

The LOCKSS Installer's :program:`install-lockss` script installs K3s by executing Rancher's official K3s Installer [#fninstallk3s]_ from https://get.k3s.io/ after making sure various firewall and DNS issues are addressed [#fniptables]_ [#fnfirewalld]_ [#fnufw]_ [#fncoredns]_. However, the installer can still run into issues and fail. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message.

Failed to apply container_runtime_exec_t to /usr/local/bin/k3s
==============================================================

.. COMMENT updated for alpha5

In some Fedora systems, the K3s installer may fail with an error message similar to the following:

.. code-block:: text

   [ERROR]  Failed to apply container_runtime_exec_t to /usr/local/bin/k3s, please install:
       yum install -y container-selinux selinux-policy-base
       yum install -y https://rpm.rancher.io/k3s/stable/common/centos/8/noarch/k3s-selinux-0.3-0.el8.noarch.rpm

The specific commands and version numbers may vary from the example above.

To resolve this problem:

1. Run the recommended commands as ``root`` [#fnroot]_.

2. Re-run :program:`install-lockss` [#fninstalllockss]_.

k3s-selinux requires container-selinux
======================================

.. COMMENT updated for alpha5

In some Oracle Linux 7 systems, you may see an error message similar to the following:

.. code-block:: text

   Error: Package: k3s-selinux-0.3-0.el7.noarch (rancher-k3s-common-stable)
              Requires: container-selinux >= 2.107-3
    You could try using --skip-broken to work around the problem
    You could try running: rpm -Va --nofiles --nodigest

The specific commands and version numbers may vary from the example above.

This can occur in environments where the Oracle Linux 7 Addons Yum repository is not enabled by default, so Rancher's official K3s installer is unable to install the package ``container-selinux`` automatically.

To resolve this problem:

1. Run the following command as ``root`` [#fnroot]_:

   .. code-block:: shell

      yum-config-manager --enable ol7_addons

2. Re-run :program:`install-lockss` [#fninstalllockss]_.

---------------------------------------------
Troubleshooting the K3s Configuration Checker
---------------------------------------------

After installing K3s [#fninstallk3s]_, :program:`install-lockss` runs the K3s configuration checker :program:`k3s check-config` [#fnk3scheckconfig]_. This configuration checker runs through a more extensive series of tests, covering "required", "generally necessary", and "optional" system aspects needed by K3s.

Some failures, especially in "optional" aspects, may not actually prevent the cluster from working normally in the limited ways the LOCKSS system uses Kubernetes. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message.

iptables should be older than v1.8.0, newer than v1.8.3, or in legacy mode
==========================================================================

.. COMMENT updated for alpha5

In some instances, you may encounter an error message similar to the following:

.. code-block:: text

   /usr/sbin iptables v1.8.2 (nf_tables): should be older than v1.8.0, newer than v1.8.3, or in legacy mode (fail)

In previous versions of K3s, this error message was also sometimes phrased as ``should be older than v1.8.0 or in legacy mode``.

The :program:`install-lockss` script should detect this situation and offer to switch :program:`iptables` to legacy mode via Alternatives (see :doc:`iptables`). If the error above occurs:

*  Verify that the :ref:`configuring-iptables` phase of :program:`install-lockss` was not skipped.

*  Verify that, if applicable, the proposed :program:`iptables` configuration changes in the :ref:`configuring-iptables` phase of :program:`install-lockss` were not bypassed.

*  Using the :doc:`iptables` section as reference, verify that the remediation attempted by :program:`install-lockss` has taken effect.

*  Search the `K3s issues database <https://github.com/k3s-io/k3s/issues>`_ for issues related to :program:`k3s check-config`, :program:`iptables` and your operating system.

User namespaces disabled
========================

.. COMMENT updated for alpha5

In the RHEL 7 family of operating systems (CentOS 7, EuroLinux 7, Scientific Linux 7...), you may receive the following error message:

.. code-block:: text

   RHEL7/CentOS7: User namespaces disabled; add 'user_namespace.enable=1' to boot command line (fail)

To resolve this issue [#fnusernamespaces]_:

1. Edit the file :file:`/etc/default/grub` as ``root`` [#fnroot]_.

   1. Look for the line beginning with ``GRUB_CMDLINE_LINUX=``, for example:

      .. code-block:: text

         GRUB_CMDLINE_LINUX="no_timer_check console=tty0 console=ttyS0,115200n8 net.ifnames=0 biosdevname=0 elevator=noop crashkernel=auto"

   2. Add ``user_namespace.enable=1`` to the space-separated list of boot arguments, for instance:

      .. code-block:: text

         GRUB_CMDLINE_LINUX="user_namespace.enable=1 no_timer_check console=tty0 console=ttyS0,115200n8 net.ifnames=0 biosdevname=0 elevator=noop crashkernel=auto"

2. Run the following command as ``root``:

   .. code-block:: shell

      grub2-mkconfig -o /boot/grub2/grub.cfg

3. Reboot the system.

4. Re-run :program:`k3s check-config` [#fnk3scheckconfig]_.

apparmor enabled but apparmor_parser missing
============================================

In some OpenSUSE systems, you may receive the following error:

.. code-block:: text

   apparmor: enabled, but apparmor_parser missing (fail)

This is because a common tool found in most Linux environments is not installed by default in some OpenSUSE versions.

To resolve this issue, run these :program:`zypper` commands as ``root`` [#fnroot]_:

.. code-block:: shell

   zypper refresh

   zypper --non-interactive install apparmor-parser

or equivalently:

.. code-block:: shell

   zypper refresh

   zypper -n install apparmor-parser

cgroup hierarchy nonexistent
============================

.. COMMENT updated for alpha5

In some Arch Linux, Debian and Fedora systems, you may see the following error message:

.. code-block:: text

   cgroup hierarchy: nonexistent?? (fail)

K3s supports ``cgroup2`` but :program:`k3s check-config` version 1.21.5+k3s1 (used in LOCKSS 2.0-alpha5) does not process this condition correctly. **This warning can be ignored.**

links: aux/iptables should link to iptables-detect.sh
=====================================================

.. COMMENT updated for alpha5

In some Fedora and OpenSUSE systems, you may encounter six related error messages like the following:

.. code-block:: text

   links: aux/ip6tables should link to iptables-detect.sh (fail)
   links: aux/ip6tables-restore should link to iptables-detect.sh (fail)
   links: aux/ip6tables-save should link to iptables-detect.sh (fail)
   links: aux/iptables should link to iptables-detect.sh (fail)
   links: aux/iptables-restore should link to iptables-detect.sh (fail)
   links: aux/iptables-save should link to iptables-detect.sh (fail)

This is due to a bug in :program:`k3s check-config` [#fniptablesdetectbug]_, triggered in environments where there is no :program:`iptables` system package installed. **This warning can be ignored.**

swap should be disabled
=======================

**This warning can be ignored:**

.. code-block:: text

   swap: should be disabled

CONFIG_INET_XFRM_MODE_TRANSPORT missing
=======================================

**This warning can be ignored:**

.. code-block:: text

   CONFIG_INET_XFRM_MODE_TRANSPORT: missing

----

.. rubric:: Footnotes

.. [#fninstalllockss]

   See :doc:`/installing/installer`.

.. [#fninstallk3s]

   See :ref:`Installing K3s`.

.. [#fniptables]

   See :ref:`configuring-iptables`.

.. [#fnfirewalld]

   See :ref:`configuring-firewalld`.

.. [#fnufw]

   See :ref:`configuring-ufw`.

.. [#fncoredns]

   See :ref:`Configuring CoreDNS for K3s`.

.. [#fnk3scheckconfig]

   See :ref:`Checking the K3s Configuration`.

.. [#fnk3sbug]

   References:

   *  https://github.com/k3s-io/k3s/issues/2946

.. [#fnusernamespaces]

   References:

   *  https://fortuitousengineer.com/installing-kubernetes-k3s-on-centos-rhel-hosts/

.. [#fniptablesdetectbug]

   Reference:

   *  https://github.com/k3s-io/k3s/issues/4066

      *  https://github.com/k3s-io/k3s/issues/4066#issuecomment-925137706

.. [#fnroot]

   See :doc:`/appendix/root`.
