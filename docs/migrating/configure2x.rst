===============================================
Configuring the LOCKSS 2.x System for Migration
===============================================

After `installing the LOCKSS system <installing>`, you will configure it with the :program:`configure-lockss --migrate` script. If you have experience with classic LOCKSS daemon version 1.x, this is the equivalent of :program:`hostconfig`.

-----------------------------------------------------
Before Invoking :program:`configure-lockss --migrate`
-----------------------------------------------------

Gathering Information

* You will need to gather all of the information listed in 4.1 except for the first three bullet points

* If you are migrating from a different host, we strongly reccomend copy the :file:`/etc/lockss/config.dat` from the LOCKSS 1.x host to a file on the LOCKSS 2.x host eg file:`/tmp/v1config.dat`


----------------------------------------------
Invoking :program:`configure-lockss --migrate`
----------------------------------------------

To invoke :program:`configure-lockss`, simply run this command in the ``lockss`` user's :file:`lockss-installer` directory as ``lockss`` [#fnlockss]_:

.. code-block:: shell

   scripts/configure-lockss --migrate

The script will begin with the first series of configuration questions, about :ref:`Kubernetes Settings`.

-------------------
Kubernetes Settings
-------------------

Prompt: :guilabel:`Command to use to execute kubectl commands`

Enter the command to invoke :program:`kubectl` in your environment. If you are using the K3s Kubernetes environment that ships with the LOCKSS system, the proposed value is already correct.

.. FIXME the script can exit here if the K8s (sic) config file can't be written to

-------------------
Migration Settings
-------------------
The configure script will attempt to locate a configuration file from a LOCKSS 1.x running on the host.

If :file:`/etc/lockss/config.dat` is detected:

LOCKSS 1.x installation detected on machine
============================================

Prompt: :guilabel:`Do you want to migrate its content to this LOCKSS 2.0 installation?`

If you will be migrating from the LOCKSS 1.x on the same machine enter :kbd:`Y`; otherwise, enter :kbd:`N`.

If you answered :kbd:`Y`, the data will be read from the config.dat file and you will be asked to confirm each configuration value (see below)

   .. caution::

      If you enter :kbd:`N`, you will immediately exit. Migrating from another host while a LOCKSS 1.x installation is present on this host is not supported

No LOCKSS 1.x installation detected on machine.
================================================

Prompt: :guilabel:`Did you copy a LOCKSS 1.x config.dat file to this host?`

If you copied the LOCKSS configuration :file:`/etc/lockss/config.dat` to the LOCKSS 2.x machine enter :kbd:`Y`; otherwise, enter :kbd:`N`.

If you answered :kbd:`Y`, you will be asked to enter the path to the copied file.

Prompt: :guilabel:`Location of copied LOCKSS 1.x config.dat file.: [/tmp/v1config.dat]`

The data will be read from the copied configuration file and you will be asked to confirm each configuration value (see below)

If you answered :kbd:`N`, you will need to enter more information see section below.


Imported Settings
=================
The following values were imported from your LOCKSS 1.x configuration.
You will be asked to confirm the settings which were set by importing the data. Hit :kbd:`Enter` to accept the default in square brackets.
For more information on each setting see :doc:`/configuring`

   .. caution::

      Only in exceptional circumstances should you modify the defaults as given.

Hostname
--------

Prompt: :guilabel:`Fully qualified hostname (FQDN) of this machine`

The machine's fully-qualified hostname (meaning with its domain name), for example :samp:`locksstest.myuniversity.edu`.

IP Address
----------

Prompt: :guilabel:`IP address of this machine`

If the machine is publicly routable, meaning it has an IP address that can be used to identify it over the Internet, the publicly routable IP address. Otherwise, if the machine is accessible via network address translation (NAT), meaning it has an IP address that is valid only on your local network but it can be reached from the Internet via a NAT router, enter the internal IP address.

Initial UI Subnet
-----------------

Prompt: :guilabel:`Initial subnet(s) for admin UI access`

The semicolon-separated list of subnets in CIDR or mask notation that should initially have access to the Web user interfaces (UI) of the system. The access list can be modified later via the UI.

LCAP Port
---------

