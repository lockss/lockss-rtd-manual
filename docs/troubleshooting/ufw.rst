==============================
Troubleshooting :program:`ufw`
==============================

If your system is running the :program:`ufw` firewall, it is necessary to allow traffic from K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) via :program:`ufw` for K3s to work properly [#fn1]_.

The LOCKSS Installer's :program:`install-k3s` script calls another script, :program:`configure-firewall`, which detects this situation at the time K3s is being installed, and offers to make this change with the following prompt [#fn2]_:

:guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

If you opt out of this change, K3s may not function properly and you may have to resolve the situation with :program:`ufw` manually.

The remediation attempted by :program:`configure-firewall` is equivalent to:

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

   * https://github.com/k3s-io/k3s/issues/1280

      * https://github.com/k3s-io/k3s/issues/1280#issuecomment-663269728

.. [#fn2]

   See :doc:`/installing/k3s`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
