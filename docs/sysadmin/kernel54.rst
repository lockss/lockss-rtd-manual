=============================================================
Upgrading to Linux Kernel 5.4 or Greater in the RHEL 8 Family
=============================================================

In the Linux kernel version 5.3 or earlier, the LOCKSS system at startup might block [#fn-block]_ or hang [#fn-hang]_ due to lack of entropy [#fn-entropy]_ in the Linux environment. Mitigation of this problem first appeared in Linux kernel version 5.4 [#fn-mitigation]_. Therefore, Linux kernel 5.4 or later is required to run LOCKSS |LATEST_MINOR|.

Most versions of the :ref:`Compatible Operating Systems` satisfy this requirement out of the box. This section describes how to upgrade operating systems **in the RHEL 8 family** (:ref:`os-almalinux` 8, :ref:`os-oracle-linux` 8, :ref:`os-rhel` 8, and :ref:`os-rocky-linux` 8) to Linux kernel 5.4 or later, as they may be running Linux kernel 5.3 or earlier out of the box.

Type ``uname --kernel-release``, or equivalently ``uname -r``, at the host's command line to see the version of the Linux kernel. If the resulting version is 5.3 or earlier, follow these steps (as ``root``):

1. Import the ELRepo [#fn-elrepo]_ GPG keys with these two :program:`rpm` commands [#fn-elrepo-start]_:

   .. code-block:: shell

      rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

      rpm --import https://www.elrepo.org/RPM-GPG-KEY-v2-elrepo.org

2. Install ELRepo for RHEL 8 with this :program:`yum` command [#fn-elrepo-start]_:

   .. code-block:: shell

      yum install https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm

3. Install the ``kernel-ml`` package from the ``elrepo-kernel`` channel with this :program:`dnf` command [#fn-elrepo-kernel]_:

   .. code-block:: shell

      dnf  --enablerepo=elrepo-kernel --refresh install kernel-ml

4. Reboot the host.

----

.. rubric:: Footnotes

.. [#fn-block]

   Wait exceedingly long.

.. [#fn-hang]

   Wait forever.

.. [#fn-entropy]

   Cryptographically secure randomness sources.

.. [#fn-mitigation]

   See https://git.kernel.org/pub/scm/linux/kernel/git/crng/random.git/commit/?id=50ee7529ec45
                                                                                                                                                    
.. [#fn-elrepo]

   `ELRepo <https://elrepo.org/>`_ is an RPM repository for Enterprise Linux packages, supporting RHEL and operating systems in the RHEL family like AlmaLinux OS, Oracle Linux and Rocky Linux.

.. [#fn-elrepo-start]

   Reference: https://elrepo.org/wiki/doku.php?id=start#get_started

.. [#fn-elrepo-kernel]

   Reference: https://elrepo.org/wiki/doku.php?id=kernel-ml
