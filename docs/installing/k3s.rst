==============
Installing K3s
==============

`K3s <https://k3s.io/>`_ is a certified `Kubernetes <https://kubernetes.io/>`_ distribution by `Rancher <https://rancher.com/>`_.

*FIXME*

-----------------
Preliminary Steps
-----------------

Some operating systems require preliminary steps. If your operating system does not need special steps, you can proceed to the next section.

.. tabs::

   .. group-tab:: CentOS

      For CentOS, you need to issue the following command before installing K3s [#fn1]_ :

      .. code-block:: shell

         sudo systemctl disable firewalld --now

--------------
Installing K3s
--------------

.. code-block:: shell

   curl -sfL https://get.k3s.io | sh -s - --with-node-id --disable traefik,metrics-server

----

.. rubric:: Footnotes

.. [#fn1] Reference: https://rancher.com/docs/k3s/latest/en/advanced/#additional-preparation-for-red-hat-centos-enterprise-linux
