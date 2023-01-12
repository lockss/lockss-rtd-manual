============================
Running the LOCKSS Installer
============================

.. note::

   Commands in this section must be run **as a privileged user** who can become ``root`` and ``lockss`` via :program:`sudo` [#fnprivileged]_.

The next task is to run the LOCKSS Installer.

--------------------------------
Overview of the LOCKSS Installer
--------------------------------

When you invoke the LOCKSS Installer, the installation process goes through various phases:

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

To start the installation process, run this command (relative to the :ref:`lockss-installer-directory`) as a privileged user who can become ``root`` and ``lockss`` via :program:`sudo` [#fnprivileged]_:

.. code-block:: shell

   scripts/install-lockss

The installer will run through its phases, each of which is described in its own section below. The first phase is :ref:`Checking K3s Prerequisites` (:numref:`Checking K3s Prerequisites`).

--------------------------
Checking K3s Prerequisites
--------------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Checking K3s prerequisites...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will check that certain prerequisites to installing K3s are met.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-check-prerequisites`` option (implied by ``--skip-install-k3s``), you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-check-prerequisites)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Checking the System User and Group` (:numref:`Checking the System User and Group`).

2. Next, :program:`install-lockss` will check that user namespaces are enabled. In some RHEL 7 and CentOS 7 systems, user namespaces are not enabled by default; if this is the case, you will see the error message:

   .. code-block:: text

      [ERROR] User namespaces must be enabled in RHEL/CentOS 7; see manual

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :ref:`Enabling User Namespaces in RHEL 7 and CentOS 7` for troubleshooting, then go back to :ref:`Invoking the LOCKSS Installer` to try again.

3. Then :program:`install-lockss` will check that :program:`apparmor_parser` is installed if Apparmor is enabled. If Apparmor is enabled but :program:`apparmor_parser` is not installed, you will see the error message:

   .. code-block:: text

      [ERROR] apparmor enabled but apparmor_parser missing; see manual

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :ref:`installing-apparmor_parser` for troubleshooting, then go back to :ref:`Invoking the LOCKSS Installer` to try again.

4. Finally, you will see the message:

   .. code-block:: text

      [success] K3s prerequisites checked

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Checking the System User and Group` (:numref:`Checking the System User and Group`).

----------------------------------
Checking the System User and Group
----------------------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Checking the system user and group...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will check that the ``lockss`` user and group exist on the host system.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-check-system-user`` option, you will see the message:

   .. code-block:: text

      [success] Skipping (--skip-check-system-user)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-iptables` (:numref:`configuring-iptables`).

2. If the ``lockss`` user or group does not exist on the host system, you will see one of these error messages:

   .. code-block:: text

      [ERROR] The lockss user does not exist

      [ERROR] The lockss group does not exist

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See the :doc:`user` section to create the ``lockss`` user and group, then go back to :ref:`Invoking the LOCKSS Installer` to try again.

3. Finally, you will see the message:

   .. code-block:: text

      [success] System user and group present

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-iptables` (:numref:`configuring-iptables`).

.. _configuring-iptables:

---------------------------------------
Configuring :program:`iptables` for K3s
---------------------------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Configuring iptables for K3s...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will configure :program:`iptables` to work with K3s, if applicable.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-iptables`` option (implied by ``--skip-install-k3s``), or if no changes to the configuration of :program:`iptables` are necessary, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-iptables)

      [success] Skipping (iptables is not on the PATH nor run via Alternatives)

      [success] Skipping (iptables version is older than 1.8.0)

      [success] Skipping (iptables version is newer than 1.8.3)

      [success] Skipping (iptables is in legacy mode)

      [success] Skipping (iptables is not run via Alternatives)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-firewalld` (:numref:`configuring-firewalld`).

2. Otherwise, you will receive the following prompt:

   :guilabel:`Switch iptables to legacy mode via Alternatives?`

   Enter :kbd:`Y` to accept the proposed :program:`iptables` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets).

   *  If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

   *  You may be prompted for your :program:`sudo` password.

   .. warning::

      If you bypass the proposed :program:`iptables` configuration, you will see the warning:

      .. code-block:: text

         [Warning] Leaving iptables unchanged; see manual for details

      and :program:`install-lockss` will immediately proceed to the next phase, :ref:`configuring-firewalld` (:numref:`configuring-firewalld`). But K3s may malfunction without further intervention; see :doc:`/troubleshooting/iptables` for details.

3. If the :program:`iptables` configuration attempt fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Error deactivating ufw

      [ERROR] Error applying update-alternatives to iptables

      [ERROR] Error applying update-alternatives to ip6tables

      [ERROR] Error flushing iptables

      [ERROR] Error reactivating ufw

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/iptables` for remediation details.

