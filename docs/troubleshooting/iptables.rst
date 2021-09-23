===================================
Troubleshooting :program:`iptables`
===================================

K3s 1.21.5+k3s1 (the version used by LOCKSS 2.0-alpha5) does not always work with :program:`iptables` version 1.8.0-1.8.3 run via Alternatives not in ``legacy`` mode, for instance in some Debian or Ubuntu systems [#fnreference]_. If :program:`install-lockss` detects this situation, you will see a warning message and the following prompt [#fninstaller]_:

:guilabel:`Switch iptables to legacy mode via Alternatives?`

Enter :kbd:`Y` to accept the proposed :program:`iptables` configuration. **If you bypass the proposed configuration, K3s may malfunction.**

The remediation attempted by :program:`install-lockss` is equivalent to:

.. code-block:: shell

   # Required only if ufw is active
   ufw disable

   # Required
   update-alternatives --set iptables /usr/sbin/iptables-legacy

   # Required
   update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy

   # Optional
   update-alternatives --set arptables /usr/sbin/arptables-legacy

   # Optional
   update-alternatives --set ebtables /usr/sbin/ebtables-legacy

   # Required
   iptables --flush

   # Required only if ufw was active
   ufw enable

.. tip::

   If your system did not initially need an adjustment for :program:`iptables` at the time K3s was installed, but later does (for example because :program:`iptables` is upgraded from a pre-1.8.0 version to version 1.8.0 or later), run this command (which is relative to the :ref:`lockss-installer-directory`) as a privileged user who can become ``root`` via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/install-lockss --configure-iptables

   This will run only the :ref:`configuring-iptables` phase of :program:`install-lockss`.

----

.. rubric:: Footnotes

.. [#fnreference]

   References:

   *  https://rancher.com/docs/k3s/latest/en/known-issues/

   *  https://github.com/kubernetes/kubernetes/issues/71305

   *  https://github.com/k3s-io/k3s/issues/116

      *  https://github.com/k3s-io/k3s/issues/116#issuecomment-624770403

   *  https://github.com/k3s-io/k3s/issues/703

.. [#fninstaller]

   See :ref:`configuring-iptables`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
