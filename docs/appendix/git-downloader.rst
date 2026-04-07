==========================================
Downloading the LOCKSS Installer using Git
==========================================

This section describes how to download the LOCKSS Installer from Git, for development or troubleshooting purposes. **This is not the normal way of using LOCKSS Installer; the normal way to download the LOCKSS Installer is with the LOCKSS Downloader, as described in** :doc:`/installing/index`.

Follow these instructions as the ``lockss`` user:

1. You may need to install Git on the host machine. Run this command:

   .. code-block:: shell

      git --version

   *  If you get a version message, for example ``git version 2.51.0``, Git is already installed and no action is needed.

   *  If you get an error message, for example ``bash: git: command not found``, see :doc:`/sysadmin/git` for instructions.

2. Go into the **parent directory** of your intended (or pre-existing, respectively) :ref:`LOCKSS Installer Directory`. This directory is the one where a ``lockss-installer`` subdirectory will (or does, respectively) exist. By default, the LOCKSS Installer Directory is :file:`{$HOME}/lockss-installer`, which is typically :file:`/home/lockss/lockss-installer`, which means the **parent directory** needed here is :file:`{$HOME}`, which is typically :file:`/home/lockss`. Example:

   .. code-block:: shell

      cd /home/lockss

3. If you have previously downloaded the LOCKSS Installer the typical way, with the LOCKSS Downloader as described in :doc:`/installing/index`, you need to rename your pre-existing ``lockss-installer`` directory to some substitute name :file:`{$OLD_LOCKSS_INSTALLER}`. For instance, if :file:`{$OLD_LOCKSS_INSTALLER}` is :file:`lockss-installer-old`:

   .. code-block:: shell

      mv lockss-installer lockss-installer-old

4. Run this Git command to clone the ``lockss-installer`` project from GitHub:

   .. code-block:: shell

      git clone --config pull.rebase=true https://github.com/lockss/lockss-installer

   .. dropdown:: Adjusting to a specific Git branch, tag or commit

      By default, the Git-based LOCKSS Installer is now in the ``develop`` branch, which means that it is in its most current state of development. If this is what you need or have been directed to do, you do not to do anything. But if you need or have been directed to adjust your Git tree to a specific Git branch, tag or commit, you will need to take these steps:

      a. Go into the :file:`lockss-installer` directory:

         .. code-block:: shell

            cd lockss-installer

      b. Perform a Git command appropriate for your situation:

         *  If you need to update the Git state to that of a given branch, use the :program:`git switch` command with the correct branch name, for example:

            .. code-block:: shell

               git switch feature-bugfix1

         *  If you need to update the Git state to that of a given tag, use the :program:`git checkout` command with the correct tag name, for example:

            .. code-block:: shell

               git checkout lockss-2.0.84-beta1

         *  If you need to update the Git state to that of a given commit, use the :program:`git checkout` command with the correct commit identifier, for example:

            .. code-block:: shell

               git checkout 85a62f0188f8dc9d884169c0115a9d5666485915

            Commit identifiers are SHA-1 hashes or abbreviations of SHA-1 hashes.

      c. Return to the parent directory:

         .. code-block:: shell

            cd ..

6. If you have previously downloaded the LOCKSS Installer the typical way, with the LOCKSS Downloader as described in :doc:`/installing/index`, you need to copy some of the configuration files from your old LOCKSS Installer directory :file:`{$OLD_LOCKSS_INSTALLER}` to your new LOCKSS Installer Directory ``lockss-installer``. For instance if :file:`{$OLD_LOCKSS_INSTALLER}` is ``lockss-installer-old``:

   .. code-block:: shell

      cp lockss-installer-old/config/*.cfg lockss-installer/config/
