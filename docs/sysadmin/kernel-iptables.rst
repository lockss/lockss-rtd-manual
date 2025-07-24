=========================================================================
Installing the ``ip_tables`` Loadable Kernel Module in the RHEL 10 Family
=========================================================================

K3s, the Kubernetes distribution used by LOCKSS |LATEST_MINOR|, uses its own embedded :program:`iptables`, but this in turns requires the ``ip_tables`` loadable kernel module, even if :program:`iptables` or :program:`nftables` is not installed on the host machine.

Most versions of the :ref:`Compatible Operating Systems` satisfy this requirement out of the box, but some operating systems, especially in the RHEL 10 family (:ref:`os-almalinux` 10, :ref:`os-oracle-linux` 10, :ref:`os-rhel` 10, and :ref:`os-rocky-linux` 10), may not. This section describes how to install a software package that will make the ``ip_tables`` loadable kernel module available on an OS in the RHEL 10 family.

Type ``modinfo ip_tables`` at the host's command line. If an error message similar to ``modinfo: ERROR: Module ip_tables not found.`` is output, follow these steps (as ``root``):

1. Run this :program:`dnf` command:

   .. code-block:: shell

      dnf install kernel-modules-extra

2. Run this :program:`modprobe` command:

   .. code-block:: shell

      modprobe ip_tables

   .. note::

      Note that in this context, the correct name is ``ip_tables``, not ``iptables`` as in many other contexts.
