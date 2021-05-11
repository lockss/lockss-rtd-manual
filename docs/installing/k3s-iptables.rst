.. rubric:: Adjusting :program:`iptables`

If :program:`iptables` (a network packet filter) is present in this operating system, it may need to be adjusted for K3s to work properly. An adjustment is needed if :program:`iptables` version 1.8.0 or later is running in ``nf_tables`` mode via the :program:`alternatives` mechanism.

1. Check if :program:`iptables` is installed, at what version and in what mode, by running this command as ``root`` [#fnroot]_ :

   .. code-block:: shell

      iptables --version

   If :program:`iptables` does not exist, you will see an error message like ``bash: iptables: command not found`` and no further action is needed; otherwise, :program:`iptables` is present on your system.

2. If :program:`iptables` is present on your system, note the version number and mode (``legacy`` or ``nf_tables``) in the line of output, for example:

   .. code-block:: text

      iptables v1.8.7 (nf_tables)

   Here the version is ``1.8.7`` and the mode is ``nf_tables``.

3. If :program:`iptables` is version 1.8.0 or later and the mode is ``nf_tables``, run the following command as ``root`` [#fnroot]_ :

   .. code-block:: shell

      readlink /etc/alternatives/iptables*

4. If the :program:`readlink` command returns file paths as output, and the files have ``nft`` in the name, for instance:

   .. code-block:: text

      /usr/sbin/ip6tables-nft
      /usr/sbin/ip6tables-nft-restore
      /usr/sbin/ip6tables-nft-save

   then switch :program:`iptables` from ``nf_tables`` to ``legacy`` mode via the :program:`alternatives` mechanism, by running these commands as ``root`` [#fnroot]_ :

   .. code-block:: shell

      update-alternatives --set iptables /usr/sbin/iptables-legacy

      update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy

      iptables --flush
