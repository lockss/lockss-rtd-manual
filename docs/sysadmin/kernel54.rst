======================================
Upgrading to Linux Kernel 5.4 or Later
======================================

In the Linux kernel version 5.3 or earlier, |LOCKSS| at startup might block [#fn-block]_ or hang [#fn-hang]_ due to lack of entropy [#fn-entropy]_ in the Linux environment. Mitigation of this problem first appeared in Linux kernel version 5.4 [#fn-mitigation]_. Therefore, :ref:`prerequisites-kernel54` to run LOCKSS. Most versions of the :ref:`Compatible Operating Systems` satisfy this requirement out of the box. This section describes how to upgrade certain operating systems to Linux kernel 5.4 or later.

.. include:: kernel54-tip.rst

.. include:: kernel54-test.rst

If an upgrade to Linux kernel version 5.4 or later is required, select your operating system below, and if applicable select the particular version of your operating system, then follow the instructions accordingly:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: almalinux-os

      .. tab-set::

         .. tab-item:: AlmaLinux OS 8
            :sync: almalinux-os-8

            .. include:: kernel54-elrepo.rst

         .. tab-item:: AlmaLinux OS 9
            :sync: almalinux-os-9

            .. include:: kernel54-none.rst

         .. tab-item:: AlmaLinux OS 10
            :sync: almalinux-os-10

            .. include:: kernel54-none.rst

   .. tab-item:: Arch Linux
      :sync: arch-linux

      .. include:: kernel54-none.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: kernel54-none.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: kernel54-none.rst

   .. tab-item:: Fedora Linux
      :sync: fedora-linux

      .. include:: kernel54-none.rst

   .. tab-item:: Linux Mint
      :sync: linux-mint

      .. include:: kernel54-none.rst

   .. tab-item:: OpenSUSE Leap
      :sync: opensuse-leap

      .. include:: kernel54-none.rst

   .. tab-item:: OpenSUSE Tumbleweed
      :sync: opensuse-tumbleweed

      .. include:: kernel54-none.rst

   .. tab-item:: Oracle Linux
      :sync: oracle-linux

      .. tab-set::

         .. tab-item:: Oracle Linux 8
            :sync: oracle-linux-8

            .. include:: kernel54-uek.rst

         .. tab-item:: Oracle Linux 9
            :sync: oracle-linux-9

            .. include:: kernel54-none.rst

         .. tab-item:: Oracle Linux 10
            :sync: oracle-linux-10

            .. include:: kernel54-none.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. tab-set::

         .. tab-item:: Red Hat Enterprise Linux 8
            :sync: rhel-8

            .. include:: kernel54-elrepo.rst

         .. tab-item:: Red Hat Enterprise Linux 9
            :sync: rhel-9

            .. include:: kernel54-none.rst

         .. tab-item:: Red Hat Enterprise Linux 10
            :sync: rhel-10

            .. include:: kernel54-none.rst

   .. tab-item:: Rocky Linux
      :sync: rocky-linux

      .. tab-set::

         .. tab-item:: Rocky Linux 8
            :sync: rocky-linux-8

            .. include:: kernel54-elrepo.rst

         .. tab-item:: Rocky Linux 9
            :sync: rocky-linux-9

            .. include:: kernel54-none.rst

         .. tab-item:: Rocky Linux 10
            :sync: rocky-linux-10

            .. include:: kernel54-none.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: kernel54-none.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: kernel54-none.rst

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
