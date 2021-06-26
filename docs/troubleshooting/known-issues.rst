============
Known Issues
============

*This page was last updated: 2021-06-25.*

.. _known-issue-security:

*  **Security**

.. _known-issue-k8s-access:

   *  In the "alpha" phase of development of LOCKSS 2.0, there are no access controls on Kubernetes' API. It is not accessible from outside the machine, but any local user can access the API, so they can stop the LOCKSS containers, change their contents, read secrets, etc. We plan to enable access controls in the "beta" phase.

.. _known-issue-dns:

*  **DNS Resolution**

   K3s' default DNS cache timeout is 30 seconds, which results in enough repetitive upstream queries to trigger alarms at some institutions. One remediation is to change the CoreDNS configuration by editing its configmap.

   With K3s, changes made to CoreDNS's configmap with :program:`kubectl apply` do not persist, because the configmap is constantly reloaded from :file:`/var/lib/rancher/k3s/server/manifests/coredns.yaml`.  Additionally, K3s overwrites the file with the defaults at startup, so changes there are not really persistent either.

   The LOCKSS Installer offers the script :file:`scripts/coredns-cron-hack`, which sets the CoreDNS cache timeout to 30 minutes. It should be run once, as ``root``, after each time K3s starts. Absent a good way to do that, it is harmless to run it periodically from ``root``'s crontab. The recommended use is to copy it to a ``root``-owned file in :file:`/etc/cron.hourly`.
