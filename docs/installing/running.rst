============================
Running the LOCKSS Installer
============================

.. note::

   Commands in this section are run as ``root``  [#fnroot]_.

**The next task is to run the LOCKSS Installer.**

The installation process goes through various phases:

*  Checking that some prerequisites to install K3s are met. No user interaction is expected.

*  Checking that the ``lockss`` system user and group exist. No user interaction is expected.

*  Configuring :program:`iptables`, :program:`firewalld` and :program:`ufw` for K3s. If applicable, you will be prompted to confirm before your system configuration is modified. You may incidentally be prompted for your :program:`sudo` password.

*  Configuring CoreDNS for K3s. If applicable, you will be prompted to enter non-loopback IP addresses of DNS servers.

*  Installing K3s. If applicable, you will be prompted for a Kubernetes state data storage directory.

*  Testing the K3s node. No user interaction is expected.

After the LOCKSS Installer succeeds, you can also optionally run the K3s Configuration Checker.

-----------------------------
Invoking the LOCKSS Installer
-----------------------------

To start the installation process, run this command (relative to the :ref:`LOCKSS Installer Directory`) as ``root``  [#fnroot]_:

.. code-block:: shell

   scripts/install-lockss

The installer will run through its phases, each of which is described in its own section below from :ref:`Checking K3s Prerequisites` (:numref:`Checking K3s Prerequisites`) to :ref:`Completion of the LOCKSS Installation Process` (:numref:`Completion of the LOCKSS Installation Process`).

.. tip::

   Below are some advanced tips for this section.

   .. dropdown:: Skipping :program:`install-lockss` phases

      You may need to skip some of the phases of :program:`install-lockss`, for example to overcome an incompatibility with the specifics of your host system. If this is necessary, invoke :program:`install-lockss` with one or more of the following options:

      ============================== ================
      Option                         Phase(s) skipped
      ============================== ================
      ``--skip-check-prerequisites`` :ref:`Checking K3s Prerequisites` (:numref:`Checking K3s Prerequisites`)
      ``--skip-check-system-user``   :ref:`Checking the System User and Group` (:numref:`Checking the System User and Group`)
      ``--skip-configure-iptables``  :ref:`configuring-iptables` (:numref:`configuring-iptables`)
      ``--skip-configure-firewalld`` :ref:`configuring-firewalld` (:numref:`configuring-firewalld`)
      ``--skip-configure-ufw``       :ref:`configuring-ufw` (:numref:`configuring-ufw`)
      ``--skip-configure-coredns``   :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`)
      ``--skip-install-k3s``         * :ref:`Checking K3s Prerequisites` (:numref:`Checking K3s Prerequisites`)
                                     * :ref:`configuring-iptables` (:numref:`configuring-iptables`)
                                     * :ref:`configuring-firewalld` (:numref:`configuring-firewalld`)
                                     * :ref:`configuring-ufw` (:numref:`configuring-ufw`)
                                     * :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`)
                                     * :ref:`Installing K3s` (:numref:`Installing K3s`)
      ``--skip-test-k3s``            :ref:`Testing the K3s Node` (:numref:`Testing the K3s Node`)
      ============================== =============

      When a phase is skipped as a result of one of these options, you will see a message similar to this during the corresponding phase:

      .. code-block:: text

          [success] Skipping (--skip-configure-firewalld)

   .. dropdown:: Running only one :program:`install-lockss` phase

      Conversely, you may need to run or re-run only one phase of :program:`install-lockss`, for example re-running the :ref:`Testing the K3s Node` phase after it fails and you perform some troubleshooting. If this is necessary, invoke :program:`install-lockss` with exactly one of the following options:

      ===================================== ==============
      Option                                Phase executed
      ===================================== ==============
      ``--check-prerequisites`` (or ``-P``) :ref:`Checking K3s Prerequisites` (:numref:`Checking K3s Prerequisites`)
      ``--check-system-user``               :ref:`Checking the System User and Group` (:numref:`Checking the System User and Group`)
      ``--configure-iptables`` (or ``-I``)  :ref:`configuring-iptables` (:numref:`configuring-iptables`)
      ``--configure-firewalld`` (or ``-F``) :ref:`configuring-firewalld` (:numref:`configuring-firewalld`)
      ``--configure-ufw`` (or ``-U``)       :ref:`configuring-ufw` (:numref:`configuring-ufw`)
      ``--configure-coredns`` (or ``-C``)   :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`)
      ``--install-k3s`` (or ``-K``)         :ref:`Installing K3s` (:numref:`Installing K3s`)
      ``--test-k3s`` (or ``-T``)            :ref:`Testing the K3s Node` (:numref:`Testing the K3s Node`)
      ===================================== ==============

   .. dropdown:: Running :program:`install-lockss` on auto-pilot

      If you invoke :program:`install-lockss` with the ``--assume-yes`` (or ``-y``) option, it will attempt to run without asking any questions interactively, by assuming that the answer to any yes/no question is "yes" and that the answer to other interactive questions is the suggested default value. This is only appropriate for advanced users who understand the implications of the default code paths in :ref:`configuring-iptables` (:numref:`configuring-iptables`), :ref:`configuring-firewalld` (:numref:`configuring-firewalld`), :ref:`configuring-ufw` (:numref:`configuring-ufw`), :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`) and :ref:`Installing K3s` (:numref:`Installing K3s`) on the host system, for example after previous experience installing the LOCKSS system.

