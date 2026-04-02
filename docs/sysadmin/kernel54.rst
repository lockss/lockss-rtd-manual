======================================
Upgrading to Linux Kernel 5.4 or Later
======================================

In the Linux kernel version 5.3 or earlier, |LOCKSS| at startup might block [#fn-block]_ or hang [#fn-hang]_ due to lack of entropy [#fn-entropy]_ in the Linux environment. Mitigation of this problem first appeared in Linux kernel version 5.4 [#fn-mitigation]_. Therefore, :ref:`prerequisites-kernel54` to run LOCKSS.

Most versions of the :ref:`Compatible Operating Systems` satisfy this requirement out of the box. This section describes how to upgrade operating systems **in the RHEL 8 family** (:ref:`os-almalinux-os` 8, :ref:`os-oracle-linux` 8, :ref:`os-rhel` 8, and :ref:`os-rocky-linux` 8) to Linux kernel 5.4 or later, as they may be running Linux kernel 5.3 or earlier out of the box.

You can check the Linux kernel version by typing:

.. code-block:: shell

   uname --kernel-release

or equivalently:

.. code-block:: shell

   uname -r

at the host's console.

*  If version 5.4 or later is output, the host satisfies the Linux kernel version requirement.

*  If version 5.3 or earlier is output, the host does not satify the Linux kernel version requirement.

If an upgrade to Linux kernel version 5.4 or later is required, select your operating system below and follow the instructions:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: almalinux-os

      .. include:: kernel54-elrepo.rst

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

      .. include:: kernel54-uek.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. include:: kernel54-elrepo.rst

   .. tab-item:: Rocky Linux
      :sync: rocky-linux

      .. include:: kernel54-elrepo.rst

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
