==============================
Troubleshooting :program:`ufw`
==============================

If your system is running the :program:`ufw` firewall, it is necessary to allow traffic from K3s' pod subnet (by default 10.42.0.0/16) and service subnet (by default 10.43.0.0/16) via :program:`ufw` for K3s to work properly [#fnreference]_. If :program:`install-lockss` detects this situation, you will see a warning message and the following prompt [#fnrunning]_:

:guilabel:`Allow traffic from 10.42.0.0/16 and 10.43.0.0/16 via ufw?`

Enter :kbd:`Y` to accept the proposed :program:`ufw` configuration.

.. caution::

   If you bypass the proposed configuration, K3s may malfunction without further intervention.

The :program:`firewalld` configuration attempted by :program:`install-lockss` is equivalent to [#fnufw]_:

.. code-block:: shell

   ufw allow from 10.42.0.0/16 to any

   ufw allow from 10.43.0.0/16 to any

   ufw reload

.. tip::

   If your system did not initially use :program:`ufw` at the time K3s was installed, but later does (for example because :program:`ufw` becomes enabled), run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/install-lockss --configure-ufw

   This will run only the :ref:`configuring-ufw` portion of the :doc:`/installing/running` section.

----

.. rubric:: Footnotes

.. [#fnreference]

   References:

   *  https://github.com/k3s-io/k3s/issues/1280

      *  https://github.com/k3s-io/k3s/issues/1280#issuecomment-663269728

.. [#fnrunning]

   See :doc:`/installing/running`.

.. [#fnufw]

   By default, K3s' pod subnet is 10.42.0.0/16 and service subnet is 10.43.0.0/16.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
