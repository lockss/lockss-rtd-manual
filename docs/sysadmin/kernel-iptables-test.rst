You can check if the ``ip_tables`` loadable kernel module is installed by typing:

.. code-block:: shell

   modinfo ip_tables

*  If technical information about the module is output, then the host satisfies the ``ip_tables`` loadable kernel module requirement.

   .. dropdown:: Example
      :animate: fade-in-slide-down

      .. COMMENT relative literalinclude didn't seem to work if this fragment was in an include from elsewhere e.g. /introduction/prerequisites

      .. literalinclude:: /sysadmin/kernel-iptables-modinfo.txt
         :language: text

*  If an error message similar to ``modinfo: ERROR: Module ip_tables not found.`` is output, then the host does not satisfy the ``ip_tables`` loadable kernel module requirement.
