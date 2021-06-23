==============================
Troubleshooting :program:`ufw`
==============================

If your system is running the :program:`ufw` firewall, it is necessary to allow traffic from K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) via :program:`ufw` for K3s to work properly [#fn1]_. If :program:`configure-firewall` (a script called by :program:`install-k3s`) detects this situation, you will see a warning message and the following prompt [#fn2]_:

:guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

Enter :kbd:`Y` for "yes" and :kbd:`N` for "no", or simply hit :kbd:`Enter` to accept the proposed answer (displayed in square brackets).

.. caution::

   If you opt out of the proposed remediation, K3s may malfunction.

The remediation attempted by :program:`configure-firewall` is equivalent to [#fn3]_:

.. code-block:: shell

   ufw allow from 10.42.0.0/16 to any

   ufw allow from 10.43.0.0/16 to any

   ufw reload

By default, K3s' pod subnet is 10.42.0.0/16 and service subnet is 10.43.0.0/16, but if you customized your K3s installation to use other subnets, you should substitute them here.

.. tip::

   If your system did not initially use :program:`ufw` at the time K3s was installed, but later does (for example because :program:`ufw` becomes enabled), run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/configure-firewall

----

.. rubric:: Footnotes

.. [#fn1]

   References:

   *  https://github.com/k3s-io/k3s/issues/1280

      *  https://github.com/k3s-io/k3s/issues/1280#issuecomment-663269728

.. [#fn2]

   See :doc:`/installing/k3s`.

.. [#fn3]

   By default, K3s' pod subnet is 10.42.0.0/16 and service subnet is 10.43.0.0/16.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
