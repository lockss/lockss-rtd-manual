=============================
Configuring the LOCKSS System
=============================

After :doc:`installing/index` and :doc:`installing/lockss-installer`, configure the system with the configure script:

.. code-block:: shell

   scripts/configure-lockss

(If you have experience with classic LOCKSS daemon version 1.x, this is the equivalent of ``hostconfig``.)

When run the first time the questions asked by the script often come with a suggested value, displayed in square brackets; hit :kbd:`Enter` to accept the suggested value, or type the correct value and hit :kbd:`Enter`. Any subsequent runs will use the previous values ad the suggested value, review and hit :kbd:`Enter` to leave unchanged.

Questions include:

1. ``Fully qualified hostname (FQDN) of this machine:`` Enter the machine's hostname (e.g. ``locksstest.myuniversity.edu``).

2. ``IP address of this machine:`` The publicly routable IP address of the machine, or if it is not publicly routable but will be accessible via network address translation (NAT), its IP address on the internal network.

3. ``Is this machine behind NAT?:`` Enter :kbd:`Y` if the machine is not publicly routable but will be accessible via network address translation (NAT), or :kbd:`N` otherwise.

   1. ``External IP address for NAT:`` If you answered :kbd:`Y` to the previous question, enter the publicly routable IP address of the machine.

4. ``Initial subnet for admin UI access:`` Enter a semicolon-separated list of subnets in CIDR notation that should have access to the Web user interfaces of the system.

5. ``LCAP V3 protocol port:`` Enter the port on the publicly routable IP address that will be used to receive LCAP (LOCKSS polling and repair) traffic. Historically, most LOCKSS nodes use 9729.

6. ``PROXY port:`` Not yet re-enabled in 2.0-alpha; ignore.

7. ``Mail relay for this machine:`` Hostname for this machine’s outgoing mail server.

9. ``Does mail relay <mailhost> need user & password``: Enter :kbd:`Y` if the outgoing mail server requires password authentication, :kbd:`N` otherwise.

   1. ``User for <mailhost>:`` If you answered :kbd:`Y` to the outgoing mail server password authentication question, enter the username for the mail server.

   2. ``Password for <mailuser>@<mailhost>:`` Enter the password for the given username.

   3. ``Again:`` Re-enter the mail server password (if the two passwords do not match, the password will be asked again).

9. ``E-mail address for administrator:`` Enter the e-mail address of the person or team who will administer the LOCKSS system on this machine.

10. ``Configuration URL:`` Enter the URL of the LOCKSS network configuration file. If you are not running your own LOCKSS network, use ``http://props.lockss.org:8001/demo/lockss.xml``, the configuration file for a demo network set up for LOCKSS 2.0 pre-release testing.

11. ``Configuration proxy (host:port):`` enter a host:port combination for the proxy server needed to reach the network configuration file (or simply hit Enter if none is needed).

12. ``Preservation group(s):`` Enter a semicolon-separated list of preservation network identifiers. If you are not joining an existing network or running your own, enter demo, the network identifier for the demo network set up for LOCKSS 2.0 pre-release testing.

13. ``Content data storage directory:`` Enter the path of a directory that is the root of the main storage area of the LOCKSS system. If you are used to the classic LOCKSS daemon (1.x), this would be the equivalent of :file:`/cache0`.

14. ``Service logs directory:`` Enter the path of a directory that is the root of the storage area for LOCKSS-related log files (historically :file:`/var/log/lockss`).

15. ``Temporary storage directory:`` not actively used in LOCKSS 2.0-alpha2; ignore.

16. ``User name for web UI administration:`` Enter the username for an administrative user in the LOCKSS system’s Web user interfaces.

17. ``Password for web UI administration user <uiuser>:`` Enter the password for the given administrative user in the LOCKSS system’s Web user interfaces [#footnote1]_.

18. ``Password for web UI administration user <uiuser> (again):`` Re-enter the password for the given administrative user in the LOCKSS system’s Web user interfaces (if the two passwords do not match, the password will be asked again).

The next set of questions will gather information about which of the LOCKSS services you will be using and how to access any service you have already configured for use:

19. ``Use LOCKSS Metadata Query Service?:`` Enter :kbd:`Y` to use the included metadata service or :kbd:`N` and no metadata service will be run.

20. ``Use LOCKSS Metadata Extractor Service?:`` Enter :kbd:`Y` to use the included metadata extraction service or :kbd:`N` and no metadata service will be run.

21. ``Use LOCKSS PostgreSQL DB Service?``:

   *  Enter :kbd:`Y` to use the embedded PostgreSQL database.

      1. ``Password for database:`` Enter the password for the PostgreSQL database included in LOCKSS 2.0-alpha2 [#footnote1]_.

      2. ``Password for database (again):`` Re-enter the password for the PostgreSQL database (if the two passwords do not match, the password will be asked again).

   *  Enter :kbd:`N` if you wish to use your own PostgreSQL database. You will be queried for the details of your PostgreSQL service.

      1. ``Fully qualified hostname (FQDN) of PostgreSQL host:`` Enter the hostname of your PostgreSQL database (e.g. ``mypgsql.myuniversity.edu``).

      2. ``Port used by PostgreSQL host:`` Enter the port where your running PostgreSQL database can be reached.

      3. ``Login name for PostgreSQL service:`` Enter the user name for your PostgreSQL database. The default is ``LOCKSS``.

      4. ``Schema for PostgreSQL service:`` Enter the schema name to be used by the LOCKSS system. The default is ``LOCKSS``.

      5. ``Database name prefix for PostgreSQL service:`` Prefix to use for any LOCKSS databases. The default is ``Lockss`` (note the uppercase/lowercase).

      6. ``Password for PostgreSQL database:`` Enter the password for your PostgreSQL database [#footnote1]_.

      7. ``Password for PostgreSQL database (again):`` Re-enter the password for your PostgreSQL database (if the two passwords do not match, the password will be asked again).

22. ``Use LOCKSS Solr Service?:``

   *  Enter :kbd:`Y` if you wish to use the included Solr install.

   *  Enter :kbd:`N` if you wish to use your own Solr database.

      1. ``Fully qualified hostname (FQDN) of Solr host:`` Enter the hostname of your Solr database server (e.g. ``mysolr.myuniversity.edu``).

      2. ``Port used by Solr host:`` Enter the port where your running Solr database server can be reached.

      3. ``Solr core repo name:`` Enter name of the Solr core for the LOCKSS repository. The default is ``lockss-repo``.

23. ``Use LOCKSS PyWb Service?:`` Answer :kbd:`Y` to use PyWb, answer :kbd:`N` and you will be offered the option to use OpenWayback.

24. ``OK to store this configuration:`` Confirm with :kbd:`Y` that the summarized configuration data is correct and that you are ready to write it to a file.

You will prompted to run :file:`scripts/start-lockss` to start the configured system.

.. rubric:: Footnotes

.. [#footnote1]

   Passwords are encrypted in the Docker Secret vault. You should also keep your passwords in a safe place for yourself, as you will need them each time you run :file:`scripts/configure-lockss`. If you change your password in PostgreSQL, you will need to re-run :file:`scripts/configure-lockss` to give the new password to the system.
