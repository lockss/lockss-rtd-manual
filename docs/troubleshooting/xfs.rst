==================================
Troubleshooting OverlayFS with XFS
==================================

This section provides troubleshooting information for the :ref:`check_xfs` phase of :doc:`/installing/installer`.

-------------------------------------------------------------------------
Filesystem backing `/var/lib/rancher` is an XFS filesystem with `ftype=0`
-------------------------------------------------------------------------

The OverlayFS driver used by K3s will fail and prevent containers from starting, if the filesystem backing
``/var/lib/rancher`` is an XFS filesystem configured with the legacy ``ftype=0`` setting that some older Linux systems
defaulted to when creating XFS filesystems. To view or verify the setting of ``ftype`` from an XFS filesystem, use
``xfs_info`` (see step 1 below).

The recommended way fix to this issue is to reformat the XFS filesystem with ``mkfs.xfs`` flag ``-n ftype=1``, or use a
different filesystem type altogether (e.g., ext4). If this is not possible (e.g., because you are performing an in-place
migration from LOCKSS 1.x to 2.x and the filesystem backing ``/var/lib/rancher`` is shared with other parts of the
system), the workaround is to create a new XFS filesystem on another partition or a loopback device backed by a file on
an existing filesystem.

Setup of the latter is described below. Commands should be run as the ``root`` user  [#fnroot]_.

1. (Optional) Verify the existing XFS filesystem has ``ftype=0``:

   .. code-block:: shell

      xfs_info BLOCK_DEVICE

   ...where ``BLOCK_DEVICE`` is the block device of the filesystem backing ``/var/lib/rancher``.

   .. tip::

      Use ``findmnt`` to determine the block device of the filesystem backing ``/var/lib/rancher``:

      .. code-block:: shell

         findmnt --target /var/lib/rancher

      The output should similar to the following (some parameters may be different):

      .. code-block:: text

         TARGET SOURCE           FSTYPE OPTIONS
         /      /dev/mapper/root xfs    rw,relatime,attr2,inode64,logbufs=8,logbsize=32k,noquota

      In the example above, the block device is ``/dev/mapper/root`` (i.e., the ``SOURCE`` column).

   The output from ``xfs_info`` should look similar to the following (some parameters may be different):

   .. code-block:: text

      meta-data=/dev/mapper/root isize=512    agcount=4, agsize=4194304 blks
               =                       sectsz=4096  attr=2, projid32bit=1
               =                       crc=1        finobt=1, sparse=1, rmapbt=0
               =                       reflink=1    bigtime=1 inobtcount=1 nrext64=0
      data     =                       bsize=4096   blocks=16777216, imaxpct=25
               =                       sunit=0      swidth=0 blks
      naming   =version 2              bsize=4096   ascii-ci=0, ftype=0
      log      =internal log           bsize=4096   blocks=16384, version=2
               =                       sectsz=4096  sunit=1 blks, lazy-count=1
      realtime =none                   extsz=4096   blocks=0, rtextents=0

   Note that in the example above, ``ftype=0``.

   .. note::

      If the output contains ``ftype=1``, there is nothing wrong with your XFS filesystem and you should not proceed
      with the instructions on this page!

2. Stop the K3s service:

   .. code-block::

      systemctl stop k3s.service

3. Rename the existing ``/var/lib/rancher`` directory:

   .. code-block:: shell

      mv /var/lib/rancher /var/lib/rancher.backup

4. Allocate a file for the loopback device: This file will contain the XFS filesystem that will hold the K3s runtime
   environment and container images. We recommend allocating a minimum of 16GB. Allocate the file on a filesystem with
   sufficient space.

   .. note::

      In this and the following examples, we allocate and use the file located at ``/var/lib/rancherfs.img``.

   .. code-block:: shell

      fallocate -l 16g /var/lib/rancherfs.img

5. Create a new XFS filesystem with ``ftype`` explicitly set to ``1``:

   .. code-block:: shell

      mkfs.xfs -n ftype=1 /var/lib/rancherfs.img

   You may verify ``ftype=1`` by running:

   .. code-block:: shell

      xfs_info /var/lib/rancherfs.img


6. Mount the loopback to ``/var/lib/rancher``:

   .. code-block:: shell

      mount --mkdir -o loop /var/lib/rancherfs.img /var/lib/rancher

7. Edit ``/etc/fstab`` to make the loopback persistent across reboots: Use your favorite text editor to open
   ``/etc/fstab`` and append the following line to it:

   .. code-block:: text

      /var/lib/rancherfs.img   /var/lib/rancher   xfs   loop   0 0

8. Copy the existing K3s runtime environment to the new XFS filesystem:

   .. code-block:: shell

      cp -r /var/lib/rancher.backup/* /var/lib/rancher/.

9. Finally, restart the K3s service:

   .. code-block:: shell

      systemctl start k3s.service

10. (Optional) If setup of the loopback was successful and K3s is running correctly, you may reclaim space by removing
    ``/var/lib/rancher.backup``:

    .. code-block:: shell

       rm -rf /var/lib/rancher.backup

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
