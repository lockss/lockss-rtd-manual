====================================
Troubleshooting :program:`firewalld`
====================================

If your system is running the :program:`firewalld` firewall, it is necessary to add K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) to :program:`firewalld`'s ``trusted`` zone for K3s to work properly [#fn1]_.

The LOCKSS Installer's :program:`install-k3s` script calls another script, :program:`configure-firewall`, which detects this situation at the time K3s is being installed, and offers to make this change with the following prompt [#fn2]_:

:guilabel:`Add 10.42.0.0/16 and 10.43.0.0/16 to firewalld's trusted zone?`

If you opt out of this change, K3s may not function properly and you may have to resolve the situation with :program:`firewalld` (via :program:`firewall-cmd`) manually.

The remediation attempted by :program:`configure-firewall` is equivalent to:

.. code-block:: shell

   firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16

   firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16

   firewall-cmd --reload

By default, K3s' pod subnet is 10.42.0.0/16 and service subnet is 10.43.0.0/16, but if you customized your K3s installation to use other subnets, you should substitute them here.

.. tip::

   If your system did not initially use :program:`firewalld` at the time K3s was installed, but later does (for example because :program:`firewalld` becomes enabled), run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/configure-firewall

----

.. rubric:: Footnotes

.. [#fn1]

   For operating systems in the RHEL family (CentOS, Rocky Linux, AlmaLinux...), the action recommended by the K3s manual is to disable :program:`firewalld` entirely (see https://rancher.com/docs/k3s/latest/en/advanced/#additional-preparation-for-red-hat-centos-enterprise-linux), but :program:`install-k3s` takes a lighter approach commonly used in the K3s community.

   References:

   * https://github.com/k3s-io/k3s/issues/1556

      * https://github.com/k3s-io/k3s/issues/1556#issuecomment-604112415

.. [#fn2]

   See :doc:`/installing/k3s`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
