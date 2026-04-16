If an upgrade to Linux kernel 5.4 or later is required for this operating system, you will need to install a kernel from the `ELRepo Project <https://elrepo.org/>`_. Follow these steps (as ``root``):

1. First, this method will only work with hosts with a ``x86_64`` architecture. Type this command:

   .. code-block:: shell

      uname --machine

   *  If the output is different from ``x86_64``, then this kernel update method will not work. Please contact us for further assistance.

   *  If the output is ``x86_64``, then proceed to the next step.

2. Import the ELRepo Project GPG keys with these two :program:`rpm` commands (as ``root``):

   .. code-block:: shell

      rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

      rpm --import https://www.elrepo.org/RPM-GPG-KEY-v2-elrepo.org

   Reference: https://elrepo.org/wiki/doku.php?id=start#get_started

3. Install the ``elrepo-release`` package for RHEL 8 with this :program:`yum` command (as ``root``):

   .. code-block:: shell

      yum install https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm

   Reference: https://elrepo.org/wiki/doku.php?id=start#get_started

4. Install the ``kernel-ml`` package from the ``elrepo-kernel`` channel with this :program:`dnf` command (as ``root``):

   .. code-block:: shell

      dnf  --enablerepo=elrepo-kernel --refresh install kernel-ml

   Reference: https://elrepo.org/wiki/doku.php?id=kernel-ml

5. Reboot the host.
