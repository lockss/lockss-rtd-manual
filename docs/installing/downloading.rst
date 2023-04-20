================================
Downloading the LOCKSS Installer
================================

.. note::

   Commands in this section are run as the ``lockss`` user  [#fnlockss]_.

**The next task is to download the LOCKSS Installer.**

--------------------------
LOCKSS Installer Directory
--------------------------

The directory into which the LOCKSS Installer is downloaded will simply be known as the **LOCKSS Installer Directory**. Many commands in upcoming sections of this manual, such as those to install, configure, start and stop the LOCKSS system, will be listed relative to the LOCKSS Installer Directory.

.. _default-lockss-installer-directory:

.. rubric:: Default LOCKSS Installer Directory

Unless you use the ``--download-dir`` option below to customize the LOCKSS Installer Directory on your host, the **default LOCKSS Installer Directory** will be ``${HOME}/lockss-installer``, where ``${HOME}`` refers to the ``lockss`` user's home directory.

-----------------------------
Running the LOCKSS Downloader
-----------------------------

To download the LOCKSS Installer, you will use `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_ [#fnfetcher]_ to invoke the LOCKSS Downloader [#fndownloader]_, whose default action is to download the LOCKSS Installer.

As the ``lockss`` user [#fnlockss]_, run this Curl, Wget or HTTPie command [#fnfetcher]_:

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: Curl
      :sync: curl

      .. code-block:: shell

         curl -sSfL https://lockss.org/downloader | sh -s -

   .. tab-item:: HTTPie
      :sync: httpie

      .. code-block:: shell

         http -qd https://lockss.org/downloader | sh -s -

   .. tab-item:: Wget
      :sync: wget

      .. code-block:: shell

         wget -qO- https://lockss.org/downloader | sh -s -

This will download the LOCKSS Installer into the :ref:`default-lockss-installer-directory`.

.. tip::

   Below are some advanced tips for this section.

   .. dropdown:: Inspecting the LOCKSS Downloader before running it

      For security purposes, you may wish to inspect the LOCKSS Downloader before executing it.

      One option is to review the contents of the script directly on GitHub to your satisfaction, then execute it as described above. The URL https://lockss.org/downloader redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

      Another option is to download a copy of the LOCKSS Downloader script, review it, then execute it, all locally. To do so, follow this procedure:

      1. As the ``lockss`` user [#fnlockss]_, run this Curl, Wget or HTTPie command [#fnfetcher]_:

         .. tab-set::
            :class: sd-bg-light

            .. tab-item:: Curl
               :sync: curl


               .. code-block:: shell

                  curl -Lo lockss-downloader https://lockss.org/downloader | sh -s -

            .. tab-item:: HTTPie
               :sync: httpie

               .. code-block:: shell

                  http -qdo lockss-downloader https://lockss.org/downloader | sh -s -

            .. tab-item:: Wget
               :sync: wget

               .. code-block:: shell

                  wget -qO lockss-downloader https://lockss.org/downloader | sh -s -

         This will download the LOCKSS Downloader script into the current directory as :file:`lockss-downloader`.

      2. Inspect the file :file:`lockss-downloader` to your satisfaction.

      3. Run this command:

         .. code-block:: shell

            chmod +x lockss-downloader

         to make the LOCKSS Downloade4r script executable.

      4. Type:

         .. code-block:: shell

            ./lockss-downloader

         to run the LOCKSS Downloader script. You can append to ``./lockss-downloader`` all the same options that can be appended to ``| sh -s -`` in the normal procedure documented in this section, for instance :samp:`./lockss-downloader --download-dir={DIR}`.

   .. dropdown:: Custom LOCKSS Installer Directory

      If you need your :ref:`LOCKSS Installer Directory` to be a directory :samp:`{DIR}` other than the :ref:`default-lockss-installer-directory`, add :samp:`--download-dir={DIR}` (or :samp:`-d {DIR}`) after ``| sh -s -``, like so:

         .. code-block:: shell

            ... | sh -s - --download-dir=DIR

   .. dropdown:: Custom version of the LOCKSS Installer

      If you have a reason to install a version of the LOCKSS Installer other than the latest stable release |LATEST_PATCH|, you can do so by making references to the ``lockss-installer`` Git repository on GitHub [#fninstaller]_:

      *  You can install a version from the tip of a given branch :samp:`{BRA}` of the ``lockss-installer`` Git repository (e.g. ``develop``) by adding :samp:`--git-branch={BRA}` (or :samp:`-b {BRA}`) after ``| sh -s -``. This might be needed if you are helping the LOCKSS Team test a development, pre-release, or hotfix version of the LOCKSS Installer.

      *  You can install a version labeled by a given tag :samp:`{TAG}` of the ``lockss-installer`` Git repository (e.g. ``version-2.0.61-alpha6``) by adding :samp:`--git-tag={TAG}` (or :samp:`-t {TAG}`) after ``| sh -s -``. This might be needed if you are installing a specific past version of the LOCKSS Installer.

      *  You can install a version as of a specific commit identifier :samp:`{COM}` of the ``lockss-installer`` Git repository by adding :samp:`--git-commit={COM}` (or :samp:`-c {COM}`) after ``| sh -s -``. This might be needed if you are helping the LOCKSS Team test a development version of the LOCKSS Installer.

   .. dropdown:: Considerations if using ``sudo -u``

      If you must use:

      .. code-block:: shell

         ... | sudo -u lockss sh -s -

      to invoke the LOCKSS Downloader as the ``lockss`` user, beware that *typically* it will run in a context where ``${HOME}`` has been adjusted to the home directory of the ``lockss`` user, but this is *not guaranteed* -- it depends on the way :program:`sudo` is configured on your host system. To *ensure* ``${HOME}`` is set correctly, use the ``-H`` (``--set-home``) option of :program:`sudo`, for example like so:

      .. code-block:: shell

         ... | sudo -Hu lockss sh -s -

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.

.. [#fnfetcher]

   Most typical Linux systems have at least one of `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_ installed by default. You can check by typing ``curl --version``, ``wget --version`` or ``http --version``, and seeing which ones do not output an error message. See :doc:`/sysadmin/curl`, :doc:`/sysadmin/wget` or :doc:`/sysadmin/httpie` for installation instructions.

.. [#fndownloader]

   The LOCKSS Downloader is a script to download GitHub projects without Git, with Curl, Wget or HTTPie instead. See https://github.com/lockss/lockss-downloader.

.. [#fninstaller]

   See https://github.com/lockss/lockss-installer.
