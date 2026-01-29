================================
Downloading the LOCKSS Installer
================================

.. note::

   Commands in this section are run as the ``lockss`` user.

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 1
         :backlinks: none

This section describes how to download the LOCKSS Installer with the LOCKSS Downloader [#fn-downloader]_.

--------------------------
LOCKSS Installer Directory
--------------------------

The **LOCKSS Installer Directory** is the directory into which the LOCKSS Installer is downloaded and stored. In this manual, it will sometimes be represented as :samp:`{LOCKSS_INSTALLER_DIR}`. Many commands in this manual, such as those to configure, start and stop the LOCKSS stack, are relative to the LOCKSS Installer Directory, meaning you need to navigate to it at the console using :program:`cd` before issuing the relevant command:

:samp:`cd {LOCKSS_INSTALLER_DIR}`

----------------------------------
Default LOCKSS Installer Directory
----------------------------------

The **default** :ref:`LOCKSS Installer Directory` is :file:`{$HOME}/lockss-installer` (meaning :file:`/home/lockss/lockss-installer` on most Linux systems).

You can specify a :ref:`custom-lockss-installer-directory` when :ref:`Running the LOCKSS Downloader` by using its ``--download-dir`` option. If you specify a :ref:`custom-lockss-installer-directory` in the LOCKSS Downloader when :doc:`index` for the first time, you need to specify the same :ref:`custom-lockss-installer-directory` in the LOCKSS Downloader whenever :doc:`/upgrading/index` in the future.

-----------------------------
Running the LOCKSS Downloader
-----------------------------

To download the LOCKSS Installer, you will use `Curl <https://curl.se/>`_ or `Wget <https://www.gnu.org/software/wget/>`_ [#fn-fetcher]_ to invoke the LOCKSS Downloader [#fn-downloader]_, whose default action is to download the LOCKSS Installer.

Run this Curl or Wget command [#fn-fetcher]_ as the ``lockss`` user:

.. tab-set::

   .. tab-item:: Curl
      :sync: curl

      .. code-block:: shell

         curl -sSfL https://lockss.org/downloader | sh -s -

   .. tab-item:: Wget
      :sync: wget

      .. code-block:: shell

         wget -qO- https://lockss.org/downloader | sh -s -

This will download the LOCKSS Installer into the :ref:`Default LOCKSS Installer Directory`.

.. tip::

   .. dropdown:: Inspecting the LOCKSS Downloader before running it
      :name: downloading-inspecting
      :icon: light-bulb
      :animate: fade-in-slide-down

      For security purposes, you may wish to inspect the LOCKSS Downloader before executing it.

      One option is to review the contents of the script directly on GitHub to your satisfaction, then execute it as described above. The URL https://lockss.org/downloader redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

      Another option is to download a copy of the LOCKSS Downloader script, review it, then execute it, all locally. To do so, follow this procedure:

      1. Navigate into a directory into which the LOCKSS Downloader script will be downloaded, for example:

         .. code-block:: shell

            cd /tmp

      2. Run this Curl or Wget command [#fn-fetcher]_ as the ``lockss`` user:

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

      5. As the ``lockss`` user, type:

         .. code-block:: shell

            ./lockss-downloader.sh

         to run the LOCKSS Downloader script.

         You can append to ``./lockss-downloader.sh`` all the same options that can be appended to the ``| sh -s -`` part of the Curl or Wget commands documented in this section, for instance :samp:`./lockss-downloader --download-dir={DIR}`; see :ref:`custom-lockss-installer-directory` or :ref:`custom-lockss-installer-version` below.

   .. dropdown:: Custom LOCKSS Installer Directory
      :name: custom-lockss-installer-directory
      :icon: light-bulb
      :animate: fade-in-slide-down

      If you need your :ref:`LOCKSS Installer Directory` to be a directory :samp:`{DIR}` other than the :ref:`Default LOCKSS Installer Directory`, add :samp:`--download-dir={DIR}` (or :samp:`-d {DIR}`) after ``| sh -s -``, like so:

      .. code-block:: shell

         ... | sh -s - --download-dir=DIR

   .. dropdown:: Custom version of the LOCKSS Installer
      :name: custom-lockss-installer-version
      :icon: light-bulb
      :animate: fade-in-slide-down

      If you have a reason to install a version of the LOCKSS Installer other than the latest stable release |LATEST_PATCH|, you can do so by making references to the ``lockss-installer`` Git repository on GitHub [#fn-installer]_:

      *  You can install a version from the tip of a given Git branch :samp:`{BRA}` of the ``lockss-installer`` repository (e.g. ``develop``) by adding :samp:`--git-branch={BRA}` (or :samp:`-b {BRA}`) after ``| sh -s -``. This might be needed if you are helping the LOCKSS Team test a development, pre-release, or hotfix version of the LOCKSS Installer.

      *  You can install a version labeled by a given Git tag :samp:`{TAG}` of the ``lockss-installer`` repository (e.g. ``version-2.0.72-alpha7``) by adding :samp:`--git-tag={TAG}` (or :samp:`-t {TAG}`) after ``| sh -s -``. This might be needed if you are installing a specific past version of the LOCKSS Installer.

      *  You can install a version as of a specific Git commit :samp:`{COM}` of the ``lockss-installer`` repository by adding :samp:`--git-commit={COM}` (or :samp:`-c {COM}`) after ``| sh -s -``. This might be needed if you are helping the LOCKSS Team test a development version of the LOCKSS Installer from a specific point in time in its Git history.

   .. dropdown:: Considerations if using ``sudo -u lockss``
      :name: considerations-if-using-sudo-u-lockss
      :icon: light-bulb
      :animate: fade-in-slide-down

      If you must use:

      .. code-block:: shell

         ... | sudo -u lockss sh -s -

      to invoke the LOCKSS Downloader as the ``lockss`` user, beware that *typically* it will run in a context where :samp:`{$HOME}` has been adjusted to the home directory of the ``lockss`` user, but this is *not guaranteed* -- it depends on the way :program:`sudo` is configured on your host system. To *ensure* :samp:`{$HOME}` is set correctly, use the ``-H`` (``--set-home``) option of :program:`sudo`, for example like so:

      .. code-block:: shell

         ... | sudo -Hu lockss sh -s -

----

.. rubric:: Footnotes

.. [#fn-downloader]

   The LOCKSS Downloader is a script to download GitHub projects without Git, but with Curl or Wget instead. See https://github.com/lockss/lockss-downloader.

.. [#fn-fetcher]

   See :ref:`requirement-fetcher` and :ref:`requirement-archiver`.

.. [#fn-installer]

   See https://github.com/lockss/lockss-installer.
