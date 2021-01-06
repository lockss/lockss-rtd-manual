==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories.

The LOCKSS Installer is available from `GitHub <https://github.com/>`_, and you will need a Git client to download it.

Your operating system may already be equipped with a Git client. Type:

.. code-block:: shell

   git --version

If the output is a version number, for example:

.. code-block:: text

   git version 2.21.0

then Git is already installed and you do not need to take any further action.

Otherwise, Git can be installed from your operating system’s software repositories.

-----------------
Git on Arch Linux
-----------------

Use Pacman to install Git on Arch Linux:

.. code-block:: shell

   sudo pacman -S git

-------------
Git on CentOS
-------------

.. caution::

   CentOS 7 is required.

Use Yum to install Git on CentOS:

.. code-block:: shell

   sudo yum install git

-------------
Git on Debian
-------------

.. caution::

   Debian 9 (Stretch) is required.

Use Apt to install Git on Debian:

.. code-block:: shell

   sudo apt-get install git

-------------
Git on Fedora
-------------

.. caution::

   Fedora 28 or better is required.

Use Dnf to install Git on Fedora:

.. code-block:: shell

   sudo dnf install git

-------------------
Git on Oracle Linux
-------------------

.. caution::

   Oracle Linux 7 is required.

Use Yum to install Git on Oracle Linux:

.. code-block:: shell

   sudo yum install git

-------------
Git on Ubuntu
-------------

.. caution::

   Ubuntu 16.04 LTS (Xenial) or better is required.

Use Apt to install Git on Ubuntu:

.. code-block:: shell

   sudo apt-get install git
