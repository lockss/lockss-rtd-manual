========
Glossary
========

.. glossary::
   :sorted:

   container
      A software container, or simply a container, is a lightweight, narrow-purpose bundle of software code, its dependencies, and its environment, forming a virtual unit of software that can be run on a variety of host environments by a :term:`container orchestration system`.

      The LOCKSS system uses :term:`Docker` containers.

   container orchestration system
      A container orchestration system is a software automation tool that configures, deploys and manages :term:`containers <container>` on a host system, providing them with a runtime environment and resources like storage and networking, and assembling them like building blocks into cohesive software applications called :term:`stacks <stack>` [#fn-stack]_.

      The LOCKSS system uses :term:`Kubernetes` as its container orchestration system.

   content storage
      .. include:: content-storage.rst

      Content storage is one of three kinds of storage needed by the LOCKSS stack, together with :term:`system storage` and :term:`operating storage`.

      Adding, removing, or reordering the content storage areas requires a reindexing step.

   content storage area
      A content storage area is an individual directory of :term:`content storage`, as content storage can consist of one or multiple areas.

   Curl
      `Curl <https://curl.se/>`_, also styled **cURL**, is an open source software package for downloading and uploading files.

      Curl is developed by a project community centered around its creator Daniel Stenberg.

   Docker
      `Docker <https://docs.docker.com/>`_ is a software development platform for :term:`containers <container>`.

      The LOCKSS stack uses Docker containers downloaded from :term:`Docker Hub`.

      Docker (the software) is developed by `Docker <https://www.docker.com/>`_ (the company).

   Docker Hub
      `Docker Hub <https://hub.docker.com/>`_ is a :term:`container` distribution service, from which containers involved in the :term:`LOCKSS stack` are downloaded.

      Docker Hub is operated by `Docker <https://www.docker.com/>`_.

   firewall
      A firewall is a computer security system that monitors and controls network traffic.

   firewalld
      `Firewalld <https://firewalld.org/>`_ is an open source :term:`firewall` management tool for Linux.

      Firewalld interacts with the Linux kernel's :term:`netfilter` framework via :term:`nftables`.

   Git
      `Git <https://git-scm.com/>`_ is an open source distributed version control system.

      Software development related to LOCKSS is done in Git at :term:`GitHub`.

   GitHub
      `GitHub <https://github.com/>`_ is a software development platform.

      Software development related to LOCKSS is done in :term:`Git` at GitHub.

      GitHub (the platform) is operated by `GitHub <https://github.com/about>`_ (the company), a subsidiary of `Microsoft <https://www.microsoft.com/>`_.

   install-lockss
      .. include:: install-lockss.rst

   iptables
      `iptables <https://netfilter.org/projects/iptables>`_ is an open source software package that implements :term:`firewall` rules using the Linux kernel's :term:`netfilter` packet filtering system.

      Although still widely in use, iptables has been succeeded by :term:`nftables`.

      Iptables is developed by the `Netfilter <https://www.netfilter.org/>`_ project.

   K3s
      `K3s <https://k3s.io/>`_ is a lightweight, open source :term:`Kubernetes` distribution.

      Important prerequisites for running LOCKSS apply to the :term:`K3s data directory`.

      K3s is developed by `Rancher <https://www.rancher.com/>`_, a subsidiary of `SUSE <https://www.suse.com/>`_.

   K3s data directory
      :term:`K3s` downloads :term:`containers <container>` and stores configuration and other data into a directory known as the **K3s data directory**.

      The K3s data directory is the most sizeable part of the :term:`system storage` needs of the LOCKSS system.

      Important prerequisites for running LOCKSS apply to the :term:`K3s data directory`, as outlined in :numref:`System Storage Prerequisites` (:ref:`System Storage Prerequisites`): :ref:`prerequisites-k3s-nfs`, :ref:`prerequisites-k3s-xfs`.

   Kubernetes
      `Kubernetes <https://kubernetes.io/>`_ (pronounced *coo-burn-NET-ease*) is an open source :term:`container orchestration system`.

      The LOCKSS system uses the :term:`K3s` Kubernetes distribution.

      Kubernetes development is governed by the `Cloud Native Computing Foundation <https://www.cncf.io/>`_, a project of the `Linux Foundation <https://www.linuxfoundation.org/>`_.

   LCAP
      .. include:: lcap.rst

      LCAP is named after `El Capitán <https://en.wikipedia.org/wiki/El_Capitan>`_. Before being called *LOCKSS Content Audit Protocol*, LCAP was called *Library Content Audit Protocol*.

   LOCKSS
      LOCKSS can refer to:

      *  The LOCKSS software. LOCKSS is an open source distributed digital preservation system. See :term:`LOCKSS system`.

      *  The LOCKSS program. LOCKSS is a program of Stanford University Libraries that develops the LOCKSS software and provides digital preservation services. See :term:`LOCKSS program`.

      *  The LOCKSS methodology. LOCKSS, short for "Lots Of Copies Keep Stuff Safe", is a digital preservation methodology.

   LOCKSS Configuration Service
      .. include:: lockss-configuration-service.rst

   LOCKSS Crawler Service
      .. include:: lockss-crawler-service.rst

   LOCKSS Downloader
      The `LOCKSS Downloader <https://github.com/lockss/lockss-downloader>`_ is a convience script to perform a one-time download of a software project from :term:`GitHub`, using :term:`Curl` or :term:`Wget` rather than :term:`Git`.

      By default, the LOCKSS Downloader downloads the :term:`LOCKSS Installer`.

   LOCKSS Installer
      The `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ is a collection of scripts to install, configure and run the :term:`LOCKSS stack` on a host system.

   LOCKSS Installer Directory
      .. include:: lockss-installer-directory.rst

   LOCKSS Metadata Service
      .. include:: lockss-metadata-service.rst

   LOCKSS network
      A LOCKSS network is a peer-to-peer network of nodes running the :term:`LOCKSS  system`'s :term:`LCAP` audit and repair protocol to preserve data together.

   LOCKSS Poller Service
      .. include:: lockss-poller-service.rst

   LOCKSS program
      LOCKSS is a program of `Stanford University Libraries <https://library.stanford.edu/>`_, that develops the :term:`LOCKSS system` and provides digital preservation services.

   LOCKSS Repository Service
      .. include:: lockss-repository-service.rst

   LOCKSS SOAP Compatibility Service
      .. include:: lockss-soap-compatibility-service.rst

   LOCKSS stack
      The LOCKSS stack is the :term:`stack` of :term:`containers <container>` providing the functionality of the LOCKSS system as a whole.

   LOCKSS system
      .. include:: lockss-system.rst

   log storage area
      The :term:`LOCKSS stack`'s log storage area is devoted to log files generated by the :ref:`Stack Components`. The log storage area is one of the three areas of :term:`operating storage`, together with the :term:`state data storage area` and the :term:`temporary storage area`.

   netfilter
      ``netfilter`` is a Linux kernel module that provides a packet filtering framework, relied on by many :term:`firewall` software applications.

   nftables
      `nftables <https://netfilter.org/projects/nftables>`_ is an open source software package that implements :term:`firewall` rules using the Linux kernel's :term:`netfilter` packet filtering system.

      Nftables is the successor for :term:`iptables`, although the latter is still widely in use.

      Nftables is developed by the `Netfilter <https://www.netfilter.org/>`_ project.

   operating storage
      .. include:: operating-storage.rst

      Operating storage is one of three kinds of storage needed by the LOCKSS stack, together with :term:`system storage` and :term:`content storage`.

      Operating storage consists of the :term:`state data storage area`, the :term:`log storage area`, and the :term:`temporary storage area`. All three can be set to the same actual directory.

   stack
      A **container stack**, or simply a stack [#fn-stack]_, is a cohesive software application made up of a suite of :term:`containers <container>` managed by a :term:`container orchestration system`.

      In particular, the suite of containers providing the functionality of the LOCKSS system as a whole is referred to as the :term:`LOCKSS stack`.

   state data storage area
      The :term:`LOCKSS stack`'s state data storage area is devoted to database files, state files, and similar persistent data needed as part of normal operation. The state data storage area is one of the three areas of :term:`operating storage`, together with the :term:`log storage area` and the :term:`temporary storage area`.

   system storage
      .. include:: system-storage.rst

      System storage is one of three kinds of storage needed by the LOCKSS stack, together with :term:`operating storage` and :term:`content storage`.

      The most sizeable part of the system storage needs of the LOCKSS system is the :term:`K3s data directory`, which has its own particular requirements.

   temporary storage area
      The :term:`LOCKSS stack`'s **temporary storage area** is devoted to temporary files, staging areas for unpacking compressed files or off-heap data processing, etc. The temporary storage area is one of the three areas of :term:`operating storage`, together with the :term:`state data storage area` and the :term:`log storage area`.

   ufw
      `Ufw <https://launchpad.net/ufw>`_, also styled **UFW**, short for **Uncomplicated Firewall**, is an open source :term:`firewall` management tool for Linux.

      Ufw interacts with the Linux kernel's :term:`netfilter` framework via :term:`iptables`.

      Ufw is developed by `Canonical <https://canonical.com/>`_.

   Wget
      `Wget <https://www.gnu.org/software/wget/>`_, or Wget for short, is an open source software package for downloading and uploading files.

      Wget is developed by the `GNU <https://www.gnu.org/>`_ project.

----

.. rubric:: Footnotes


.. [#fn-lcap]

   Formely Library Audit Content Protocol.

.. [#fn-stack]

   There is no widespread term for a containerized application; "stack" is common in the LOCKSS ecosystem.