--------------------------
Checking K3s Prerequisites
--------------------------

During this phase, :program:`install-lockss` will check that certain prerequisites to installing K3s are met. This phase begins with this heading:

.. code-block:: text

   Checking K3s prerequisites...

No user interaction is expected; if everything goes well, you will see this message:

.. code-block:: text

   [success] K3s prerequisites checked

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Checking the System User and Group` (:numref:`Checking the System User and Group`).

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: User namespaces must be enabled in RHEL/CentOS 7

      In some RHEL 7 and CentOS 7 systems, user namespaces are not enabled by default. If this is the case, you will see the error message:

      .. code-block:: text

         [ERROR] User namespaces must be enabled in RHEL/CentOS 7; see manual

      and :program:`install-lockss` will fail. See :ref:`Enabling User Namespaces in RHEL 7 and CentOS 7` for troubleshooting, then go back to :ref:`Invoking the LOCKSS Installer` to try again.

   .. dropdown:: Apparmor enabled but :program:`apparmor_parser` missing

      In some systems, Apparmor is enabled but :program:`apparmor_parser` is not installed. If this is the case, you will see the error message:

      .. code-block:: text

         [ERROR] apparmor enabled but apparmor_parser missing; see manual

      and :program:`install-lockss` will fail. See :ref:`installing-apparmor_parser` for troubleshooting, then go back to :ref:`Invoking the LOCKSS Installer` to try again.

----------------------------------
Checking the System User and Group
----------------------------------

During this phase, :program:`install-lockss` will check that the ``lockss`` user and group exist on the host system. This phase begins with the heading:

.. code-block:: text

   Checking the system user and group...

No user interaction is expected; if everything goes well, you will see this message:

.. code-block:: text

   [success] System user and group present

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-iptables` (:numref:`configuring-iptables`).

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: ``lockss`` user or group does not exist

      If the ``lockss`` user or group does not exist on the host system, you will see one of these error messages:

      .. code-block:: text

         [ERROR] The lockss user does not exist

         [ERROR] The lockss group does not exist

      and :program:`install-lockss` will fail. See the :doc:`user` section to create the ``lockss`` user and group, then go back to :ref:`Invoking the LOCKSS Installer` to try again.

.. _configuring-iptables:

---------------------------------------
Configuring :program:`iptables` for K3s
---------------------------------------

During this phase, :program:`install-lockss` will configure :program:`iptables` to work with K3s, if applicable. This phase begins with the heading:

.. code-block:: text

   Configuring iptables for K3s...

In many situations, no configuration of :program:`iptables` is needed; you will see one of these messages:

