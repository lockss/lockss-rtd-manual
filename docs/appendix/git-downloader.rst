==========================================
Downloading the LOCKSS Installer using Git
==========================================

This section describes how to download the LOCKSS Installer from Git, for development or troubleshooting purposes. **This is not the normal way of using LOCKSS Installer; the normal way to download the LOCKSS Installer is with the LOCKSS Downloader** (see :doc:`/installing/index`).

If you need to install Git (type ``git --version`` at the command line to check), see :doc:`git`.

Follow these instructions as the ``lockss`` user [#fnlockss]_:

1. If you have previously downloaded the LOCKSS Installer the typical way, with the LOCKSS Installer as described in :doc:`/installing/index`:

   a. Go into your existing :ref:`LOCKSS Installation Directory` (by default :file:`{$HOME}/lockss/lockss-installer`, which is typically :file:`/home/lockss/lockss-installer`):

      .. code-block:: shell

         cd /path/to/lockss-installer

   b. Go back into the parent directory:

      .. code-block:: shell

         cd ..

   c. Rename :file:`lockss-installer` to some substitute name :file:`{$OLD_LOCKSS_INSTALLER}`. For instance, if :file:`{$OLD_LOCKSS_INSTALLER}` is :file:`lockss-installer-old`:

      .. code-block:: shell

         mv lockss-installer lockss-installer-old

2. .. tip::

      If you just completed step (1), you are already in this directory; you do not need to perform step (2) and you can move on to step (3).

   Go into the directory in which you want the :file:`lockss-installer` directory to be created; by default this is :file:`{$HOME}/lockss`, which is typically :file:`/home/lockss`:

   .. code-block:: shell

      cd /home/lockss

3. Run this Git command to clone the ``lockss-installer`` project from GitHub:

   .. code-block:: shell

      git clone -c pull.rebase=true https://github.com/lockss/lockss-installer

4. By default, the Git-based LOCKSS Installer is now in the ``develop`` branch, which means that it is in its most current state of development. If this is what you need or have been directed to do, you do not to perform this step, and you can move on to step (5); but if you need to switch to another Git branch, tag or commit, follow these steps:

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

      *  If you need to update the Git state to that of a given commit, use the :program:`git checkout` command with the correct SHA-1 commit identifier, for example:

         .. code-block:: shell

            git checkout 85a62f0188f8dc9d884169c0115a9d5666485915

   c. Return to the parent directory:

      .. code-block:: shell

         cd ..

5. If you have previously downloaded the LOCKSS Installer the typical way, with the LOCKSS Installer as described in :doc:`/installing/index`, you need to copy some of the configuration files from your old LOCKSS Installer directory :file:`{$OLD_LOCKSS_INSTALLER}` to your new LOCKSS Installer Directory ``lockss-installer``. For instance if :file:`{$OLD_LOCKSS_INSTALLER}` is ``lockss-installer-old``:

   .. code-block:: shell

      cp lockss-installer-old/config/*.cfg lockss-installer/config/

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`

