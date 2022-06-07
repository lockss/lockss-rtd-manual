=============================================
Troubleshooting the K3s Configuration Checker
=============================================

After installing K3s [#fninstallk3s]_, you may optionally run the K3s configuration checker :program:`k3s check-config` [#fnk3scheckconfig]_ (see :ref:`Checking the K3s Configuration`). This configuration checker runs through a more extensive series of tests, covering "required", "generally necessary", and "optional" system aspects needed by K3s.

Some failures, especially in "optional" aspects, may not actually prevent the cluster from working normally, in the limited ways the LOCKSS system uses Kubernetes. Some of the error messages you might encounter are documented below, but you may need to refer to the official `K3s documentation <https://rancher.com/docs/k3s/latest/en/>`_ or use a search engine to look up a specific error message.

--------------------------------------------------------------------------
iptables should be older than v1.8.0, newer than v1.8.3, or in legacy mode
--------------------------------------------------------------------------

.. COMMENT updated for alpha5

In some instances, you may encounter an error message similar to the following:

.. code-block:: text

   /usr/sbin iptables v1.8.2 (nf_tables): should be older than v1.8.0, newer than v1.8.3, or in legacy mode (fail)

In previous versions of K3s, this error message was also sometimes phrased as ``should be older than v1.8.0 or in legacy mode``.

The :program:`install-lockss` script should detect this situation and offer to switch :program:`iptables` to legacy mode via Alternatives (see :doc:`iptables`). If the error above occurs:

*  Verify that the :ref:`configuring-iptables` phase of :program:`install-lockss` was not skipped.

*  Verify that, if applicable, the proposed :program:`iptables` configuration changes in the :ref:`configuring-iptables` phase of :program:`install-lockss` were not bypassed.

*  Using the :doc:`iptables` section as reference, verify that the remediation attempted by :program:`install-lockss` has taken effect.

*  Search the `K3s issues database <https://github.com/k3s-io/k3s/issues>`_ for issues related to :program:`k3s check-config`, :program:`iptables` and your operating system.

------------------------
User namespaces disabled
------------------------

In some RHEL 7 and CentOS 7 systems, you may receive the following error message:

.. code-block:: text

   RHEL7/CentOS7: User namespaces disabled; add 'user_namespace.enable=1' to boot command line (fail)

To resolve this issue, see :ref:`Enabling User Namespaces in RHEL 7 and CentOS 7`.

--------------------------------------------
apparmor enabled but apparmor_parser missing
--------------------------------------------

In some systems where Apparmor is enabled, you may receive the following error:

.. code-block:: text

   apparmor: enabled, but apparmor_parser missing (fail)

To resolve this issue, see :ref:`installing-apparmor_parser`.

----------------------------
cgroup hierarchy nonexistent
----------------------------

.. COMMENT updated for alpha5

In some Arch Linux, Debian and Fedora systems, you may see the following error message:

.. code-block:: text

   cgroup hierarchy: nonexistent?? (fail)

K3s supports ``cgroup2`` but :program:`k3s check-config` version 1.21.5+k3s1 (used in LOCKSS 2.0-alpha5) does not process this condition correctly. **This warning can be ignored.**

-----------------------------------------------------
links: aux/iptables should link to iptables-detect.sh
-----------------------------------------------------

.. COMMENT updated for alpha5

In some Fedora and OpenSUSE systems, you may encounter six related error messages like the following:

.. code-block:: text

   links: aux/ip6tables should link to iptables-detect.sh (fail)
   links: aux/ip6tables-restore should link to iptables-detect.sh (fail)
   links: aux/ip6tables-save should link to iptables-detect.sh (fail)
   links: aux/iptables should link to iptables-detect.sh (fail)
   links: aux/iptables-restore should link to iptables-detect.sh (fail)
   links: aux/iptables-save should link to iptables-detect.sh (fail)

This is due to a bug in :program:`k3s check-config` [#fniptablesdetectbug]_, triggered in environments where there is no :program:`iptables` system package installed. **This warning can be ignored.**

-----------------------
swap should be disabled
-----------------------

**This warning can be ignored:**

.. code-block:: text

   swap: should be disabled

---------------------------------------
CONFIG_INET_XFRM_MODE_TRANSPORT missing
---------------------------------------

**This warning can be ignored:**

.. code-block:: text

   CONFIG_INET_XFRM_MODE_TRANSPORT: missing

----

.. rubric:: Footnotes

.. [#fninstalllockss]

   See :doc:`/installing/installer`.

.. [#fninstallk3s]

   See :ref:`Installing K3s`.

.. [#fnk3scheckconfig]

   See :ref:`Checking the K3s Configuration`.

.. [#fnk3sbug]

   References:

   *  https://github.com/k3s-io/k3s/issues/2946

.. [#fnusernamespaces]

   References:

   *  https://fortuitousengineer.com/installing-kubernetes-k3s-on-centos-rhel-hosts/

.. [#fniptablesdetectbug]

   Reference:

   *  https://github.com/k3s-io/k3s/issues/4066

      *  https://github.com/k3s-io/k3s/issues/4066#issuecomment-925137706

.. [#fnroot]

   See :doc:`/sysadmin/root`.
