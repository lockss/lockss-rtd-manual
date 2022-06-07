=================================
Troubleshooting the K3s Installer
=================================

The LOCKSS Installer's :program:`install-lockss` script installs K3s by executing Rancher's official K3s Installer from https://get.k3s.io/, after checking that various system, firewall and DNS prerequisites are addressed (see :doc:`/installing/installer`). However, the installation can still run into issues and fail. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up a specific error message.

-----------------------------------------------
Enabling User Namespaces in RHEL 7 and CentOS 7
-----------------------------------------------

K3s requires user namespaces, a feature generally available and enabled in many Linux flavors. However, some RHEL 7 and CentOS 7 systems do not have user namespace enabled by default. This can cause the :ref:`Checking K3s Prerequisites` or :ref:`Testing the K3s Node` phases of :program:`install-lockss` or the optional :ref:`Checking the K3s Configuration` phase to fail.

To resolve this issue in RHEL 7 or CentOS 7 [#fnusernamespaces]_:

1. Edit the file :file:`/etc/default/grub` as ``root`` [#fnroot]_.

   1. Look for the line beginning with ``GRUB_CMDLINE_LINUX=``, for example:

      .. code-block:: text

         GRUB_CMDLINE_LINUX="no_timer_check console=tty0 console=ttyS0,115200n8 net.ifnames=0 biosdevname=0 elevator=noop crashkernel=auto"

      This line defines a space-separated list of boot arguments.

   2. Add ``user_namespace.enable=1`` to the beginning of the space-separated list, for instance:

      .. code-block:: text

         GRUB_CMDLINE_LINUX="user_namespace.enable=1 no_timer_check console=tty0 console=ttyS0,115200n8 net.ifnames=0 biosdevname=0 elevator=noop crashkernel=auto"

2. Run the following command as ``root``:

   .. code-block:: shell

      grub2-mkconfig -o /boot/grub2/grub.cfg

   .. note::

      If EFI is in use, the file to use for the ``-o`` option will not be :file:`/boot/grub2/grub.cfg` exactly. For example on CentOS, it may be :file:`/boot/efi/EFI/centos/grub.cfg`.

3. Reboot the system.

4. Check that the change took effect. To do so, look at the contents of :file:`/proc/cmdline` (for example type ``cat /proc/cmdline``) and verify that it now contains ``user_namespace.enable=1``.

   .. note::

      If the change did not take effect, it could be an indication that a different :file:`grub.cfg` file is needed for the ``-o`` option of :program:`grub2-mkconfig` command above.

.. _installing-apparmor_parser:

-------------------------------------
Installing :program:`apparmor_parser`
-------------------------------------

K3s uses Apparmor in systems where it is enabled. However, some systems, especially OpenSUSE systems, have Apparmor enabled but :program:`apparmor_parser` is not installed by default. This can cause the :ref:`Checking K3s Prerequisites` or :ref:`Installing K3s` phases of :program:`install-lockss` or the optional :ref:`Checking the K3s Configuration` phase to fail.

To resolve this issue in OpenSUSE, run these :program:`zypper` commands as ``root`` [#fnroot]_:

.. code-block:: shell

   zypper refresh

   zypper --non-interactive install apparmor-parser

or equivalently:

.. code-block:: shell

   zypper refresh

   zypper -n install apparmor-parser

.. tip::

   In other Linux flavors, use similar package installation commands.

--------------------------------------------------------------
Failed to apply container_runtime_exec_t to /usr/local/bin/k3s
--------------------------------------------------------------

In some Fedora systems, the K3s installer may fail with an error message similar to the following:

.. code-block:: text

   [ERROR]  Failed to apply container_runtime_exec_t to /usr/local/bin/k3s, please install:
       yum install -y container-selinux selinux-policy-base
       yum install -y https://rpm.rancher.io/k3s/stable/common/centos/8/noarch/k3s-selinux-0.3-0.el8.noarch.rpm

The specific commands and version numbers may vary from the example above.

To resolve this problem, run the recommended commands as ``root`` [#fnroot]_.

--------------------------------------
k3s-selinux requires container-selinux
--------------------------------------

In some Oracle Linux 7 systems, you may see an error message similar to the following:

.. code-block:: text

   Error: Package: k3s-selinux-0.3-0.el7.noarch (rancher-k3s-common-stable)
              Requires: container-selinux >= 2.107-3
    You could try using --skip-broken to work around the problem
    You could try running: rpm -Va --nofiles --nodigest

The specific commands and version numbers may vary from the example above.

This can occur in environments where the Oracle Linux 7 Addons Yum repository is not enabled by default, so Rancher's official K3s installer is unable to install the package ``container-selinux`` automatically.

To resolve this problem in Oracle Linux 7, run the following command as ``root`` [#fnroot]_:

.. code-block:: shell

   yum-config-manager --enable ol7_addons

----

.. rubric:: Footnotes

.. [#fnusernamespaces]

   References:

   *  https://fortuitousengineer.com/installing-kubernetes-k3s-on-centos-rhel-hosts/

.. [#fnroot]

   See :doc:`/sysadmin/root`.
