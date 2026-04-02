.. tip::

   Only version 8 of this operating system is expected to require an upgrade to Linux kernel version 5.4 or later. Versions 9 and 10 of this operating system are expected to ship with newer Linux kernel versions out of the box. Confirm from above that the kernel upgrade is required before proceeding.

If an upgrade to Linux kernel 5.4 or later is required for your version of this operating system, you will need to install a kernel from the `ELRepo Project <https://elrepo.org/>`_. Follow these steps (as ``root``):

1. Import the ELRepo Project GPG keys with these two :program:`rpm` commands (as ``root``):

   .. code-block:: shell

      rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

      rpm --import https://www.elrepo.org/RPM-GPG-KEY-v2-elrepo.org

   Reference: https://elrepo.org/wiki/doku.php?id=start#get_started

2. Install the ``elrepo-release`` package for RHEL 8 with this :program:`yum` command (as ``root``):

   .. code-block:: shell

      yum install https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm

   Reference: https://elrepo.org/wiki/doku.php?id=start#get_started

3. Install the ``kernel-ml`` package from the ``elrepo-kernel`` channel with this :program:`dnf` command (as ``root``):

   .. code-block:: shell

      dnf  --enablerepo=elrepo-kernel --refresh install kernel-ml

   Reference: https://elrepo.org/wiki/doku.php?id=kernel-ml

4. Reboot the host.