.. code-block:: text

   [success] Skipping (iptables is not on the PATH nor run via Alternatives)

   [success] Skipping (iptables version is older than 1.8.0)

   [success] Skipping (iptables version is newer than 1.8.3)

   [success] Skipping (iptables is in legacy mode)

   [success] Skipping (iptables is not run via Alternatives)

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-firewalld` (:numref:`configuring-firewalld`).

Otherwise, you will receive the following prompt:

:guilabel:`Switch iptables to legacy mode via Alternatives?`

Enter :kbd:`Y` to accept the proposed :program:`iptables` configuration, or enter :kbd:`N` to bypass, or hit :kbd:`Enter` to accept the default in square brackets [#fnyes]_. (You may be prompted for your :program:`sudo` password.)

.. caution::

   If you choose to bypass the proposed :program:`iptables` configuration, you will see the warning:

   .. code-block:: text

      [Warning] Leaving iptables unchanged; see manual for details

   and :program:`install-lockss` will keep going. But K3s may malfunction without further intervention; see :doc:`/troubleshooting/iptables` for details.

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: :program:`iptables` configuration attempt fails

      If the :program:`iptables` configuration attempt fails, you will see one of these error messages:

      .. code-block:: text

         [ERROR] Error deactivating ufw

         [ERROR] Error applying update-alternatives to iptables

         [ERROR] Error applying update-alternatives to ip6tables

         [ERROR] Error flushing iptables

         [ERROR] Error reactivating ufw

      and :program:`install-lockss` will fail. See :doc:`/troubleshooting/iptables` for remediation details.

.. _configuring-firewalld:

----------------------------------------
Configuring :program:`firewalld` for K3s
----------------------------------------

During this phase, :program:`install-lockss` will configure :program:`firewalld` to work with K3s, if applicable. This phase begins with the heading:

.. code-block:: text

   Configuring firewalld for K3s...

In many situations, no configuration of :program:`firewalld` is needed; you will see one of these messages:

.. code-block:: text

   [success] Skipping (firewall-cmd is not on the PATH)

   [success] Skipping (firewalld is not running)

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-ufw` (:numref:`configuring-ufw`).

Otherwise, you will receive the following prompt:

   :guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

