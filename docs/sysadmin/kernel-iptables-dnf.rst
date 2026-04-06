If installing the ``ip_tables`` loadable kernel module is required for this operating system, follow these steps (as ``root``):

1. Run this :program:`dnf` command as ``root``:

   .. code-block:: shell

      dnf install kernel-modules-extra

2. Reboot the host.

3. Run this :program:`modprobe` command as ``root``:

   .. code-block:: shell

      modprobe ip_tables
