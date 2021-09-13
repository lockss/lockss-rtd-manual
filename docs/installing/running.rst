============================
Running the LOCKSS Installer
============================

The next task is to run the LOCKSS Installer's :program:`install-lockss` script.

FIXME overview

----------------------------------
Checking the System User and Group
----------------------------------

.. rubric:: Description

During this phase, :program:`install-lockss` will check that the ``lockss`` user and group exist on the host system.

.. rubric:: Label

This phase begins with the label :guilabel:`Checking the system user and group...`.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-check-system-user`` option, you will see the message:

   .. code-block:: text

      [success] Skipping (--skip-check-system-user)

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`configuring-firewalld`).

2. If the ``lockss`` user or group does not exist on the host system, you will see one of these error messages:

   .. code-block:: text

      [ERROR] The lockss user does not exist

      [ERROR] The lockss group does not exist

   and :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See the :doc:`user` section to create the ``lockss`` user and group.

3. Finally, you will see the message:

   .. code-block:: text

      [success] User and group present

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`configuring-firewalld`).

.. _configuring-firewalld:

----------------------------------------
Configuring :program:`firewalld` for K3s
----------------------------------------

.. rubric:: Description

During this phase, :program:`install-lockss` will configure :program:`firewalld` to work with K3s, if necessary.

.. rubric:: Label

This phase begins with the label :guilabel:`Configuring firewalld for K3s...`.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-firewalld`` option (implied by ``--skip-install-k3s``), or if :program:`firewalld` is not present or is not running, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-firewalld)

      [success] Skipping (firewall-cmd is not on the PATH)

      [success] Skipping (firewalld is not running)

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`configuring-ufw`).

2. If :program:`firewalld` is running, you will receive the following prompt:

   :guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

   Enter :kbd:`Y` to accept the proposed :program:`firewalld` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets). (If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.)

   .. warning::

      If you bypass the proposed :program:`firewalld` configuration, you will see the warning:

      .. code-block:: text

         [Warning] Leaving firewalld unchanged; see manual for details

      and :program:`install-lockss` will immediately proceed to the next phase (:ref:`configuring-ufw`), but K3s may malfunction without further intervention. See :doc:`/troubleshooting/firewalld` for details.

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

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`configuring-ufw`).

.. _configuring-ufw:

----------------------------------
Configuring :program:`ufw` for K3s
----------------------------------

.. rubric:: Description

During this phase, :program:`install-lockss` will configure :program:`ufw` to work with K3s, if necessary.

.. rubric:: Label

This phase begins with the label :guilabel:`Configuring firewalld for ufw...`.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-ufw`` option (implied by ``--skip-install-k3s``), or if :program:`ufw` is not present or is not active, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-ufw)

      [success] Skipping (ufw is not on the PATH)

      [success] Skipping (ufw is not active)

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`configuring-coredns`).

2. If :program:`ufw` is active, you will receive the following prompt:

   :guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

   Enter :kbd:`Y` to accept the proposed :program:`ufw` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets). (If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.)

   .. warning::

      If you bypass the proposed :program:`ufw` configuration, you will see the warning:

      .. code-block:: text

         [Warning] Leaving ufw unchanged; see manual for details

      and :program:`install-lockss` will immediately proceed to the next phase (:ref:`configuring-coredns`), but K3s may malfunction without further intervention. See :doc:`/troubleshooting/ufw` for details.

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

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`configuring-coredns`).

.. _configuring-coredns:

---------------------------
Configuring CoreDNS for K3s
---------------------------

.. rubric:: Description

During this phase, :program:`install-lockss` will configure CoreDNS to work with K3s, if necessary.

.. rubric:: Label

This phase begins with the label :guilabel:`Configuring CoreDNS for K3s...`.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-configure-coredns`` option (implied by ``--skip-install-k3s``), or if your system's DNS configuration will simply work with CoreDNS, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-dns)

      [success] Using system resolv.conf files

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`installing-k3s`).

