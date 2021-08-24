====================================
Troubleshooting :program:`firewalld`
====================================

If your system is running the :program:`firewalld` firewall, it is necessary to add K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) to :program:`firewalld`'s ``trusted`` zone for K3s to work properly [#fnrhel]_. If :program:`install-lockss` detects this situation, you will see a warning message and the following prompt [#fnrunning]_:

:guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

Enter :kbd:`Y` to accept the proposed :program:`firewalld` configuration.

.. caution::

   If you bypass the proposed configuration, K3s may malfunction without further intervention.

The :program:`firewalld` configuration attempted by :program:`install-lockss` is equivalent to [#fnfirewalld]_:

.. code-block:: shell

   firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16

   firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16

   firewall-cmd --reload

.. tip::

   If your system did not initially use :program:`firewalld` at the time K3s was installed, but later does (for example because :program:`firewalld` becomes enabled), run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/install-lockss --configure-firewalld

   This will run only the :ref:`configuring-firewalld` portion of the :doc:`/installing/running` section.

----

.. rubric:: Footnotes

.. [#fnrhel]

   For operating systems in the RHEL family (CentOS, Rocky Linux, AlmaLinux...), the action recommended by the K3s manual is to disable :program:`firewalld` entirely (see https://rancher.com/docs/k3s/latest/en/advanced/#additional-preparation-for-red-hat-centos-enterprise-linux), but :program:`install-lockss` takes a lighter approach commonly used in the K3s community.

   References:

   *  https://github.com/k3s-io/k3s/issues/1556

      *  https://github.com/k3s-io/k3s/issues/1556#issuecomment-604112415

.. [#fnrunning]

   See :doc:`/installing/running`.

.. [#fnfirewalld]

   By default, K3s' pod subnet is 10.42.0.0/16 and service subnet is 10.43.0.0/16.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
