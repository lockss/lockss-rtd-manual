===================
Troubleshooting K3s
===================

This section offers troubleshooting information when the K3s installer or the K3s ocnfiguration checker fail.

----------------------------
When the K3s Installer Fails
----------------------------

The LOCKSS Installer's :program:`install-k3s` script installs K3s by executing `Rancher's official K3s installer <https://get.k3s.io/>`_ after making sure many firewall and DNS issues are resolved [#fn1]_. However, the installer can still run into issues and fail. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message:

Failed to apply container_runtime_exec_t to /usr/local/bin/k3s
   In some Fedora systems, you may see an error message similar to the following:

   .. code-block:: text

      [ERROR]  Failed to apply container_runtime_exec_t to /usr/local/bin/k3s, please install:
          yum install -y container-selinux selinux-policy-base
          yum install -y https://rpm.rancher.io/k3s/stable/common/centos/7/noarch/k3s-selinux-0.2-1.el7_8.noarch.rpm

   The specific commands and version numbers may vary from the example above.

   To resolve this problem:

   1. Run the recommended commands as ``root`` [#fnroot]_.

   2. Re-run :program:`install-k3s`.

Package k3s-selinux (rancher-k3s-common-stable) requires container-selinux
   In some Oracle Linux 7 systems, you may see an error message similar to the following:

   .. code-block:: text

      Error: Package: k3s-selinux-0.3-0.el7.noarch (rancher-k3s-common-stable)
                 Requires: container-selinux >= 2.107-3
       You could try using --skip-broken to work around the problem
       You could try running: rpm -Va --nofiles --nodigest

   The specific commands and version numbers may vary from the example above. This can occur in environments where the Oracle Linux 7 Addons Yum repository is not enabled by default, so Rancher's official K3s installer is unable to install the package ``container-selinux`` automatically.

   To resolve this problem:

   1. Run the following command as ``root`` [#fnroot]_:

      .. code-block:: shell

         yum-config-manager --enable ol7_addons

   2. Re-run :program:`install-k3s`.

----------------------------------------
When the K3s Configuration Checker Fails
----------------------------------------

After installing K3s with :program:`install-k3s` [#fn1]_ and successfully running :program:`check-k3s` [#fn2]_, you can run the following command as ``root`` [#fnroot]_:

.. code-block:: shell

   k3s check-config

This configuration checker runs through a more extensive series of tests, covering "required", "generally necessary", and "optional" aspects for K3s to operate.

As a rule of thumb, if :program:`k3s check-config` ends successfully with ``STATUS: pass``, there is a good chance the K3s cluster is configured correctly.

Some failures, especially in "optional" aspects, may not prevent the cluster from working normally in the limited ways the LOCKSS system uses Kubernetes, but if possible they should be addressed. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message:

.. _k3s-iptables180:

iptables v1.8.4 (nf_tables): should be older than v1.8.0 or in legacy mode (fail)
   This error message is generally spurious, because the LOCKSS Installer should have previously detected and offered to correct this issue in the circumstances where it applies, and Rancher has a documented bug report that the K3s configuration checker keeps reporting this issue even in circumstances where it does not apply [#fn3]_.

   If :program:`check-k3s` ran successfully [#fn2]_, your K3s cluster is probably running normally and you can ignore this error message even if you receive it.

   If your system is running :program:`iptables` version 1.8.0 or later in ``nf_tables`` mode via Alternatives, as can be the case in some Debian or Ubuntu systems, :program:`iptables` needs to be switched to ``legacy`` mode via Alternatives. The :program:`configure-firewall` script called by :program:`install-k3s` is supposed to detect this condition and offer to fix it for you [#fn1]_. See :doc:`/troubleshooting/iptables`.

.. _k3s-usernamespace:

RHEL7/CentOS7: User namespaces disabled; add 'user_namespace.enable=1' to boot command line
   To resolve this issue sometimes ecountered in the RHEL/CentOS family of operating systems [#fn4]_:

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

.. _k3s-swap:

swap: should be disabled
   This warning can be ignored.

.. _k3s-configinetxfrmmodetransport:

CONFIG_INET_XFRM_MODE_TRANSPORT: missing
   This warning can be ignored.

----

.. rubric:: Footnotes

.. [#fn1]

   See "Installing K3s With :program:`install-k3s`" in :doc:`/installing/k3s`.

.. [#fn2]

   See "Checking K3s" in :doc:`/installing/k3s`.

.. [#fn3]

   References:

   * https://github.com/k3s-io/k3s/issues/2946

.. [#fn4]

   References:

   * https://fortuitousengineer.com/installing-kubernetes-k3s-on-centos-rhel-hosts/

.. [#fnroot]

   See :doc:`/appendix/root`.
