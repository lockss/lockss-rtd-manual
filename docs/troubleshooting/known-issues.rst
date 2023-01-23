============
Known Issues
============

*This section was last updated: 2023-01-23.*

.. _known-issue-k3s-cert:

.. rubric:: Expired K3s Certificate

LOCKSS-provided scripts like ``scripts/stop-lockss`` or ``scripts/restart-lockss`` that interact with the K3s server may display error messages that include:

.. code-block:: text

   error: You must be logged in to the server (Unauthorized)

In parallel, the host system log might contain messages similar to:

.. code-block:: text

   client_builder_dynamic.go:197: get or create service account failed: Get "https://127.0.0.1:6444/api/v1/namespaces/kube-system/serviceaccounts/generic-garbage-collector": x509: certificate has expired or is not yet valid: current time 2023-01-22T03:32:05-08:00 is after 2023-01-21T02:13:28Z

This is caused by a bug in the version of K3s that currently ships with the LOCKSS system, whereby the auto-rotation of a certificate after the K3s server runs continuously for one year does not take place correctly. Future releases of the LOCKSS system will use a newer version of K3s without this bug. In the meantime, to work around this problem, simply restart the K3s service with :program:`systemctl` as ``root``:

.. code-block:: text

   systemctl restart k3s

Scripts that interact with the K3s server should then again work as expected.

.. _known-issue-security:

.. rubric:: Security

.. _known-issue-k8s-access:

*  In the "alpha" phase of development of LOCKSS 2.0, there are no access controls on Kubernetes' API. It is not accessible from outside the machine, but any local user can access the API, so they can stop the LOCKSS containers, change their contents, read secrets, etc. We plan to enable access controls in the "beta" phase.

.. _known-issue-lcap-ssl:

*  In the Classic LOCKSS system (1.x), the LCAP SSL key could only be read by ``root``, but now it can also be read by ``lockss``.

.. _known-issue-dns:

.. rubric:: DNS Resolution

K3s' default DNS cache timeout is 30 seconds, which results in enough repetitive upstream queries to trigger alarms at some institutions. One remediation is to change the CoreDNS configuration by editing its configmap.

With K3s, changes made to CoreDNS's configmap with :program:`kubectl apply` do not persist, because the configmap is constantly reloaded from :file:`/var/lib/rancher/k3s/server/manifests/coredns.yaml`.  Additionally, K3s overwrites the file with the defaults at startup, so changes there are not really persistent either.

The LOCKSS Installer offers the script :file:`scripts/coredns-cron-hack`, which sets the CoreDNS cache timeout to 30 minutes. It should be run once, as ``root``, after each time K3s starts. Absent a good way to do that, it is harmless to run it periodically from ``root``'s crontab. The recommended use is to copy it to a ``root``-owned file in :file:`/etc/cron.hourly`.

.. _known-issue-pid-files:

.. rubric:: Harmless PID File Errors

The ``stdout`` log files of the various LOCKSS service containers contain the following error messages at startup:

.. code-block:: text

   /usr/local/bin/docker-entrypoint: line 374: can't create /var/run/docker-entrypoint.pid: Permission denied

This is harmless and will be addressed in the a future release of the system.
