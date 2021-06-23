=======================
Working with PostgreSQL
=======================

This section of the appendix documents administrative tasks for the embedded PostgreSQL database configured by the LOCKSS 2.x system.

-----------------------------------------
Changing the PostgreSQL Database Password
-----------------------------------------

To change the password of the embedded PostgreSQL database, perform the following steps as the ``lockss`` user [#fnlockss]_ in the ``lockss`` user's :file:`lockss-installer` directory:

1. Ensure the Kubernetes service definitions reflect the current state of the LOCKSS configuration by running:

   .. code-block:: shell

      scripts/assemble-lockss

2. Start the PostgreSQL database container by running:

   .. code-block:: shell

      k3s kubectl apply -n lockss --filename=config/configs/lockss-stack/svcs/lockss-postgres-service.yaml

3. Run the following command to store the name of the PostgreSQL database container into the variable ``postgres_pod`` (to be reused later):

   .. code-block:: shell

      postgres_pod=$(k3s kubectl get pod -n lockss --selector=io.kompose.service=lockss-postgres-service --output=jsonpath="{.items[0].metadata.name}")

4. Execute the following command to alter the ``LOCKSS`` database user's password, taking care to replace :samp:`{newpassword}` with your new embedded PostgreSQL database password:

   .. code-block:: shell

      echo "ALTER USER \"LOCKSS\" WITH PASSWORD 'newpassword'" | k3s kubectl exec $postgres_pod -n lockss -i -- psql --username=LOCKSS --dbname=postgres

   Successful execution of the command results in the output ``ALTER ROLE``.

5. *FIXME: insert verification step here*

6. Stop the PostgreSQL database container by running this command:

   .. code-block:: shell

      k3s kubectl -n lockss delete service,deployment lockss-postgres-service &&
          k3s kubectl -n lockss wait --for=delete pod $postgres_pod --timeout=60s

7. Re-run :program:`configure-lockss` so that you can record the new embedded PostgreSQL database password into the configuration of the LOCKSS stack:

   .. code-block:: shell

      scripts/configure-lockss

   See the :ref:`PostgreSQL` and :ref:`Embedded PostgreSQL Database` sections of :doc:`/configuring` for details.

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/appendix/lockss`.
