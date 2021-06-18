================================
Downloading the LOCKSS Installer
================================

You will need to download the `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ from `GitHub <https://github.com/>`_ using `Git <git>`_.

Follow these instructions as the ``lockss`` user [#fnlockss]_:

1. Run this command:

   .. code-block:: shell

      git clone https://github.com/lockss/lockss-installer

   .. admonition:: Troubleshooting

      On early CentOS 7 systems (for example CentOS 7.1), you may receive the error message ``fatal: unable to access 'https://github.com/lockss/lockss-installer/': Peer reports incompatible or unsupported protocol version``. This is due to outdated network security libraries. Run the command ``yum update -y curl nss nss-util nspr`` as ``root`` to update them, and retry the :program:`git clone` command.

2. Go into the :file:`lockss-installer` directory created by the :program:`git clone` command:

   .. code-block:: shell

      cd lockss-installer

   .. important::

      Many commands in this manual are run from this :file:`lockss-installer` directory. Run the command ``pwd`` to display its full path (typically :file:`/home/lockss/lockss-installer`) and make a note of it.

3. To avoid a harmless Git warning when updating the LOCKSS Installer from GitHub in the future, run this command:

   .. code-block:: shell

      git config --local pull.rebase true

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/appendix/lockss`