4. Finally, you will see the message:

   .. code-block:: text

      [success] Configured iptables for K3s

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-firewalld` (:numref:`configuring-firewalld`).

.. _configuring-firewalld:

----------------------------------------
Configuring :program:`firewalld` for K3s
----------------------------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Configuring firewalld for K3s...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will configure :program:`firewalld` to work with K3s, if applicable.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-firewalld`` option (implied by ``--skip-install-k3s``), or if :program:`firewalld` is not present or is not running, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-firewalld)

      [success] Skipping (firewall-cmd is not on the PATH)

      [success] Skipping (firewalld is not running)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`configuring-ufw` (:numref:`configuring-ufw`).

2. If :program:`firewalld` is running, you will receive the following prompt:

   :guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

   Enter :kbd:`Y` to accept the proposed :program:`firewalld` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets).

   *  If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

   *  You may be prompted for your :program:`sudo` password.

   .. warning::

      If you bypass the proposed :program:`firewalld` configuration, you will see the warning:

      .. code-block:: text

         [Warning] Leaving firewalld unchanged; see manual for details

      and :program:`install-lockss` will immediately proceed to the next phase, :ref:`configuring-ufw` (:numref:`configuring-ufw`). But K3s may malfunction without further intervention; see :doc:`/troubleshooting/firewalld` for details.

3. If the :program:`firewalld` configuration attempt fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Could not add 10.42.0.0/16 to firewalld's trusted zone

      [ERROR] Could not add 10.43.0.0/16 to firewalld's trusted zone

      [ERROR] Could not reload firewalld

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/firewalld` for remediation details.

4. Finally, you will see the message:

   .. code-block:: text

      [success] Configured firewalld for K3s

   and :program:`install-lockss` will successfully proceed to the next phase :ref:`configuring-ufw` (:numref:`configuring-ufw`).

.. _configuring-ufw:

----------------------------------
Configuring :program:`ufw` for K3s
----------------------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Configuring firewalld for ufw...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will configure :program:`ufw` to work with K3s, if necessary.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-ufw`` option (implied by ``--skip-install-k3s``), or if :program:`ufw` is not present or is not active, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-ufw)

      [success] Skipping (ufw is not on the PATH)

      [success] Skipping (ufw is not active)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`).

2. If :program:`ufw` is active, you will receive the following prompt:

   :guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

   Enter :kbd:`Y` to accept the proposed :program:`ufw` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets).

   *  If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

   *  You may be prompted for your :program:`sudo` password.

   .. warning::

      If you bypass the proposed :program:`ufw` configuration, you will see the warning:

      .. code-block:: text

         [Warning] Leaving ufw unchanged; see manual for details

      and :program:`install-lockss` will immediately proceed to the next phase, :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`). But K3s may malfunction without further intervention. See :doc:`/troubleshooting/ufw` for details.

3. If the :program:`ufw` configuration attempt fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Could not allow traffic from 10.42.0.0/16 via ufw

      [ERROR] Could not allow traffic from 10.43.0.0/16 via ufw

      [ERROR] Could not reload ufw

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/ufw` for remediation details.

4. Finally, you will see the message:

   .. code-block:: text

      [success] Configured ufw for K3s

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Configuring CoreDNS for K3s` (:numref:`Configuring CoreDNS for K3s`).

