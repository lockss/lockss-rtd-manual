================================
Downloading the LOCKSS Installer
================================

.. note::

   Commands in this section are run as the ``lockss`` user  [#fnlockss]_.

The next task is to download the LOCKSS Installer.

--------------------------
LOCKSS Installer Directory
--------------------------

The LOCKSS Installer will be installed into a directory that will simply be known as the **LOCKSS Installer Directory**. Many commands in upcoming sections of this manual, such as those to install, configure, start and stop the LOCKSS system, will be listed relative to the LOCKSS Installer Directory.

-----------------------------
Running the LOCKSS Downloader
-----------------------------

To install the LOCKSS Installer, you will use `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_ [#fnfetcher]_ to invoke the LOCKSS Downloader [#fndownloader]_.

As the ``lockss`` user [#fnlockss]_, run this Curl, Wget or HTTPie command [#fnfetcher]_:

.. tab-set::

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

.. _default-lockss-install-directory:

**By default**, this will download the LOCKSS Installer into the default :ref:`LOCKSS Installer Directory` ``${HOME}/lockss-installer`` (where ``${HOME}`` refers to the ``lockss`` user's home directory).

.. tip::

   .. dropdown:: Custom LOCKSS Installer Directory

      If you need your :ref:`LOCKSS Installer Directory` to be a directory :samp:`{DIR}` other than :ref:`the default <default-lockss-install-directory>`, add :samp:`--download-dir={DIR}` (or :samp:`-d {DIR}`) after ``| sh -s -``, like so:

         .. code-block:: shell

            ... | sh -s - --download-dir=DIR

   .. dropdown:: Custom version of the LOCKSS Installer

      If you have a reason to install a version of the LOCKSS Installer other than the latest stable release, you can do so by making references to the ``lockss-installer`` Git repository on GitHub [#fninstaller]_:

      *  You can install a version from the tip of a given Git branch :samp:`{BRA}` (e.g. ``develop``) by adding :samp:`--git-branch={BRA}` (or :samp:`-b {BRA}`).

      *  You can install a version labeled by a given Git tag :samp:`{TAG}` (e.g. ``version-2.0.61-alpha6``) by adding :samp:`--git-tag={TAG}` (or :samp:`-t {TAG}`).

      *  You can even install a version as of a specific Git commit identifier :samp:`{COM}` by adding :samp:`--git-commit={COM}` (or :samp:`-c {COM}`).

   .. dropdown:: Inspecting the LOCKSS Downloader before running it

      For security purposes, you may wish to inspect the LOCKSS Downloader before executing it.

      One option is to review the contents of the script directly on GitHub to your satisfaction, then execute it as described above. The URL https://lockss.org/downloader redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

      Another option is to download a copy of the LOCKSS Downloader script, review it, then execute it, all locally. To do so, follow this procedure:

      1. As the ``lockss`` user [#fnlockss]_, run this Curl, Wget or HTTPie command [#fnfetcher]_:

         .. tab-set::

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

         This will download the LOCKSS Downloader into the current directory as :file:`lockss-downloader`.

      2. Inspect the file :file:`lockss-downloader` to your satisfaction.

      3. Run this command:

         .. code-block:: shell

            chmod +x lockss-downloader

         to make the file :file:`lockss-downloader` executable.

      4. Type:

         .. code-block:: shell

            ./lockss-downloader

         to run the LOCKSS Downloader, appending options like :samp:`--download-dir={DIR}` to the end as desired.

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.

.. [#fnfetcher]

   Most typical Linux systems have at least one of `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_ installed by default. You can check by typing ``curl --version``, ``wget --version`` or ``http --version``, and seeing which ones do not output an error message. See :doc:`/sysadmin/curl`, :doc:`/sysadmin/wget` or :doc:`/sysadmin/httpie` for installation instructions.

.. [#fndownloader]

   The `LOCKSS Downloader <https://github.com/lockss/lockss-downloader>`_ is a script to download GitHub projects without Git, with Curl, Wget or HTTPie instead.

.. [#fninstaller]

   See https://github.com/lockss/lockss-installer.
