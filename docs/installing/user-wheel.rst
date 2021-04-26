To create the ``lockss`` user and group, run the following command (as ``root`` or with :program:`sudo`):

.. code-block:: shell

   useradd --system --user-group --groups=wheel --create-home --shell=/bin/bash lockss
