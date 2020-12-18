==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories.

The LOCKSS Installer is available from `GitHub <https://github.com>`_, and you will need a Git client to download it.

----------------
Checking for Git
----------------

Your operating system may already be equipped with a Git client. Type:

.. code-block:: shell

   git --version

If the output is a version number, for example:

.. code-block:: text

   git version 2.28.0

then Git is already installed and you do not need to take further action.

If you see an error message similar to the following:

.. code-block:: text

   bash: git: command not found

then you need to install Git.

--------------
Installing Git
--------------

On many flavors of Linux, you can install Git with the built-in package manager:

*  CentOS 7: see :ref:`git-yum`
*  CentOS 8: see :ref:`git-dnf`
*  Debian: see :ref:`git-apt`
*  Linux Mint: see :ref:`git-apt`
*  OpenSUSE: see :ref:`git-zypper`
*  RHEL 7: see :ref:`git-yum`
*  RHEL 8: see :ref:`git-dnf`
*  Ubuntu: see :ref:`git-apt`

.. _git-apt:

Installing Git with Apt
=======================

Apt is the package manager on **Debian**, **Linux Mint** and **Ubuntu**.

Use these Apt commands to install Git:

.. code-block:: shell

   sudo apt update

   sudo apt install git

.. _git-dnf:

Installing Git with Dnf
=======================

Dnf is the package manager on **CentOS 8** and **RHEL 8**.

Use this Dnf command to install Git:

.. code-block:: shell

   sudo dnf install git

.. _git-yum:

Installing Git with Yum
=======================

Yum is the package manager on **CentOS 7** and **RHEL 7**.

Use this Yum commands to install Git:

.. code-block:: shell

   sudo yum install git

.. _git-zypper:

Installing Git with Zypper
==========================

Zypper is the package manager on **OpenSUSE**.

Use these Zypper commands to install Git:

.. code-block:: shell

   sudo zypper refresh

   sudo zypper install git
