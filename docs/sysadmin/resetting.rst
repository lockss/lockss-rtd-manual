=====================================
Resetting the System to a Blank State
=====================================

**During and after alpha and beta testing,** you may have cause to delete all of the stored content in order to start over. This section provides guidance on how to do this without reinstalling completely from scratch.

LOCKSS 2.x stores content and metadata in several places which depend on how it was configured.  We've provided a script to facilitate deleting all the right directories, but to provide flexibility and make it difficult to do this accidentally, the script generates a second script that actually performs the deletions.

The procedure consists of deleting the PostgreSQL data directory (``lockss-stack-postgres-data``) and Solr data directory (``lockss-stack-solr-data``) from the primary content data storage area, and the repository data directory (``lockss-stack-repo-data``) from each content data storage area, all of which must be done after shutting down the system.

.. rubric:: Directions

1. Stop the stack:

   .. code-block:: shell

      scripts/stop-lockss

2. Generate the deletion script:

   .. code-block:: shell

      scripts/upgrades/generate-content-reset-script > /tmp/delcontent

3. Examine :file:`/tmp/delcontent` if you wish. Note that there is one :command:`sudo` command because the PostgreSQL files are not owned by the ``lockss`` user, which may need modifying in some environments.

4. Make the script executable:

   .. code-block:: shell

      chmod +x /tmp/delcontent

5. Delete the content:

   .. code-block:: shell

      /tmp/delcontent

6. We recommend deleting the script after use:

   .. code-block:: shell

      rm /tmp/delcontent

7. Restart the system:

   .. code-block:: shell

      scripts/start-lockss
