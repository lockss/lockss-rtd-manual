==============
Installing K3s
==============

`K3s <https://k3s.io/>`_ is a certified `Kubernetes <https://kubernetes.io/>`_ distribution by `Rancher <https://rancher.com/>`_.

*FIXME*

.. code-block:: shell

   curl -sfL https://get.k3s.io | sh -s - --with-node-id --disable traefik,metrics-server
