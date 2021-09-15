===================================
Troubleshooting :program:`iptables`
===================================

K3s, the Kubernetes environment recommended for the LOCKSS system, does not currently work with :program:`iptables` version 1.8.0 or later in ``nf_tables`` mode via Alternatives, for instance in some Debian or Ubuntu systems [#fn1]_. If :program:`configure-firewall` (a script called by :program:`install-k3s`) detects this situation, you will see a warning message and the following prompt [#fn2]_:

:guilabel:`Switch iptables to legacy mode via Alternatives?`

Enter :kbd:`Y` for "yes" and :kbd:`N` for "no", or simply hit :kbd:`Enter` to accept the proposed answer (displayed in square brackets).

.. caution::

   If you opt out of the proposed remediation, K3s may malfunction.

The remediation attempted by :program:`configure-firewall` is equivalent to:

.. code-block:: shell

   # Needed if ufw is installed and active
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

   # Needed if ufw is installed and was active
   ufw enable

.. tip::

   If your system did not initially need an adjustment for :program:`iptables` at the time K3s was installed, but later does (for example because :program:`iptables` is upgraded from a pre-1.8.0 version to version 1.8.0 or later), re-run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/configure-firewall

----

.. rubric:: Footnotes

.. [#fn1]

   References:

   *  https://rancher.com/docs/k3s/latest/en/known-issues/

   *  https://github.com/kubernetes/kubernetes/issues/71305

   *  https://github.com/k3s-io/k3s/issues/116

      *  https://github.com/k3s-io/k3s/issues/116#issuecomment-624770403

   *  https://github.com/k3s-io/k3s/issues/703

.. [#fn2]

   See :doc:`/installing/running`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
