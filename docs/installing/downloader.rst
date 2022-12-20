================================
Downloading the LOCKSS Installer
================================

FIXME

.. note::

   Commands in this section are run as the ``lockss`` user  [#fnlockss]_.

The next task is to download the LOCKSS Installer. To do this, you will use :program:`curl` or :program:`wget` [#fncurlwget]_ to invoke the LOCKSS Downloader [#fndownloader]_. (Alternatively, for security purposes, you can inspect the LOCKSS Downloader before executing it manually [#fnsecurity]_.)

As the ``lockss`` user [#fnlockss]_, run either this :program:`curl` command:

.. code-block:: shell

   curl -sSfL https://www.lockss.org/downloader | sh -s -

or this :program:`wget` command:

.. code-block:: shell

   wget -qO- https://www.lockss.org/downloader | sh -s -

This will download and invoke the LOCKSS Downloader, which in turn will download the latest version of the LOCKSS Installer into :file:`{$HOME}/lockss-installer` (in this case :file:`/home/lockss/lockss-installer`).

.. tip::

   To install it into another directory :samp:`{DIR}`, add :samp:`--download-dir={DIR}` after ``sh -s -``, like so:

   .. code-block:: shell

      ... | sh -s - --download-dir=DIR

   The :program:`lockss-downloader` script accepts other options after ``sh -s -``. You can list them by invoking it with the ``--help`` option.

.. important::

   .. _lockss-installer-directory:

   .. rubric:: LOCKSS Installer Directory

   Whether it is the default directory :file:`{$HOME}/lockss-installer` or a custom directory passed to the LOCKSS Downloader via the ``--download-dir`` option, make a note of the LOCKSS Installer directory, as many commands in this manual are documented relative to this directory.

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

   One option is to review the contents of the script directly on GitHub to your satisfaction, then execute it as described above. The URL https://www.lockss.org/downloader redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

   Another option is to download a copy of the LOCKSS Downloader, review the :program:`lockss-downloader` script, then execute it, all locally. To do so, follow this procedure:

   1. Run either:

      .. code-block:: shell

         curl -Lo /tmp/lockss-downloader https://www.lockss.org/downloader

      or:

      .. code-block:: shell

         wget -O /tmp/lockss-downloader https://www.lockss.org/downloader

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