---------------------------
Configuring CoreDNS for K3s
---------------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Configuring CoreDNS for K3s...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will configure CoreDNS to work with K3s, if necessary.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-coredns`` option (implied by ``--skip-install-k3s``), or if your system's DNS configuration will simply work with CoreDNS, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-dns)

      [success] Using system resolv.conf files

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Installing K3s` (:numref:`Installing K3s`).

2. If your system's DNS configuration will not work with CoreDNS, or if :program:`install-lockss` was invoked with the ``--force-dns-prompt`` option, you will receive a message including ``CoreDNS does not allow a loopback address to be given to Kubernetes pods as an upstream DNS server``, and the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses. A suggested value will be offered to you in square brackets, consisting of non-loopback IP addresses collected from your machine's DNS configuration; you can simply hit :kbd:`Enter` to accept the suggested value.

   *  If :program:`install-lockss` was invoked with the ``--assume-yes`` option, the suggested value is automatically accepted witout the prompt.

3. If the creation of the CoreDNS configuration file fails, you will see error messages similar to these:

   .. code-block:: text

      [ERROR] Could not create /etc/lockss

      [ERROR] Error rendering config/templates/k3s/resolv.conf.mustache to config/resolv.conf

      [ERROR] Could not copy config/resolv.conf to /etc/lockss/resolv.conf

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/coredns` for remediation details.

4. Finally, you will see the message:

   .. code-block:: text

      [success] Configured CoreDNS for K3s

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Installing K3s` (:numref:`Installing K3s`).

--------------
Installing K3s
--------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Installing K3s...`.

.. rubric:: Description

