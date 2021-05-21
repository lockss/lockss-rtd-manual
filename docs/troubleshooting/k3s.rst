===================
Troubleshooting K3s
===================

-----------------------------------
Running :program:`k3s check-config`
-----------------------------------

If :program:`check-k3s` fails after installing K3s with :program:`install-k3s` [#fn1]_, run the following command as the ``lockss`` user [#fnlockss]_:

.. code-block:: shell

   k3s check-config

This tool runs through a more extensive series of tests, covering "required", "generally necessary", and "optional" aspects for K3s to operate.

As a rule of thumb, if :program:`k3s check-config` ends successfully with ``STATUS: pass``, there is a good chance the K3s cluster is configured correctly.

Some failures, especially in "optional" aspects, may not prevent the cluster from working normally in the limited ways the LOCKSS system uses Kubernetes, but if possible they should be addressed. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message:

RHEL7/CentOS7: User namespaces disabled; add 'user_namespace.enable=1' to boot command line
   To resolve this issue sometimes ecountered in the RHEL/CentOS family of operating systems [#fn2]_:

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

   See :ref:`Checking K3s` in :doc:`/installing/k3s`.

.. [#fn2]

   References:

   * https://fortuitousengineer.com/installing-kubernetes-k3s-on-centos-rhel-hosts/

.. [#fnlockss]

   See :doc:`/appendix/lockss`.

.. [#fnroot]

   See :doc:`/appendix/root`.
