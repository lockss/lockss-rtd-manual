===================
Security Advisories
===================

--------------
CVE-2021-44228
--------------

*Last updated: 2021-12-15*

A critical remote code execution vulnerability has been identified in Apache Log4j 2.x, a ubiquitous Java library for recording information to software logs. Tracked as CVE-2021-44228 and also nicknamed "Log4Shell" or "LogJam", this vulnerability led to the discovery of related, albeit milder, vulnerabilities in Log4j 1.x and 2.x, such as CVE-2021-45046 and CVE-2021-4104.

**These vulnerabilities affect the LOCKSS system version 2.0-alpha4, Solr and OpenWayback, and require an upgrade to fix.**

Remediation
===========

1. Log in as the ``lockss`` user and navigate to the :file:`lockss-installer` directory.

2. Stop the LOCKSS system with this command:

   .. code-block:: shell

      scripts/stop-lockss

3. Synchronize the LOCKSS Installer with GitHub with this :command:`git` command:

   .. code-block:: shell

      git fetch --all --tags

4. Move the LOCKSS Installer from the version tagged ``version-2.0-alpha4`` to the version tagged ``version-2.0-alpha4c`` with this :command:`git` command:

   .. code-block:: shell

      git reset --hard version-2.0-alpha4c

5. Start the LOCKSS system back up with this command:

   .. code-block:: shell

      scripts/start-lockss

.. attention::

   If you are using an external Solr database or external OpenWayback replay engine, you are responsible for mitigating the threat in the respective environments.

References
==========

*  https://logging.apache.org/log4j/2.x/security.html

*  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228

*  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046

*  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-4104