Enter :kbd:`Y` to accept the proposed :program:`firewalld` configuration, or enter :kbd:`N` to bypass, or hit :kbd:`Enter` to accept the default in square brackets [#fnyes]_. (You may be prompted for your :program:`sudo` password.)

.. caution::

   If you choose to bypass the proposed :program:`firewalld` configuration, you will see the warning:

   .. code-block:: text

      [Warning] Leaving firewalld unchanged; see manual for details

   and :program:`install-lockss` will keep going. But K3s may malfunction without further intervention; see :doc:`/troubleshooting/firewalld` for details.

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: :program:`firewalld` configuration attempt fails

      If the :program:`firewalld` configuration attempt fails, you will see one of these error messages:

      .. code-block:: text

         [ERROR] Could not add 10.42.0.0/16 to firewalld's trusted zone

         [ERROR] Could not add 10.43.0.0/16 to firewalld's trusted zone

         [ERROR] Could not reload firewalld

      and :program:`install-lockss` will fail. See :doc:`/troubleshooting/firewalld` for remediation details.

.. _configuring-ufw:

----------------------------------
Configuring :program:`ufw` for K3s
----------------------------------

During this phase, :program:`install-lockss` will configure :program:`ufw` to work with K3s, if necessary. This phase begins with the heading:

.. code-block:: text

   Configuring ufw for K3s...

In many situations, no configuration of :program:`firewalld` is needed; you will see one of these messages:

.. code-block:: text

   [success] Skipping (ufw is not on the PATH)

   [success] Skipping (ufw is not active)

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`).

Otherwise, you will receive the following prompt:

:guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

Enter :kbd:`Y` to accept the proposed :program:`ufw` configuration, or enter :kbd:`N` to bypass, or hit :kbd:`Enter` to accept the default in square brackets [#fnyes]_. (You may be prompted for your :program:`sudo` password.)

.. caution::

   If you choose to bypass the proposed :program:`ufw` configuration, you will see the warning:

   .. code-block:: text

      [Warning] Leaving ufw unchanged; see manual for details

   and :program:`install-lockss` will keep going. But K3s may malfunction without further intervention. See :doc:`/troubleshooting/ufw` for details.

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: :program:`ufw` configuration attempt fails

      If the :program:`ufw` configuration attempt fails, you will see one of these error messages:

      .. code-block:: text

         [ERROR] Could not allow traffic from 10.42.0.0/16 via ufw

         [ERROR] Could not allow traffic from 10.43.0.0/16 via ufw

         [ERROR] Could not reload ufw

      and :program:`install-lockss` will fail. See :doc:`/troubleshooting/ufw` for remediation details.

---------------------------
Configuring CoreDNS for K3s
---------------------------

During this phase, :program:`install-lockss` will configure CoreDNS to work with K3s, if necessary. This phase begins with the heading:

.. code-block:: text

   Configuring CoreDNS for K3s...

In many situations, no configuration of :program:`firewalld` is needed; you will see this message:

.. code-block:: text

   [success] Using system resolv.conf files

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Installing K3s` (:numref:`Installing K3s`).

Otherwise [#fnforcedns]_, you will receive a message including ``CoreDNS does not allow a loopback address to be given to Kubernetes pods as an upstream DNS server``, and the following prompt:

:guilabel:`IP address(es) of DNS resolvers, separated by ';'`

Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses. A suggested value will be offered to you in square brackets, consisting of non-loopback IP addresses collected from your machine's DNS configuration; you can simply hit :kbd:`Enter` to accept the suggested value [#fnyes2]_.

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: CoreDNS configuration attempt fails

      If the CoreDNS configuration attempt fails, you will see one of these error messages:

      .. code-block:: text

         [ERROR] Could not create /etc/lockss

         [ERROR] Error rendering config/templates/k3s/resolv.conf.mustache to config/resolv.conf

         [ERROR] Could not copy config/resolv.conf to /etc/lockss/resolv.conf

      and :program:`install-lockss` will fail. See :doc:`/troubleshooting/coredns` for remediation details.

--------------
Installing K3s
--------------

During this phase, :program:`install-lockss` will install K3s |K3S_PATCH|, if applicable. This phase begins with the heading:

.. code-block:: text

   Installing K3s...

This phase consists of these steps:

1. First, :program:`install-lockss` will determine if K3s |K3S_PATCH| needs to be installed:

   *  If K3s is not present, :program:`install-lockss` will display ``K3s is not present``, and *will* install K3s |K3S_PATCH|.

   *  If an older version of K3s is present, :program:`install-lockss` will display :samp:`Detected K3s version {<installed_version>} is older than expected version {<expected_version>}`, and you will receive the following prompt:

      :guilabel:`Upgrade K3s from <installed_version> to <expected_version>?`

      Enter :kbd:`Y` and :program:`install-lockss` *will* install K3s |K3S_PATCH|, or enter :kbd:`N` and :program:`install-lockss` *will not* install K3s |K3S_PATCH|, or hit :kbd:`Enter` to accept the default in square brackets [#fnyes]_.

   *  If the expected version of K3s is already present, :program:`install-lockss` will display :samp:`K3s version {<installed_version>} is already installed; skipping`, and *will not* install K3s |K3S_PATCH|.

   *  If a more recent version of K3s is present, :program:`install-lockss` will display :samp:`Detected K3s version {<installed_version>} is more recent than expected version {<expected_version>}`, and *will not* install K3s |K3S_PATCH|.

   *  If K3s is detected but the installed and expected version numbers cannot be compared automatically, :program:`install-lockss` will display :samp:`[Warning] Detected K3s version {<installed_version>}, expected version {<expected_version>}, comparison failure, skipping`, and :program:`install-lockss` *will not* install K3s.

2. If :program:`install-lockss` determined it *will not* install K3s |K3S_PATCH|, you will see the confirmation ``Not installing K3s``, and nothing will happen in this step.

   But if :program:`install-lockss` determined it *will* install K3s |K3S_PATCH|, you will see the confirmation :samp:`Installing K3s version {<expected_version>}`, and this step will proceed as follows:

   a. First, :program:`install-lockss` will ask you to specify the K3s state data directory (the directory K3s uses to store state data), with this prompt:

      :guilabel:`K3s state data directory`

      By default, this is :file:`/var/lib/rancher/k3s`. However, if :file:`/var` is space-limited, you should specify a different directory, that has ample space and is not backed by NFS or by XFS with legacy ``ftype=0``.

      Enter a suitable directory path for the K3s state data directory, or hit :kbd:`Enter` to accept the default in square brackets [#fnyes2]_ [#fnk3sdatadir]_.

   b. Then :program:`install-lockss` will attempt to determine the filesystem type of the specified K3s state data directory. In many situations, it will simply display the filesystem type in a message similar to this (for example, :samp:`{<fs_type>}` might be ``ext4``):

      :samp:`Filesystem type of {<k3s_dir>} ({<k3s_mountpoint>}) is {<fs_type>}; proceeding`

      .. error::

         Below are some error conditions you may encounter here and what to do about them.

         .. dropdown:: Filesystem type of K3s state data directory is NFS

            If the filesystem type backing the K3s state data directory is NFS, you will see the error message:

            :samp:`[ERROR] Filesystem type of {<k3s_dir>} ({<k3s_mountpoint>}) is NFS; see manual`

            and :program:`install-lockss` will fail. It is not possible to run K3s with a state data directory backed by NFS [#fnk3sdatadirnfs]_. Re-run :program:`install-lockss` and designate a different K3s state data directory that is not backed by NFS.

         .. dropdown:: Filesystem type of K3s state data directory is XFS with legacy ``ftype=0``

            If the filesystem type backing the K3s state data directory is XFS with legacy ``ftype=0``, you will see the error message:

            :samp:`[ERROR] Filesystem type of {<k3s_dir>} ({<k3s_mountpoint>}) is XFS with legacy ftype=0; see manual for workaround`

            and :program:`install-lockss` will fail. Contemporary XFS filesystems with modern ``ftype=1`` work well with K3s, but older XFS filesystems with legacy ``ftype=0`` are not compatible. Ideally, re-run :program:`install-lockss` and designate a different K3s state data directory that is not backed by XFS with legacy ``ftype=0``. Alternatively, you can read about a workaround in :doc:`/troubleshooting/xfs`.

      .. warning::

         Below are some warning messages you may see here and how to respond to them.

         .. dropdown:: Filesystem type of K3s state data directory unknown

            If the filesystem type backing the K3s state data directory cannot be inferred automatically, you will see the warning:

            :samp:`[Warning] Filesystem type of {<k3s_dir>} unknown (findmnt not present); proceeding`

            and :program:`install-lockss` will keep going. But K3s may malfunction if the actual filesystem type backing the selected K3s state data directory is one that does not work with K3s, such as NFS, or XFS with legacy ``ftype=0``; see the error conditions above.

         .. dropdown:: Filesystem type of K3s state data directory is XFS but ``ftype`` unknown

            If the ``ftype`` of the XFS filesystem backing the K3s state data directory cannot be inferred automatically, you will see the warning:

            :samp:`[Warning] Filesystem type of {k3s_dir} ({k3s_mountpoint}) is XFS but ftype unknown (xfs_info not present); proceeding`

            and :program:`install-lockss` will keep going. But K3s may malfunction if the actual filesystem type backing the selected K3s state data directory is XFS with legacy ``ftype=0``; see the corresponding error condition above.

   c. Then :program:`install-lockss` will download the K3s Installer from https://get.k3s.io/ and invoke it with suitable options. This may take several minutes, during which the output will be that of the K3s Installer.

      Depending on your operating system and other factors, the K3s Installer may install additional software packages or configure system components, using :program:`sudo` if necessary (which may prompt for the user's :program:`sudo` password).

      .. error::

         If the K3s Installer does not succeed, it will display its own error messages, then :program:`install-lockss` will fail. See :doc:`/troubleshooting/k3s-installer` for remediation details.

         .. dropdown:: Sample error messages from the K3s Installer

            Error messages that the K3s Installer may display include:

            .. code-block:: text

               [ERROR]  Failed to apply container_runtime_exec_t to /usr/local/bin/k3s, please install:
                   yum install -y container-selinux selinux-policy-base
                   yum install -y https://rpm.rancher.io/k3s/stable/common/centos/8/noarch/k3s-selinux-0.3-0.el8.noarch.rpm

                Error: Package: k3s-selinux-0.3-0.el7.noarch (rancher-k3s-common-stable)
                          Requires: container-selinux >= 2.107-3
                You could try using --skip-broken to work around the problem
                You could try running: rpm -Va --nofiles --nodigest

3. Finally, whether or not K3s was installed, :program:`install-lockss` will store Kubernetes configuration data as the ``lockss`` user in the file :file:`config/k8s.cfg` (relative to the :ref:`LOCKSS Installer Directory`).

   .. error::

      Below are some error conditions you may encounter here and what to do about them.

      .. dropdown:: Could not write or append to :file:`k8s.cfg`

         If the creation of the file fails, you will see one of these error messages:

         .. code-block:: text

            [ERROR] Could not write k8s.cfg

            [ERROR] Could not append to k8s.cfg

         and :program:`install-lockss` will fail. Check for file permission mismatches between the user running :program:`install-lockss` and the :file:`lockss-installer/config` directory, then try again.

--------------------
Testing the K3s Node
--------------------

During this phase, :program:`install-lockss` runs a series of tests to verify that the K3s node is operational. This phase begins with the heading:

.. code-block::

   Testing the K3s node...

No user interaction is expected. If all tests pass, you will see the message:

.. code-block:: text

   [success] Tested the K3s node

and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Completion of the LOCKSS Installation Process` (:numref:`Completion of the LOCKSS Installation Process`).

Otherwise, you will see an error message corresponding to the test that did not pass, and :program:`install-lockss` will fail.

.. error::

   Below are some error conditions you may encounter here and what to do about them.

   .. dropdown:: Problems with :file:`config/k8s.cfg`

      At the end of :numref:`Installing K3s` (:ref:`Installing K3s`), some Kubernetes-related data is stored in :file:`config/k8s.cfg` (relative to the :ref:`LOCKSS Installer Directory`). If the file cannot be found or read, or if it contains invalid or unexpected data, you may see one of these error messages:

      .. code-block:: text

         [ERROR] k8s.cfg not found

         [ERROR] Error reading K8S_FLAVOR

         [ERROR] K8S_FLAVOR is not set

         [ERROR] K8S_FLAVOR is not k3s

         [ERROR] Error reading KUBECTL_CMD

         [ERROR] KUBECTL_CMD is not set

         [ERROR] k3s command of KUBECTL_CMD is not on the PATH

      Check the contents of :file:`config/k8s.cfg` and contact us (:email:`lockss-support@lockss.org`) for troubleshooting if necessary.

   .. dropdown:: Problems with the K3s node

      If the K3s node is not behaving as expected, you may see one of these errors:

      .. code-block:: text

         [ERROR] Command failed (kubectl version)

         [ERROR] Timeout waiting for the K3s node to be ready

         [ERROR] Command failed (kubectl get node)

         [ERROR] Unexpected number of K3s nodes

      If the K3s node is newly installed, it may simply be that there has not yet been enough time for it to come up; you can re-run this phase with ``scripts/install-lockss --test-k3s`` (or ``scripts/install-lockss -K``) to retry. Contact us (:email:`lockss-support@lockss.org`) for troubleshooting if necessary.

   .. dropdown:: Problems with DNS

      If the K3s node's DNS environment is not working properly, you may see one of these errors:

      .. code-block:: text

         [ERROR] Timeout waiting for the CoreDNS pod to be running and ready

         [ERROR] Command failed (kubectl get pod)

         [ERROR] Unexpected number of CoreDNS pods

         [ERROR] Timeout waiting for the DNS service to be present

         [ERROR] Command failed (kubectl get service)

         [ERROR] Unexpected number of kube-dns services

         [ERROR] Unexpected kube-dns service type

         [ERROR] Timeout waiting for DNS resolution

         [ERROR] Unexpected Cluster-IP

      If the K3s node is newly installed, it may simply be that there has not yet been enough time for CoreDNS to come up; you can re-run this phase with ``scripts/install-lockss --test-k3s`` (or ``scripts/install-lockss -K``) to retry. You can also use the :program:`install-lockss` options :samp:`--retries={N}` (to increase the number of retries in DNS lookup tests to :samp:`{N}` from 5) or :samp:`--wait={S}` (to increase the delay between retries in DNS lookup tests to :samp:`{S}` seconds from 10). Contact us (:email:`lockss-support@lockss.org`) for troubleshooting if necessary.

---------------------------------------------
Completion of the LOCKSS Installation Process
---------------------------------------------

If all phases completed successfully, you will see the message:

.. code-block:: text

   [success] Successful completion of the LOCKSS installation process

and :program:`install-lockss` will terminate.

------------------------------
Checking the K3s Configuration
------------------------------

.. tip::

   This section is optional.

K3s comes with :program:`k3s check-config`, a configuration checker tool. The K3s configuration checker is capable of detecting complex underlying system situations that definitely require fixing (or applications running in the K3s cluster will not be able to function properly). On the other hand, the versions of the K3s configuration checker available at the time LOCKSS |LATEST_MINOR| was released contained bugs that reported spurious issues that are either inaccurate or moot. As a result, we have decided against running :program:`k3s check-config` as part of :program:`install-lockss` at this time, to avoid unnecessary interruptions in the installation of the LOCKSS system in many cases where there is no particular cause for concern.

That being said, we still recommend running :program:`k3s check-config` and interpreting the results using the :ref:`Troubleshooting the K3s Configuration Checker` section of the manual:

1. Run this command:

   .. code-block:: text

      k3s check-config

2. The following error messages in the output are indicative of system situations that require attention:

   .. code-block:: text

      /usr/sbin iptables v1.8.2 (nf_tables): should be older than v1.8.0, newer than v1.8.3, or in legacy mode (fail)

      RHEL7/CentOS7: User namespaces disabled; add 'user_namespace.enable=1' to boot command line (fail)

      apparmor: enabled, but apparmor_parser missing (fail)

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/k3s-checker` for details.

3. The following error messages in the output can be ignored:

   .. code-block:: text

      cgroup hierarchy: nonexistent?? (fail)

      links: aux/ip6tables should link to iptables-detect.sh (fail)
      links: aux/ip6tables-restore should link to iptables-detect.sh (fail)
      links: aux/ip6tables-save should link to iptables-detect.sh (fail)
      links: aux/iptables should link to iptables-detect.sh (fail)
      links: aux/iptables-restore should link to iptables-detect.sh (fail)
      links: aux/iptables-save should link to iptables-detect.sh (fail)

      swap: should be disabled

      CONFIG_INET_XFRM_MODE_TRANSPORT: missing

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/k3s-checker` for details.

4. For other error messages, check the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_, search for `K3s issues database on GitHub <https://github.com/k3s-io/k3s/issues>`_ or the Web for resources matching your error message or operating system, and/or contact us so we can help investigate and document for future reference.

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.

.. [#fnyes]

   If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

.. [#fnyes2]

   If :program:`install-lockss` was invoked with the ``--assume-yes`` option, the suggested value is automatically accepted for you.

.. [#fnforcedns]

   Or if your :program:`install-lockss` was invoked with the ``--force-dns-prompt`` option.

.. [#fnk3sdatadir]

   If :program:`install-lockss` was invoked with the :samp:`--k3s-data-dir={DIR}` option, :samp:`{DIR}` will automatically be used without the prompt.

.. [#fnk3sdatadirnfs]

   See https://github.com/containerd/containerd/discussions/6140.

.. [#fnk3sdatadirxfs]

   See https://docs.docker.com/storage/storagedriver/overlayfs-driver/#prerequisites.
