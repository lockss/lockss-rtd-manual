===============
Installing Snap
===============

`Snap <https://snapcraft.io/>`_ is a Linux application package manager maintained by `Canonical <https://canonical.com/>`_, makers of `Ubuntu <https://ubuntu.com/>`_.

Snap is needed to install `MicroK8s <https://microk8s.io/>`_ (a lightweight `Kubernetes <https://kubernetes.io/>`_ environment used by the LOCKSS system), which is also maintained by Canonical (and therefore only installed via Snap).

More complete instructions can be found at "`Installing snapd <https://snapcraft.io/docs/installing-snapd>`_" on `Snapcraft <https://snapcraft.io/>`_, Snap's home Web site, but we also provide some high level installation instructions below.

-----------------
Checking for Snap
-----------------

Some Linux flavors come with Snap pre-installed, for instance **Ubuntu**. To determine if your operating system is already be equipped with Snap, type:

.. code-block:: shell

   snap version

If you see something similar to the following:

.. code-block:: text

   snap    2.46.1-1
   snapd   2.46.1-1
   series  16
   kernel  5.8.13

then Snap is already installed and you do not need to take further action.

If you see an error message similar to the following:

.. code-block:: shell

   bash: snap: command not found

then you need to install Snap.

---------------
Installing Snap
---------------

On many flavors of Linux, you can install Snap with the built-in package manager:

*  CentOS 7: see :ref:`snap-yum`
*  CentOS 8: see :ref:`snap-dnf`
*  Debian: see :ref:`snap-apt`
*  Linux Mint: see :ref:`snap-apt`
*  OpenSUSE: see :ref:`snap-zypper`
*  RHEL 7: see :ref:`snap-yum`
*  RHEL 8: see :ref:`snap-dnf`
*  Ubuntu: see :ref:`snap-apt`

.. _snap-apt:

Installing Snap with Apt
========================

Apt is the package manager on **Debian**, **Linux Mint** and **Ubuntu**.

.. admonition:: Preliminary Steps for Linux Mint 20

   Before you can install Snap on **Linux Mint 20**, you first need to type this command:

   .. code-block:: shell

      sudo rm /etc/apt/preferences.d/nosnap.pref

   This step is not needed for Linux Mint 19.

Use these Apt commands to install Snap:

.. code-block:: shell

   sudo apt update

   sudo apt install snapd

You can then proceed to the next step, :ref:`confinement`.

.. _snap-dnf:

Installing Snap with Dnf
========================

Dnf is the package manager on **CentOS 8** and **RHEL 8**.

.. admonition:: Preliminary Steps for CentOS 8

   Before you can install Snap on **CentOS 8**, you first need to type this Dnf command:

   .. code-block:: shell

      sudo dnf install epel-release

.. admonition:: Preliminary Steps for RHEL 8

   Before you can install Snap on **RHEL 8**, you first need to type this Dnf command:

   .. code-block:: shell

      sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

Use this Dnf command to install Snap:

.. code-block:: shell

   sudo dnf install snapd

You can then proceed to the next step, :ref:`confinement`.

.. _snap-yum:

Installing Snap with Yum
========================

Yum is the package manager on **CentOS 7** and **RHEL 7**.

.. admonition:: Preliminary Steps for CentOS 7

   Before you can install Snap on **CentOS 7**, you first need to type this Yum command:

   .. code-block:: shell

      sudo yum install epel-release

.. admonition:: Preliminary Steps for RHEL 7

   Before you can install Snap on **RHEL 7**, you first need to type these commands:

   .. code-block:: shell

      sudo rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

      sudo subscription-manager repos --enable "rhel-*-optional-rpms" --enable "rhel-*-extras-rpms"

Use this Yum command to install Snap:

.. code-block:: shell

   sudo yum install snapd

You can then proceed to the next step, :ref:`confinement`.

.. rubric:: References

*  `Installing snap on CentOS <https://snapcraft.io/docs/installing-snap-on-centos>`_
*  `Installing snap on Red Hat Enterprise Linux (RHEL) <https://snapcraft.io/docs/installing-snap-on-red-hat>`_

.. _snap-zypper:

Installing Snap with Zypper
===========================

Zypper is the package manager on **OpenSUSE**.

First, use one of these Zypper commands (note the slight variation based on the exact version of your system):

.. code-block:: shell

   # For OpenSUSE Leap 15.2:
   sudo zypper addrepo --refresh https://download.opensuse.org/repositories/system:/snappy/openSUSE_Leap_15.2 snappy

   # For OpenSUSE Leap 15.1:
   sudo zypper addrepo --refresh https://download.opensuse.org/repositories/system:/snappy/openSUSE_Leap_15.1 snappy

   # For OpenSUSE Leap 15.0:
   sudo zypper addrepo --refresh https://download.opensuse.org/repositories/system:/snappy/openSUSE_Leap_15.0 snappy

Then use these Zypper commands to install Snap:

.. code-block:: shell

   sudo zypper --gpg-auto-import-keys refresh

   sudo zypper dup --from snappy

   sudo zypper install snapd

You can then proceed to the next step, :ref:`confinement`.

.. rubric:: References

*  `Installing snap on openSUSE <https://snapcraft.io/docs/installing-snap-on-opensuse>`_

.. _confinement:

----------------------------
Enabling Classic Confinement
----------------------------

MicroK8s uses Snap's so-called classic confinement model, which expects a top-level directory named :file:`/snap` on your system. Nowadays this directory is located at :file:`/var/lib/snapd/snap`. In order for Snap to install MicroK8s correctly, you need to create a symbolic link from :file:`/snap` to :file:`/var/lib/snapd/snap` with this command:

.. code-block:: shell

   sudo ln -s /var/lib/snapd/snap /snap

(On some systems like Debian, :file:`/snap` may already exist.)

-------------
Enabling Snap
-------------

You can then enable Snap on your system with the following command:

.. code-block:: shell

   sudo systemctl enable --now snapd.socket

-----------------------
Logging Out and Back In
-----------------------

Log out and back in again (or restart your system) to ensure Snap's paths are updated correctly.

--------------
Verifying Snap
--------------

Snap offers a way to verify that things work correctly, by installing and running the `hello-world` Snap package. Type this Snap command:

.. code-block:: shell

   sudo snap install hello-world

and then verify that this command:

.. code-block:: shell

   hello-world

outputs the greeting ``Hello World!``.

------------------------
Configuring Snap Updates
------------------------

The snap daemon will automatically update any installed Snap packages and by default it will check every four hours for updates.

For stability, you should adjust the frequency at which Snap checks and updates your Snap packages.

To adjust your update schedule to a year (the maximum allowed), use a refresh hold:

.. code-block:: shell

   sudo snap set system refresh.hold="$(date --date='364 days' +%Y-%m-%dT%H:%M:%S%:z)"