During this phase, :program:`install-lockss` will install K3s.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-install-k3s`` option, you will see the message:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Testing the K3s Node` (:numref:`Testing the K3s Node`).

2. Next, :program:`install-lockss` will determine if K3s needs to be installed or upgraded. There are five cases:

   *  Case 1: If K3s is not present, :program:`install-lockss` will display ``K3s is not present``, and will install K3s.

   *  Case 2: If the expected version of K3s is already present, :program:`install-lockss` will display :samp:`K3s version {installed_version} is already installed; skipping`, and will *not* install K3s.

   *  Case 3: If a more recent version of K3s is present, :program:`install-lockss` will display :samp:`Detected K3s version {installed_version} is more recent than expected version {expected_version}`, and will *not* install K3s.

   *  Case 4: If an older version of K3s is present, :program:`install-lockss` will display :samp:`Detected K3s version {installed_version} is older than expected version {expected_version}` and you will receive the following prompt:

      :guilabel:`Upgrade K3s from {installed_version} to {expected_version}?`

      Enter :kbd:`Y` and :program:`install-lockss` will install the newer K3s version, or :kbd:`N` and :program:`install-lockss` will *not* install the newer K3s version (or hit :kbd:`Enter` to accept the default in square brackets).

      *  If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

   *  Case 5: If K3s is detected but the installed and expected version numbers cannot be compared automatically, you will see the following warning:

      :samp:`[Warning] Detected K3s version {installed_version}, expected version {expected_version}, comparison failure, skipping`

      and :program:`install-lockss` will *not* install K3s.

   If :program:`install-lockss` determines that it will *not* install K3s, it will confirm ``Not installing K3s``, then will :ref:`skip the next 3 steps <write-k8s-config>`.

   Otherwise, :program:`install-lockss` will confirm :samp:`Installing K3s version {expected_version}` and will simply proceed to the next step.

3. First, :program:`install-lockss` will warn you that if the directory K3s uses to store state data (by default :file:`/var/lib/rancher/k3s`) is space-limited, you should specify a different directory. You will see the following prompt:

   :guilabel:`K3s state data directory`

   Enter a suitable directory path for the K3s state data directory, or simply hit :kbd:`Enter` to accept the default in square brackets.

   *  If :program:`install-lockss` was invoked with the :samp:`--k3s-data-dir={DIR}` option, :samp:`{DIR}` will automatically be used without the prompt.

   *  If :program:`install-lockss` was invoked with the ``--assume-yes`` option, the default is automatically used without the prompt.

4. Next, :program:`install-lockss` will detect the filesystem type backing the K3s state data directory, because some filesystem types (like NFS, or XFS with legacy ``ftype=0``) are not suitable or require special handling:

   a. If the filesystem type backing the K3s state data directory cannot be inferred automatically, you will see the warning:

      :samp:`[Warning] Filesystem type of {k3s_dir} unknown (findmnt not present); proceeding`

      and :program:`install-lockss` will :ref:`proceed to the next step <write-k8s-config>`.

   b. If the filesystem type backing the K3s state data directory is NFS, you will see the error message:

      :samp:`[ERROR] Filesystem type of {k3s_dir} ({k3s_mountpoint}) is NFS; see manual`

      and :program:`install-lockss` will fail.

   c. If the filesystem type backing the K3s state data directory is XFS, :program:`install-lockss` will determine its ``ftype`` (an internal characteristic):

      (i) If the XFS filesystem backing the K3s state data directory has legacy ``ftype=0``, you will see the error message:

         :samp:`[ERROR] Filesystem type of {k3s_dir} ({k3s_mountpoint}) is XFS with legacy ftype=0; see manual for workaround`

         and :program:`install-lockss` will fail.

      (ii) If the XFS filesystem backing the K3s state data directory does not have legacy ``ftype=0``, you will see one of these messages:

         :samp:`Filesystem type of {k3s_dir} ({k3s_mountpoint}) is XFS with ftype=1; proceeding`

         :samp:`Filesystem type of {k3s_dir} ({k3s_mountpoint}) is XFS but not with legacy ftype=0; proceeding`

         and :program:`install-lockss` will :ref:`proceed to the next step <write-k8s-config>`.

      (iii) If the ``ftype`` of the XFS filesystem backing the K3s state data directory cannot be inferred automatically, you will see the warning:

            :samp:`[Warning] Filesystem type of {k3s_dir} ({k3s_mountpoint}) is XFS but ftype unknown (xfs_info not present); proceeding`

         and :program:`install-lockss` will :ref:`proceed to the next step <write-k8s-config>`.

      (iv) Otherwise, :program:`install-lockss` will display the filesystem type backing the K3s state data directory in a message similar to this:

         :samp:`Filesystem type of {k3s_dir} ({k3s_mountpoint}) is {fs_type}; proceeding`

         (for some filesystem type :samp:`{fs_type}`, for example ``ext4``), and will :ref:`proceed to the next step <write-k8s-config>`.

5. Finally, the K3s Installer will be downloaded from https://get.k3s.io/ and invoked with suitable options.

   Depending on your operating system and other factors, the K3s Installer may install additional software packages or configure system components, using :program:`sudo` if necessary (which may prompt for the user's :program:`sudo` password).

   If the K3s Installer does not succeed, it will display its own error messages, then :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      Error messages that the K3s Installer may display include:

      .. code-block:: text

         [ERROR]  Failed to apply container_runtime_exec_t to /usr/local/bin/k3s, please install:
             yum install -y container-selinux selinux-policy-base
             yum install -y https://rpm.rancher.io/k3s/stable/common/centos/8/noarch/k3s-selinux-0.3-0.el8.noarch.rpm

         Error: Package: k3s-selinux-0.3-0.el7.noarch (rancher-k3s-common-stable)
                    Requires: container-selinux >= 2.107-3
          You could try using --skip-broken to work around the problem
          You could try running: rpm -Va --nofiles --nodigest

      See :doc:`/troubleshooting/k3s-installer` for remediation details.

.. _write-k8s-config:

6. Whether or not K3s was installed, :program:`install-lockss` will store Kubernetes configuration data as the ``lockss`` user in the file :file:`config/k8s.cfg`, relative to the LOCKSS Installer home directory. If the creation of the file fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Could not write k8s.cfg

      [ERROR] Could not append to k8s.cfg

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      Check file permission mismatches between the user running :program:`install-lockss` and the :file:`lockss-installer/config` directory, then try again.

7. Finally, you will see the message:

   .. code-block:: text

      [success] Installed K3s

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`Testing the K3s Node`).

--------------------
Testing the K3s Node
--------------------

.. rubric:: Heading

This phase begins with the heading :guilabel:`Testing the K3s node...`.

.. rubric:: Description

During this phase, :program:`install-lockss` runs a series of tests to verify that the K3s node is operational.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-test-k3s`` option (implied by ``--skip-install-k3s``), you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-test-k3s)

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Completion of the LOCKSS Installation Process` (:numref:`Completion of the LOCKSS Installation Process`).

