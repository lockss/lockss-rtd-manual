=======================
Working with PostgreSQL
=======================

This section of the appendix documents administrative tasks for the embedded PostgreSQL database configured by the LOCKSS 2.x system.

-----------------------------------------
Changing the PostgreSQL Database Password
-----------------------------------------

Changing the password of the embedded PostgreSQL database must done **while the LOCKSS stack is stopped**, requiring an interruption of service. To perform the change, perform the following steps as the ``lockss`` user [#fnlockss]_ in the :ref:`LOCKSS Installer Directory`:

1. Ensure the LOCKSS stack is stopped by running:

   .. code-block:: shell

      scripts/stop-lockss

2. Ensure the Kubernetes service definitions reflect the current state of the LOCKSS configuration by running:

   .. code-block:: shell

      scripts/assemble-lockss

3. Start only the PostgreSQL database container of the LOCKSS stack by running:

   .. code-block:: shell

      k3s kubectl apply -n lockss --filename=config/configs/lockss-stack/svcs/lockss-postgres-service.yaml

4. Run the following command to store the name of the PostgreSQL database container into the variable ``postgres_pod``:

   .. code-block:: shell

      postgres_pod=$(k3s kubectl get pod -n lockss --selector=io.kompose.service=lockss-postgres-service --output=jsonpath="{.items[0].metadata.name}")

5. Run the following command to store the IP of the PostgreSQL database container into the variable ``postgres_ip``:

   .. code-block:: shell

      postgres_ip=$(k3s kubectl get pod -n lockss --selector=io.kompose.service=lockss-postgres-service --output=jsonpath="{.items[0].status.podIP}")

6. Execute the following command to alter the ``LOCKSS`` database user's password, taking care to replace the placeholder :samp:`{newpassword}` below with your intended new PostgreSQL database password:

   .. code-block:: shell

      echo "ALTER USER \"LOCKSS\" WITH PASSWORD 'newpassword'" | k3s kubectl exec $postgres_pod -n lockss -i -- psql --username=LOCKSS --dbname=postgres

   Successful execution of the command results in the output ``ALTER ROLE``.

7. To verify that the password change worked, run the following command:

   .. code-block:: shell

      k3s kubectl exec $postgres_pod -n lockss -it -- psql --username=LOCKSS --dbname=postgres --host=$postgres_ip

   and enter your new password (represented here as :samp:`{newpassword}`) at the :guilabel:`Password for user LOCKSS` prompt.

   *  If the password change was successful and you enter your new password correctly, you will see a PostgreSQL prompt similar to:

      .. code-block:: text

         psql (9.6.12)
         Type "help" for help.

         postgres=#

      which you can now exit by entering :samp:`\quit` (or :samp:`\q`) or hitting :kbd:`Ctrl+D`.

   *  If the password change was unsuccessful or you do not enter :samp:`{newpassword}` correctly, you will see output similar to:

      .. code-block:: text

         psql: FATAL:  password authentication failed for user "LOCKSS"
         command terminated with exit code 2

8. Stop the PostgreSQL database container by running this command:

   .. code-block:: shell

      k3s kubectl -n lockss delete service,deployment lockss-postgres-service &&
          k3s kubectl -n lockss wait --for=delete pod $postgres_pod --timeout=60s

9. Re-run :program:`configure-lockss` so that you can record the new PostgreSQL database password into the configuration of the LOCKSS stack:

   .. code-block:: shell

      scripts/configure-lockss

   See the :ref:`PostgreSQL` and :ref:`Embedded PostgreSQL Database` sections of :doc:`/configuring` for details.

10. You can then restart your LOCKSS stack if applicable:

   .. code-block:: shell

      scripts/start-lockss

   See :ref:`Starting the LOCKSS system` for details.

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.
