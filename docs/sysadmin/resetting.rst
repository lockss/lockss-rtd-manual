=====================================
Resetting the System to a Blank State
=====================================

**During alpha and beta testing,** you may have cause to delete all of the stored content in order to start over. This section provides guidance on how to do this without reinstalling completely from scratch.

The procedure consists of deleting the PostgreSQL data directory (``lockss-stack-postgres-data``) and Solr data directory (``lockss-stack-solr-data``) from the primary content data storage area, and the repository data directory (``lockss-stack-repo-data``) from each content data storage area, all of which must be done after shutting down the system.

FIXME
