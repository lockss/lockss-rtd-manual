====================
Installing OpenJDK 8
====================

Temporarily in LOCKSS 2.0-alpha2, Java 8 is needed on the host machine to run the Solr upgrade tool. (In the future, this process will be packaged in a way that does not require Java to be installed.)

--------------------
Debian, Ubuntu, etc.
--------------------

On the command line, type:

.. code-block:: shell

   sudo apt-get install openjdk-8-jre

----------------------------------------------------
Fedora, Oracle Linux, Red Hat Enterprise Linux, etc.
----------------------------------------------------

On the command line, type:

.. code-block:: shell

   sudo yum install java-1.8.0-openjdk
