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

.. _default-lockss-install-directory:

**By default**, the LOCKSS Installer Directory is a directory named :file:`lockss-installer` in the ``lockss`` user's home directory.

-----------------------------
Running the LOCKSS Downloader
-----------------------------

To install the LOCKSS Installer, you will use :program:`curl` or :program:`wget` [#fncurlwget]_ to invoke the LOCKSS Downloader [#fndownloader]_. (Alternatively, for security purposes, you can download and inspect the LOCKSS Downloader before executing it manually [#fnsecurity]_.)

As the ``lockss`` user [#fnlockss]_, run either this :program:`curl` command:

.. code-block:: shell

   curl -sSfL https://lockss.org/downloader | sh -s -

or this :program:`wget` command:

.. code-block:: shell

   wget -qO- https://lockss.org/downloader | sh -s -

You can add options after ``| sh -s -``:

*  If you need your LOCKSS Installer Directory to be a directory :samp:`{DIR}` other than :ref:`the default <default-lockss-install-directory>`, add :samp:`--download-dir={DIR}` (or alternatively :samp:`-d {DIR}`) after ``| sh -s -``, like so:

   .. code-block:: shell

      ... | sh -s - --download-dir=DIR

   and the LOCKSS Installer will be installed into the custom LOCKSS Installer Directory :samp:`{DIR}`.

*  (Advanced uses only.) If you have a reason to install a version of the LOCKSS Installer other than the latest stable release, you can do so by making references to the ``lockss-installer`` Git repository on GitHub [#fninstaller]_:

   *  You can install a version labeled by the Git tag :samp:`{TAG}` (e.g. ``version-2.0.61-alpha6``) by adding :samp:`--git-tag={TAG}` (or :samp:`-t {TAG}`).

   *  You can install a version from the tip of a Git branch :samp:`{BRA}` (e.g. ``develop``) by adding :samp:`--git-branch={BRA}` (or :samp:`-b {BRA}`).

   *  You can even install a version as of a specific Git commit identifier :samp:`{COM}` by adding :samp:`--git-commit={COM}` (or :samp:`-c {COM}`).

*  The LOCKSS Downloader accepts other options after ``| sh -s -``; you can list them by adding ``--help`` (or ``-h``).

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.

.. [#fncurlwget]

   Most typical Linux systems have at least one of :program:`curl` or :program:`wget` installed by default. You can check by typing ``curl --version`` or ``wget --version`` and verifying that the output is not an error message. If you need to install :program:`curl`, see :doc:`/sysadmin/curl`. If you prefer to install :program:`wget`, see :doc:`/sysadmin/wget`.

.. [#fndownloader]

   See https://github.com/lockss/lockss-downloader.

.. [#fninstaller]

   See https://github.com/lockss/lockss-installer.

.. [#fnsecurity]

   For security purposes, you may wish to inspect the LOCKSS Downloader before executing it.

   One option is to review the contents of the script directly on GitHub to your satisfaction, then execute it as described above. The URL https://lockss.org/downloader redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

   Another option is to download a copy of the LOCKSS Downloader, review the :program:`lockss-downloader` script, then execute it, all locally. To do so, follow this procedure:

   1. Run either:

      .. code-block:: shell

         curl -Lo /tmp/lockss-downloader https://lockss.org/downloader

      or:

      .. code-block:: shell

         wget -O /tmp/lockss-downloader https://lockss.org/downloader

      to download the :program:`lockss-downloader` script to :file:`/tmp/lockss-downloader`.

   2. Inspect :file:`/tmp/lockss-downloader` to your satisfaction.

   3. Run this command:

      .. code-block:: shell

         chmod +x /tmp/lockss-downloader

      to make :file:`/tmp/lockss-downloader` executable.

   4. Type:

      .. code-block:: shell

         /tmp/lockss-downloader

      to run the :program:`lockss-downloader` script, appending options like :samp:`--download-dir={DIR}` to the end as desired.
