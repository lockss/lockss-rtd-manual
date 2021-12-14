===================
Security Advisories
===================

--------------
CVE-2021-44228
--------------

*Last updated: 2021-12-13*

A critical remote code execution vulnerability has been identified in Apache Log4j 2.x, a ubiquitous Java library for recording information to software logs. Tracked as CVE-2021-44228 and also nicknamed "Log4Shell" or "LogJam", **this vulnerability affects the LOCKSS system version 2.0-alpha4, Solr and OpenWayback, and requires an upgrade to fix.**

Remediation
===========

1. Log in as the ``lockss`` user and navigate to the :file:`lockss-installer` directory.

2. Stop the LOCKSS system with this command:

   .. code-block:: shell

      scripts/stop-lockss

3. Synchronize the LOCKSS Installer with GitHub with this :command:`git` command:

   .. code-block:: shell

      git fetch --all --tags

4. Move the LOCKSS Installer from the version tagged ``version-2.0-alpha4`` to the version tagged ``version-2.0-alpha4b`` with this :command:`git` command:

   .. code-block:: shell

      git reset --hard version-2.0-alpha4b

5. Start the LOCKSS system back up with this command:

   .. code-block:: shell

      scripts/start-lockss

Scope
=====

*  The five component services of the LOCKSS system as run in the original 2.0-alpha4 release are affected: repository service, configuration service, poller service, metadata extraction service (if configured), metadata service (if configured).

*  The provided Solr and OpenWayback containers as run in the original 2.0-alpha4 release are affected.

*  If you are using an external Solr database or external OpenWayback replay engine, you are responsible for mitigating the threat in the respective environments. You can upgrade Solr to 8.11.1 or use the ``log4j2.formatMsgNoLookups``/``LOG4J_FORMAT_MSG_NO_LOOKUPS`` mitigation; see https://solr.apache.org/security.html#apache-solr-affected-by-apache-log4j-cve-2021-44228. OpenWayback 2.4.0 may not offer an upgradeable version promptly; use the ``log4j2.formatMsgNoLookups``/``LOG4J_FORMAT_MSG_NO_LOOKUPS`` mitigation.

*  Version 2.0-alpha5 of the LOCKSS system will use Log4j 2.16.0 which is not vulnerable, and will run the provided Solr and OpenWayback containers in a non-vulnerable manner.

References
==========

*  https://logging.apache.org/log4j/2.x/security.html

*  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228
