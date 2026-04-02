.. tip::

   Only version 8 of this operating system is expected to require an upgrade to Linux kernel version 5.4 or later. Versions 9 and 10 of this operating system are expected to ship with newer Linux kernel versions out of the box. Confirm from above that the kernel upgrade is required before proceeding.

:Section last updated: 2026-04-02

If an upgrade to Linux kernel 5.4 or later is required for your version of this operating system, you will need to install the `Unbreakable Enterprise Kernel Release 6 Update 3 <https://docs.oracle.com/en/operating-systems/uek/6/relnotes6.3/index.html>`_ (UEK R6U3) from the `Unbreakable Linux Network <https://linux.oracle.com/>`_ (ULN). Follow these steps:

1. In your `ULN <https://linux.oracle.com/>`_ account, select your host, then select :menuselection:`System Details --> Manage Subscriptions`, then subscribe to the ``ol8_x86_64_baseos_latest`` and ``ol8_x86_64_UEKR6`` channels.

   Reference: "Subscribing to ULN Channels" at https://docs.oracle.com/en/operating-systems/uek/6/relnotes6.3/uek6-InstallationandAvailability.html#ol_sub_uln

2. At the host's console, run the following :program:`dnf` command (as ``root``):

   .. code-block:: shell

      dnf config-manager --enable ol8_baseos_latest ol8_addons ol8_UEKR6                  

   to enable the ``ol8_baseos_latest``, ``ol8_addons``, and ``ol8_UEKR6`` repositories.

   Reference: "Enabling Access to Oracle Linux Yum Server Repositories" at https://docs.oracle.com/en/operating-systems/uek/6/relnotes6.3/uek6-InstallationandAvailability.html#ol_sub_pubyum

3. Then update your system with this :program:`dnf` command (as ``root``):

   .. code-block:: shell

      dnf update

   Reference: "Upgrading Your System" at https://docs.oracle.com/en/operating-systems/uek/6/relnotes6.3/uek6-InstallationandAvailability.html#ol_upgradea_sys

4. Reboot the host.