2. If your system's DNS configuration will not work with CoreDNS, or if :program:`install-lockss` was invoked with the ``--force-dns-prompt`` option, you will receive the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses. A suggested value will be offered to you in square brackets, consisting of non-loopback addresses collected from your machine's DNS configuration; you can simply hit :kbd:`Enter` to accept the suggested value. (If :program:`install-lockss` was invoked with the ``--assume-yes`` option, the suggested value is automatically accepted witout the prompt.)

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

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`installing-k3s`).

.. _installing-k3s:

--------------
Installing K3s
--------------

.. rubric:: Description

During this phase, :program:`install-lockss` will install K3s.

.. rubric:: Label

This phase begins with the label :guilabel:`Installing K3s...`.

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-install-k3s`` option, or if K3s is already installed, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (K3s is already present)

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`k3s-check-config`).

2. Next, :program:`install-lockss` will warn you that the directory K3s uses to store state data (by default :file:`/var/lib/rancher/k3s`) should not be attached to a space-limited volume. You will see the following prompt:

   :guilabel:`K3s state data directory`

   Enter a directory path for the K3s state directory, or simply hit :kbd:`Enter` to accept the default in square brackets. (If :program:`install-lockss` was invoked with the :samp:`--k3s-data-dir={DIR}` option, :samp:`{DIR}` will automatically be used without the prompt. If :program:`install-lockss` was invoked with the ``--assume-yes`` option, the default is automatically used without the prompt.)

3. The K3s Installer will then be downloaded from https://get.k3s.io/ and invoked with suitable options. Depending on your operating system and other factors, the K3s Installer may install additional software packages or configure system components, using :program:`sudo` if necessary (which may prompt for the user's :program:`sudo` password).

   If the K3s Installer does not succeed, it will display its own error messages, then :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :ref:`Troubleshooting the K3s Installer` for remediation details. Error messages that the K3s Installer may display include:

      *  FIXME

4. Then :program:`install-lockss` will store Kubernetes configuration data as the ``lockss`` user in the file :file:`configs/k8s.cfg`, relative to the LOCKSS Installer home directory. If the creation of the file fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Could not write to configs/k8s.cfg

      [ERROR] Could not append to configs/k8s.cfg

      [ERROR] configs/k8s.cfg is not owned by lockss:lockss

   and :program:`lockss-installer` will fail.

   .. admonition:: Troubleshooting

      FIXME

5. Finally, you will see the message:

   .. code-block:: text

      [success] Configured CoreDNS for K3s

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`k3s-check-config`).

.. _k3s-check-config:

------------------------------
Checking the K3s Configuration
------------------------------

.. rubric:: Description

During this phase, :program:`install-lockss` will invoke :program:`k3s check-config`, a configuration checker provided by K3s.

.. rubric:: Label

This phase begins with the label :guilabel:`Checking the K3s configuration...`

.. rubric:: Steps

1. If :program:`install-lockss` was invoked with the ``--skip-k3s-check-config`` option (implied by ``--skip-install-k3s``), you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-check-k3s-config)

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`testing-k3s`).

2. Next, :program:`install-lockss` will invoke :program:`k3s check-config` via :program:`sudo` (which may prompt for the user's :program:`sudo` password).

   If the K3s configuration checker does not succeed, it will display its own error messages, then :program:`install-lockss` will fail.

   .. admonition:: Troubleshooting

      See :ref:`Troubleshooting the K3s Configuration Checker` for remediation details. Error messages that the K3s configuration checker may display include:

      *  FIXME

3. Finally, you will see the message:

   .. code-block:: text

      [success] Checked the K3s configuration

   and :program:`install-lockss` will successfully proceed to the next phase (:ref:`testing-k3s`).

.. _testing-k3s:

--------------------
Testing the K3s Node
--------------------

.. rubric:: Description

During this phase, :program:`install-lockss` runs a series of tests to verify that the K3s node is operational.

.. rubric:: Label

This phase begins with the label :guilabel:`Testing the K3s node...`

.. rubric:: Steps