2. Next, :program:`install-lockss` will run a series of tests. If a test fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] k8s.cfg not found

      [ERROR] Error reading K8S_FLAVOR

      [ERROR] K8S_FLAVOR is not set

      [ERROR] K8S_FLAVOR is not k3s

      [ERROR] Error reading KUBECTL_CMD

      [ERROR] KUBECTL_CMD is not set

      [ERROR] k3s command of KUBECTL_CMD is not on the PATH

      [ERROR] Command failed (kubectl version)

      [ERROR] Timeout waiting for the K3s node to be ready

      [ERROR] Command failed (kubectl get node)

      [ERROR] Unexpected number of K3s nodes

      [ERROR] Timeout waiting for the CoreDNS pod to be running and ready

      [ERROR] Command failed (kubectl get pod)

      [ERROR] Unexpected number of CoreDNS pods

      [ERROR] Timeout waiting for the DNS service to be present

      [ERROR] Command failed (kubectl get service)

      [ERROR] Unexpected number of kube-dns services

      [ERROR] Unexpected kube-dns service type

      [ERROR] Timeout waiting for DNS resolution

      [ERROR] Unexpected Cluster-IP

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      The reasons for some of these tests failing vary. Some wait for K3s to start up and retry a number of times but eventually give up, even though K3s will eventually come up fully. You can invoke just this portion of :program:`lockss-install` by invoking:

      .. code-block:: shell

         install-lockss --test-k3s

      or equivalently:

      .. code-block:: shell

         install-lockss -T

      You can also alter the number of retries and the number of seconds between retries with :samp:`--retries={N}` and :samp:`--wait={S}` respectively.

      Other problems may require reaching out to the LOCKSS support team at :email:`lockss-support@lockss.org` for assistance.

3. Finally, you will see the message:

   .. code-block:: text

      [success] Tested the K3s node

   and :program:`install-lockss` will successfully proceed to the next phase, :ref:`Completion of the LOCKSS Installation Process` (:numref:`Completion of the LOCKSS Installation Process`).

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

K3s comes with :program:`k3s check-config`, a configuration checker tool. The K3s configuration checker is capable of detecting complex underlying system situations that definitely require fixing (or applications running in the K3s cluster will not be able to function properly). On the other hand, the versions of the K3s configuration checker available at the time LOCKSS 2.0-alpha4 and LOCKSS 2.0-alpha5 were released contained bugs that reported spurious issues that are either inaccurate or moot. As a result, we have decided against running :program:`k3s check-config` as part of :program:`install-lockss` at this time, to avoid unnecessary interruptions in the installation of the LOCKSS system in many cases where there is no particular cause for concern.

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

.. [#fnprivileged]

   See :doc:`/sysadmin/privileged`.

.. [#fnk3sdatadirnfs]

   See https://github.com/containerd/containerd/discussions/6140.

.. [#fnk3sdatadirxfs]

   See https://docs.docker.com/storage/storagedriver/overlayfs-driver/#prerequisites.
