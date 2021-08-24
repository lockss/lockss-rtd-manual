============================
Running the LOCKSS Installer
============================

The next task is to run the LOCKSS Installer's :program:`install-lockss` script.

----------------------------------
Checking the System User and Group
----------------------------------

During this step, :program:`install-lockss` will check that the ``lockss`` user and group exist on the host system.

1. If :program:`install-lockss` was invoked with the ``--skip-check-system-user`` option, you will see the message:

   .. code-block:: text

      [success] Skipping (--skip-check-system-user)

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`configuring-firewalld`).

2. If the ``lockss`` user or group does not exist on the host system, you will see one of the following error messages:

   .. code-block:: text

      [ERROR] The lockss user does not exist

      [ERROR] The lockss group does not exist

   and :program:`install-lockss` will *fail*.

   .. admonition:: Troubleshooting

      See the :doc:`user` section to create the ``lockss`` user and group.

3. Otherwise, you will see the message:

   .. code-block:: text

      [success] User and group present

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`configuring-firewalld`).

.. _configuring-firewalld:

----------------------------------------
Configuring :program:`firewalld` for K3s
----------------------------------------

During this step, :program:`install-lockss` will configure :program:`firewalld` to work with K3s, if necessary.

1. If :program:`install-lockss` was invoked with the ``--skip-configure-firewalld`` option (implied by ``--skip-install-k3s``), or if :program:`firewalld` is not present or is not running, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-firewalld)

      [success] firewall-cmd is not on the PATH

      [success] firewalld is not running

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`configuring-ufw`).

2. If :program:`firewalld` is running, you will receive the following prompt:

   :guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

   Enter :kbd:`Y` to accept the proposed :program:`firewalld` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets). If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

   .. warning::

      If you bypass the proposed :program:`firewalld` configuration, you will see the warning:

   .. code-block:: text

      [Warning] Leaving firewalld unchanged; see manual for details

   and :program:`install-lockss` will immediately proceed to the next step (:ref:`configuring-ufw`), but K3s may malfunction without further intervention. See :doc:`/troubleshooting/firewalld` for details.

3. If the :program:`firewalld` configuration attempt fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Could not add 10.42.0.0/16 to firewalld's trusted zone

      [ERROR] Could not add 10.43.0.0/16 to firewalld's trusted zone

      [ERROR] Could not reload firewalld

   and :program:`install-lockss` will *fail*.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/firewalld` for remediation details.

4. Otherwise, you will see the message:

   .. code-block:: text

      [success] Configured firewalld for K3s

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`configuring-ufw`).

.. _configuring-ufw:

----------------------------------
Configuring :program:`ufw` for K3s
----------------------------------

During this step, :program:`install-lockss` will configure :program:`ufw` to work with K3s, if necessary.

1. If :program:`install-lockss` was invoked with the ``--skip-configure-ufw`` option (implied by ``--skip-install-k3s``), or if :program:`ufw` is not present or is not active, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-ufw)

      [success] ufw is not on the PATH

      [success] ufw is not active

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`configuring-dns`).

2. If :program:`ufw` is active, you will receive the following prompt:

   :guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

   Enter :kbd:`Y` to accept the proposed :program:`ufw` configuration or :kbd:`N` to bypass (or hit :kbd:`Enter` to accept the default in square brackets). If :program:`install-lockss` was invoked with the ``--assume-yes`` option, :kbd:`Y` is automatically entered for you.

   .. warning::

      If you bypass the proposed :program:`ufw` configuration, you will see the warning:

      .. code-block:: text

         [Warning] Leaving ufw unchanged; see manual for details

      and :program:`install-lockss` will immediately proceed to the next step (:ref:`configuring-dns`), but K3s may malfunction without further intervention. See :doc:`/troubleshooting/ufw` for details.

3. If the :program:`firewalld` configuration attempt fails, you will see one of these error messages:

   .. code-block:: text

      [ERROR] Could not allow traffic from 10.42.0.0/16 via ufw

      [ERROR] Could not allow traffic from 10.43.0.0/16 via ufw

      [ERROR] Could not reload ufw

   and :program:`install-lockss` will *fail*.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/ufw` for remediation details.

4. Otherwise, you will see the message:

   .. code-block:: text

      [success] Configured ufw for K3s

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`configuring-dns`).

.. _configuring-dns:

---------------------------
Configuring CoreDNS for K3s
---------------------------

During this step, :program:`install-lockss` will configure CoreDNS to work with K3s, if necessary.

1. If :program:`install-lockss` was invoked with the ``--skip-configure-coredns`` option (implied by ``--skip-install-k3s``), or if your system's DNS configuration will simply work with CoreDNS, you will see one of these messages:

   .. code-block:: text

      [success] Skipping (--skip-install-k3s)

      [success] Skipping (--skip-configure-dns)

      [success] Using system resolv.conf files

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`FIXME`).

2. If your system's DNS configuration will not work with CoreDNS, you will receive the following prompt:

   :guilabel:`IP address(es) of DNS resolvers, separated by ';'`

   Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses. A suggested value will be offered to you in square brackets, consisting of non-loopback addresses collected from your machine's DNS configuration; you can simply hit :kbd:`Enter` to accept the suggested value. If :program:`install-lockss` was invoked with the ``--assume-yes`` option, the suggested values is automatically accepted.

3. If the creation of the CoreDNS configuration file fails, you will see error messages similar to these:

   .. code-block:: text

      [ERROR] Could not create /etc/lockss

      [ERROR] Error rendering config/templates/k3s/resolv.conf.mustache to config/resolv.conf

      [ERROR] Could not copy config/resolv.conf to /etc/lockss/resolv.conf

   and :program:`install-lockss` will *fail*.

   .. admonition:: Troubleshooting

      See :doc:`/troubleshooting/coredns` for remediation details.

4. Otherwise, you will see the message:

   .. code-block:: text

      [success] Configured CoreDNS for K3s

   and :program:`install-lockss` will successfully proceed to the next step (:ref:`FIXME`).
