=========================
Running the LOCKSS System
=========================

After :doc:`configuring` and anytime after updating the LOCKSS Installer to a new version and stopping your LOCKSS stack:

*  Run :file:`scripts/generate-lockss`. This script takes your configuration data and turns into into a set of configuration files containing the right values.

*  Run :file:`scripts/assemble-lockss`. This script puts the configuration files and puts them in the right places, and ensures that all storage volumes are ready for use (creating them if necessary).

*  Run :file:`scripts/deploy-lockss`. This script deploys your LOCKSS stack by invoking Docker.