Prompt: :guilabel:`LCAP protocol port`

The port on the publicly routable IP address that will be used to receive LCAP (LOCKSS polling and repair) traffic. Historically, most LOCKSS nodes use :samp:`9729`.

Temporary LOCKSS 2.x LCAP PORT
------------------------------

Prompt: :guilabel:`Temporary LOCKSS 2.x LCAP port`

When migrating on the same host, the system will need an LCAP port different from the one used by LOCKSS 1.x during migration.

Network Address Translation
---------------------------

1. Prompt: :guilabel:`Is this machine behind NAT?`

   If the machine is publicly routable, value is :kbd:`N`; otherwise, if the machine is not publicly routable but will be accessible via network address translation (NAT) value is :kbd:`Y`.

2. If value is :kbd:`Y`, additional configuration question will be shown:

   :guilabel:`External IP address for NAT`

   The publicly routable IP address of the NAT router.

Mail Relay
----------

Prompt: :guilabel:`Mail relay for this machine`

The hostname of this machine's outgoing mail server, for example :samp:`smtp.myuniversity.edu`.

Mail Relay Credentials
----------------------

1. Prompt: :guilabel:`Does the mail relay <mailhost> need a username and password?`

   If the outgoing mail server does not require password authentication, value is :kbd:`N`; otherwise, :kbd:`Y`.

2. If  :kbd:`Y`, you will be asked additional configuration questions:

   1. Prompt: :guilabel:`User for <mailhost>`

     The username for the mail server.

   2. Prompt: :guilabel:`Password for <mailuser>@<mailhost>`

     The password for the username on the mail server.

   3. Prompt: :guilabel:`Password for <mailuser>@<mailhost> (again)`

      Re-enter the password for the username on the mail server.

Administrator Email
-------------------

Prompt: :guilabel:`E-mail address for administrator`

The e-mail address of the person or team who will administer the LOCKSS system on this machine.


Configuration URL
-----------------

1. Prompt: :guilabel:`Configuration URL`

  The URL of your LOCKSS 1.x network's configuration file. Select a scenario below for more details:


Configuration Proxy
-------------------

Prompt: :guilabel:`Configuration proxy (host:port)`

If the configuration URL can be reached directly, leave this blank; otherwise, if a proxy server is required to reach the configuration URL, enter its host and port in :samp:`{host}:{port}` format (for example :samp:`proxy.myuniversity.edu:8080`).

Preservation Groups
-------------------

Prompt: :guilabel:`Preservation group(s)`

The preservation group identifier or semicolon-separated list of preservation group identifiers. Select a scenario below for more details:


Web User Interface Settings
---------------------------

1. Prompt: :guilabel:`User name for web UI administration`

   The username for the primary administrative user in the LOCKSS system's Web user interfaces.

Mark this the end of defaults

2. Prompt: :guilabel:`Password for web UI administration user <uiuser>`

   Enter a password for the primary administrative user.

3. Prompt: :guilabel:`Password for web UI administration user <uiuser> (again)`

   Re-enter the password for the primary administrative user. If the two passwords do not match, the password will be asked again.

Continue with the configure script :doc:`/configuring`.

--------------------------------------------
No LOCKSS 1.x configuration file available.
--------------------------------------------

If the configuration file from the LOCKSS 1.x host is not available. More information will be needed.

Prompt: :guilabel:`Is the LOCKSS 1.x machine behind NAT?`

If you enter :kbd: `N`

Prompt: :guilabel:`LOCKSS 1.x IP address`

Enter the IP address of the LOCKSS 1.x host.

Prompt: :guilabel:`LOCKSS 1.x LCAP port`

If you enter :kbd `Y`

Prompt: :guilabel:`LOCKSS 1.x external IP address`

Enter the publicly routable IP address of the NAT router.  The address that LOCKSS boxes uses to communicate with this box.

Prompt: :guilabel:`LOCKSS 1.x routable IP address`

Enter the IP address that the LOCKSS 2.x machine will use to talk to the LOCKSS 1.x machine.

Prompt: :guilabel:`LOCKSS 1.x LCAP port`

The port in use by LOCKSS 1.x

Continue with the configure script, :doc:`/configuring` 4.6

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.
