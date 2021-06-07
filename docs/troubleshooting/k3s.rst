===================
Troubleshooting K3s
===================

-----------------------------------
Running :program:`k3s check-config`
-----------------------------------

After installing K3s with :program:`install-k3s` [#fn1]_, run the following command as ``root`` [#fnroot]_:

.. code-block:: shell

   k3s check-config

This tool runs through a more extensive series of tests, covering "required", "generally necessary", and "optional" aspects for K3s to operate.

As a rule of thumb, if :program:`k3s check-config` ends successfully with ``STATUS: pass``, there is a good chance the K3s cluster is configured correctly.

Some failures, especially in "optional" aspects, may not prevent the cluster from working normally in the limited ways the LOCKSS system uses Kubernetes, but if possible they should be addressed. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message:

iptables v1.8.4 (nf_tables): should be older than v1.8.0 or in legacy mode (fail):
   This error message may or may not reflect a problem.

   If :program:`check-k3s` ran successfully [#fn2]_, your K3s cluster is probably running normally and you do not need to take any action, even if you receive this error message [#fn3]_.

   If your system is running :program:`iptables` version 1.8.0 or later in ``nf_tables`` mode via Alternatives, as can be the case in some Debian or Ubuntu systems, :program:`iptables` needs to be switched to ``legacy`` mode via Alternatives. The :program:`configure-firewall` script called by :program:`install-k3s` is supposed to detect this condition and offer to fix it for you [#fn1]_.

RHEL7/CentOS7: User namespaces disabled; add 'user_namespace.enable=1' to boot command line
   To resolve this issue sometimes ecountered in the RHEL/CentOS family of operating systems [#fn4]_:

   1. Edit the file :file:`/etc/default/grub` as ``root`` [#fnroot]_.

      1. Look for the line beginning with ``GRUB_CMDLINE_LINUX=``, for example:

         .. code-block:: text

            GRUB_CMDLINE_LINUX="no_timer_check console=tty0 console=ttyS0,115200n8 net.ifnames=0 biosdevname=0 elevator=noop crashkernel=auto"

      2. Add ``user_namespace.enable=1`` to the space-separated list of boot arguments, for instance:

         .. code-block:: text

            GRUB_CMDLINE_LINUX="no_timer_check console=tty0 console=ttyS0,115200n8 net.ifnames=0 biosdevname=0 elevator=noop crashkernel=auto user_namespace.enable=1"

   2. Reboot the system.

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
