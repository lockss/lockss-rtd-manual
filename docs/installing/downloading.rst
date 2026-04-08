================================
Downloading the LOCKSS Installer
================================

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 1
         :backlinks: none

This section describes how to use the :term:`LOCKSS Downloader` to download the :term:`LOCKSS Installer`.

.. index:: LOCKSS Installer Directory

--------------------------
LOCKSS Installer Directory
--------------------------

.. include:: /glossary/lockss-installer-directory.rst

.. index:: ! LOCKSS_INSTALLER_DIRECTORY
   single: symbol; LOCKSS_INSTALLER_DIRECTORY

In this manual, it will sometimes be represented symbolically as :samp:`{<LOCKSS_INSTALLER_DIR>}`. Many commands, such as those to configure, start and stop the :term:`LOCKSS stack`, are relative to the LOCKSS Installer Directory, meaning you need to navigate to it at the console using :program:`cd` before issuing the relevant command:

:samp:`cd {<LOCKSS_INSTALLER_DIR>}`

.. index:: LOCKSS Installer Directory; default

----------------------------------
Default LOCKSS Installer Directory
----------------------------------

The **default** :ref:`LOCKSS Installer Directory` is :file:`{$HOME}/lockss-installer` relative to the ``lockss`` user, meaning :file:`/home/lockss/lockss-installer` on most Linux systems.

You can specify a :ref:`custom-lockss-installer-directory` when :ref:`Running the LOCKSS Downloader` by using its ``--download-dir`` option.

.. index:: LOCKSS Installer; installation, LOCKSS Downloader; invocation

-----------------------------
Running the LOCKSS Downloader
-----------------------------

To download the :term:`LOCKSS Installer`, you will use :term:`Curl` or :term:`Wget` [#fn-fetcher]_ to invoke the :term:`LOCKSS Downloader`, whose default action is to download the LOCKSS Installer.

1. .. index:: whoami

   Double-check that you are operating in the ``root`` session established for the entirety of this chapter [#fn-root-session]_ by typing:

   .. code-block:: shell

      whoami

   and verifying that the output is ``root``.

2. .. index:: Curl, Wget, runuser

   Run this :program:`curl` or :program:`wget` command as the ``lockss`` user:

   .. tab-set::

      .. tab-item:: Curl
         :sync: curl

         .. code-block:: shell

            curl -sSfL https://lockss.org/downloader | runuser -u lockss sh -s -

      .. tab-item:: Wget
         :sync: wget

         .. code-block:: shell

            wget -qO- https://lockss.org/downloader | runuser -u lockss sh -s -

   This will download the LOCKSS Installer into the :ref:`Default LOCKSS Installer Directory`.

   .. tip::

      .. index:: LOCKSS Installer Directory; custom, LOCKSS Installer; custom directory

      .. dropdown:: Custom LOCKSS Installer Directory
         :name: custom-lockss-installer-directory
         :icon: light-bulb
         :animate: fade-in-slide-down

         If you need your :ref:`LOCKSS Installer Directory` to be a directory :samp:`{DIR}` other than the :ref:`Default LOCKSS Installer Directory`, add :samp:`--download-dir={DIR}` (or :samp:`-d {DIR}`) after ``| runuser -u lockss sh -s -``, like so:

         :samp:`... | runuser -u lockss sh -s - --download-dir={DIR}`

         .. important::

            If you specify a custom LOCKSS Installer Directory in the LOCKSS Downloader when :doc:`index` for the first time, you will need to specify the same custom LOCKSS Installer Directory in the LOCKSS Downloader whenever :doc:`/upgrading/index` in the future.

      .. index:: LOCKSS Installer; custom version, Git, GitHub

      .. dropdown:: Custom version of the LOCKSS Installer
         :name: custom-lockss-installer-version
         :icon: light-bulb
         :animate: fade-in-slide-down

         If you have a reason to install a version of the LOCKSS Installer other than the latest stable release (currently |LATEST_PATCH|), you can do so by making references to the ``lockss-installer`` :term:`Git` repository on :term:`GitHub` [#fn-installer]_:

         *  You can install a version from the tip of a given Git branch :samp:`{BRA}` of the ``lockss-installer`` repository (e.g. ``develop``) by adding :samp:`--git-branch={BRA}` (or :samp:`-b {BRA}`) after ``| runuser -u lockss sh -s -`` in the command above. This might be needed if you are helping the LOCKSS Team test a development, pre-release, or hotfix version of the LOCKSS Installer.

         *  You can install a version labeled by a given Git tag :samp:`{TAG}` of the ``lockss-installer`` repository (e.g. ``version-2.0.91-beta2``) by adding :samp:`--git-tag={TAG}` (or :samp:`-t {TAG}`) after ``| runuser -u lockss sh -s -`` in the command above. This might be needed if you are installing a specific pre-release or past version of the LOCKSS Installer.

         *  You can install a version as of a specific Git commit :samp:`{COM}` of the ``lockss-installer`` repository by adding :samp:`--git-commit={COM}` (or :samp:`-c {COM}`) after ``| runuser -u lockss sh -s -`` in the command above. This might be needed if you are helping the LOCKSS Team test a development version of the LOCKSS Installer from a specific point in time in its Git history.

      .. index:: LOCKSS Installer; pre-inspection, GitHub, Curl, Wget, runuser

      .. dropdown:: Pre-inspecting the LOCKSS Downloader before running it
         :name: downloading-inspecting
         :icon: light-bulb
         :animate: fade-in-slide-down

         For security purposes, you may wish to inspect the LOCKSS Downloader before executing it.

         One option is to review the contents of the script directly on GitHub to your satisfaction, then execute it as described above. The URL https://lockss.org/downloader redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

         Another option is to download a copy of the LOCKSS Downloader script, review it, then execute it, all locally. To do so, follow this procedure:

         1. Navigate into a directory into which the LOCKSS Downloader script will be downloaded, for example:

            .. code-block:: shell

               cd /tmp

         2. Run this :program:`curl` or :program:`wget` command [#fn-fetcher]_ as the ``lockss`` user:

            .. tab-set::

               .. tab-item:: Curl
                  :sync: curl

                  .. code-block:: shell

                     curl -Lo lockss-downloader.sh https://lockss.org/downloader

               .. tab-item:: Wget
                  :sync: wget

                  .. code-block:: shell

                     wget -qO lockss-downloader.sh https://lockss.org/downloader

            This will download the LOCKSS Downloader script into the current directory as :file:`lockss-downloader.sh`.

         3. Inspect the file :file:`lockss-downloader.sh` to your satisfaction.

         4. Run this command:

            .. code-block:: shell

               chmod +x lockss-downloader.sh

            to make the LOCKSS Downloader script executable.

         5. Then run this command:

            .. code-block:: shell

               runuser -u lockss ./lockss-downloader.sh

            to run the LOCKSS Downloader script (as ``lockss``).

            You can append to ``./lockss-downloader.sh`` the same options that can be appended to ``| runuser -u lockss sh -s -`` elsewhere in this section, for instance :samp:`./lockss-downloader --download-dir={DIR}`. See :ref:`custom-lockss-installer-directory` or :ref:`custom-lockss-installer-version` above.

----

.. rubric:: Footnotes

.. [#fn-fetcher]

   See :ref:`prerequisites-fetcher` and :ref:`prerequisites-archiver` in the :ref:`System Software Prerequisites`.

.. [#fn-installer]

   See https://github.com/lockss/lockss-installer.

.. [#fn-root-session]

   See :numref:`Establishing a root Session` (:ref:`Establishing a root Session`).
