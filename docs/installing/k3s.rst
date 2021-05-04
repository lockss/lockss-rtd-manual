==============
Installing K3s
==============

`K3s <https://k3s.io/>`_ is a certified `Kubernetes <https://kubernetes.io/>`_ distribution by `Rancher <https://rancher.com/>`_.

*FIXME*

.. note::

   This section is run as the ``root`` user or as a user with :program:`sudo` privileges.

-----------------
Preliminary Steps
-----------------

Some operating systems require preliminary steps [#fn1]_ . If your operating system does not need special steps, you can proceed to the next section.

.. tabs::

   .. group-tab:: AlmaLinux

      .. include:: k3s-firewalld.rst

   .. group-tab:: CentOS

      .. include:: k3s-firewalld.rst

   .. group-tab:: Oracle Linux

      .. include:: k3s-firewalld.rst

   .. group-tab:: RHEL

      .. include:: k3s-firewalld.rst

   .. group-tab:: Rocky Linux

      .. include:: k3s-firewalld.rst

--------------
Installing K3s
--------------

Assuming you are in the :file:`lockss-installer` directory, run the following command  (as ``root`` or with :program:`sudo`):

.. code-block:: shell

   scripts/install-k3s

*FIXME possible interaction especially DNS*

----

.. rubric:: Footnotes

.. [#fn1] Reference: https://rancher.com/docs/k3s/latest/en/installation/installation-requirements/#operating-systems

.. [#fn2] Reference: https://rancher.com/docs/k3s/latest/en/advanced/#additional-preparation-for-red-hat-centos-enterprise-linux

.. [#fn3] Alternatively, you can log in as ``root``, in which case you can issue all commands without the leading :program:`sudo`.
