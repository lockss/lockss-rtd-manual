=============================
Configuring the LOCKSS System
=============================

After :doc:`installing/index` and :doc:`installing/lockss-installer`, configure the system with the configure script:

.. code-block:: shell

   scripts/configure-lockss

(If you have experience with classic LOCKSS daemon version 1.x, this is the equivalent of ``hostconfig``.)

The questions asked by the script often come with a suggested value, displayed in square brackets; hit :kbd:`Enter` to accept the suggested value, or type the correct value and hit Enter. Questions include:

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

17. ``Password for web UI administration user <uiuser>:`` Enter the password for the given administrative user in the LOCKSS system’s Web user interfaces.

18. ``Password for web UI administration user <uiuser> (again):`` Re-enter the password for the given administrative user in the LOCKSS system’s Web user interfaces (if the two passwords do not match, the password will be asked again).

19. ``Password for database:`` Enter the password for the embedded Postgres database included in LOCKSS 2.0-alpha. *Future versions will allow you to use an existing Postgres database and enter credentials accordingly.*

20. ``Password for database (again):`` Re-enter the password for the embedded Postgres database (if the two passwords do not match, the password will be asked again).

21. ``OK to store this configuration:`` confirm with :kbd:`Y` that the summarized configuration data is correct and that you are ready to write it to a file.

If prompted to generate files, accept (or run :file:`scripts/generate-lockss` immediately after).
