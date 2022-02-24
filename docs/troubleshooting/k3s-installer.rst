=================================
Troubleshooting the K3s Installer
=================================

This section provides troubleshooting information for the :ref:`Installing K3s` phase of :doc:`/installing/installer`.

The LOCKSS Installer's :program:`install-lockss` script installs K3s by executing Rancher's official K3s Installer [#fninstallk3s]_ from https://get.k3s.io/ after making sure various firewall and DNS issues are addressed [#fniptables]_ [#fnfirewalld]_ [#fnufw]_ [#fncoredns]_. However, the installer can still run into issues and fail. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up the specific error message.

--------------------------------------------------------------
Failed to apply container_runtime_exec_t to /usr/local/bin/k3s
--------------------------------------------------------------

.. COMMENT updated for alpha5

In some Fedora systems, the K3s installer may fail with an error message similar to the following:

.. code-block:: text

   [ERROR]  Failed to apply container_runtime_exec_t to /usr/local/bin/k3s, please install:
       yum install -y container-selinux selinux-policy-base
       yum install -y https://rpm.rancher.io/k3s/stable/common/centos/8/noarch/k3s-selinux-0.3-0.el8.noarch.rpm

The specific commands and version numbers may vary from the example above.

To resolve this problem:

1. Run the recommended commands as ``root`` [#fnroot]_.

2. Re-run :program:`install-lockss` [#fninstalllockss]_.

--------------------------------------
k3s-selinux requires container-selinux
--------------------------------------

.. COMMENT updated for alpha5

In some Oracle Linux 7 systems, you may see an error message similar to the following:

.. code-block:: text

   Error: Package: k3s-selinux-0.3-0.el7.noarch (rancher-k3s-common-stable)
              Requires: container-selinux >= 2.107-3
    You could try using --skip-broken to work around the problem
    You could try running: rpm -Va --nofiles --nodigest

The specific commands and version numbers may vary from the example above.

This can occur in environments where the Oracle Linux 7 Addons Yum repository is not enabled by default, so Rancher's official K3s installer is unable to install the package ``container-selinux`` automatically.

To resolve this problem:

1. Run the following command as ``root`` [#fnroot]_:

   .. code-block:: shell

      yum-config-manager --enable ol7_addons

2. Re-run :program:`install-lockss` [#fninstalllockss]_.

----

.. rubric:: Footnotes

.. [#fninstalllockss]

   See :doc:`/installing/installer`.

.. [#fninstallk3s]

   See :ref:`Installing K3s`.

.. [#fniptables]

   See :ref:`configuring-iptables`.

.. [#fnfirewalld]

   See :ref:`configuring-firewalld`.

.. [#fnufw]

   See :ref:`configuring-ufw`.

.. [#fncoredns]

   See :ref:`Configuring CoreDNS for K3s`.

.. [#fnroot]

   See :doc:`/sysadmin/root`.
