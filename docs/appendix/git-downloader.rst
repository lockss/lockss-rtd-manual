=====================================================
Downloading the LOCKSS Installer using :program:`git`
=====================================================

.. warning::

   **The official way to download the LOCKSS Installer is now through the LOCKSS Downloader, rather than cloning the LOCKSS Installer as a Git project as in previous releases.**

   Follow the instructions in :doc:`/installing/index` to use the LOCKSS Downloader.

.. tip::

   Follow the instructions in :doc:`/appendix/git` to install :program:`git`, if it is not yet available on your system.

Follow these instructions as the ``lockss`` user [#fnlockss]_:

1. If you have not previously cloned the LOCKSS Installer, run this command to clone it from GitHub:

   .. code-block:: shell

      git clone https://github.com/lockss/lockss-installer

   .. admonition:: Troubleshooting

      On early CentOS 7 systems (for example CentOS 7.1), you may receive the error message ``fatal: unable to access 'https://github.com/lockss/lockss-installer/': Peer reports incompatible or unsupported protocol version``. This is due to outdated network security libraries. Run the command ``yum update -y curl nss nss-util nspr`` as ``root`` to update them, and retry the :program:`git clone` command.

   .. tip::

      To avoid a harmless Git warning when updating the LOCKSS Installer from GitHub in the future, run this command within the :file:`lockss-installer` directory created by the :program:`git clone` command:

      .. code-block:: shell

         git config --local pull.rebase true

2. Checkout the 2.0-alpha5 branch of the LOCKSS Installer by running this command within the :file:`lockss-installer` directory created by the :program:`git clone` command earlier:

   .. code-block:: shell

      git checkout 2.0-alpha5

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`

