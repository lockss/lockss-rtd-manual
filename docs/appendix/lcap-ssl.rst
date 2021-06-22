=============
LCAP Over SSL
=============

The section explains how to configure secure communication between LOCKSS boxes in a network.

Some LOCKSS networks, such as the Global LOCKSS Network (GLN), are open, in the sense that anyone may join and set up a LOCKSS box to participate in that network. The LOCKSS polling protocol (LCAP) includes several security measures to prevent rogue players from disrupting the network, but it is also possible to create a closed network, where only authorized nodes are allowed to participate.  This document describes the steps needed to set up such a network.

In order to ensure that only authorized nodes may participate, each node is issued a private key, and all nodes are provided the set of corresponding public keys. This allows all inter-node communication to be both encrypted and authenticated, using SSL.

.. note::

   The Classic LOCKSS system (version 1.x) does not support PKCS12, so if building keystores for a network that includes classic LOCKSS nodes, JCEKS should be selected.

--------------------
Generating Keystores
--------------------

The authority in charge of the private LOCKSS network (PLN) must create and distribute Java keystores to all participants. Each box receives two keystores: one containing its own private key (along with a password file containing the secret password for the private key) and another containing the public certificates for each of the boxes in the network. There are two methods available to create these keystores:

*  A :ref:`Command Line Tool` run in the LOCKSS development environment.

*  An :ref:`Interactive Tool` invoked in a running LOCKSS node.

In both cases, the admin creating the keystores must know the complete set of hostnames of boxes in the network. More hosts can be added at any time, but a new public keystore must be created and distributed to each box.

Command Line Tool
=================

To use the command line tool:

1. Clone the `lockss-core <https://github.com/lockss/lockss-core>`_ and `laaws-dev-scripts <https://github.com/lockss/laaws-dev-scripts>`_ projects from GitHub, in sibling directories.

2. Build ``lockss-core``.

3. In the root directory of ``lockss-core``, run this command (on a single line):

   .. code-block:: shell

      ../laaws-dev-scripts/bin/runclass org.lockss.keystore.EditKeyStores
          -s pubkeystore.pkcs12 -o keydir
          box1.pln.org ... boxN.pln.org"

   This will create, in the directory :file: :samp:`{keydir}`, a public keystore named :file:`pubkeystore.pkcs12`, and a pair of files for each box: :samp:`box{K}.pln.org.pkcs12` and
:samp:`box{K}.pln.org.pass`.

4. To add additional hosts, provide the existing public keystore as the value of the ``-s`` argument, and list the new hosts. The new public keys will be added to the existing public keystore.

Interactive Tool
================

1. Bring up a LOCKSS stack, either in the production environment or ``runcluster``. In the UI, select :menuselection:`DebugPanel --> Generate LCAP Keys`.

2. Enter the hostname of each of the LOCKSS boxes in the :guilabel:`Hostnames` text box, then click the :guilabel:`Generate Keystores` button. A .tgz or a .zip file will be generated and offered for download. This file will contain the private keystore and password file for each host, as well as the shared public keystore.

3. To add additional hosts, use the :guilabel:`Browse` button to supply the existing public keystore, and enter the new hosts in the :guilabel:`Hostnames` text box.  The downloaded file will contain the private keystore and password files for each new host, as well as the updated shared public keystore, which must be installed on all hosts.

------------------------
Installing the Keystores
------------------------

1. **Securely** transmit to each box its two files and the public keystore. Put them in :file:`~lockss/lockss-installer/config/keys`, and set the owner and group to ``lockss:lockss`` and the permissions to ``600``.

2. Restart the stack and check that it is now using SSL. In the UI, select :menuselection:`Daemon Status --> Comm Channels`. The page should show :guilabel:`SSL: TLSv1.2, Client Auth`.

3. After a few hours, select :menuselection:`Daemon Status --> Comm Peer Data` to ensure that each box is successfully originating and accepting connections from all the other boxes.
