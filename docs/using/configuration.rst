======================================
Using the LOCKSS Configuration Service
======================================

.. note::

   This page is under construction.

--------------------------------
Accessing the Web User Interface
--------------------------------

If you are already connected to the Web user interface (UI) of another component of the LOCKSS System, click :guilabel:`Config Service` in the top-left menu.

Alternatively, if your primary hostname is :samp:`{<HOST>}`, you can use your browser to connect to the LOCKSS Configuration Service Web user interface (UI) at :samp:`http://{<HOST>}:24621`.

Enter your Web UI username and password to login if prompted.

---------------------
Adding Archival Units
---------------------

To add AUs to the system for preservation:

1. In the top-right menu, click :guilabel:`Journal Configuration`.
2. In the center menu, click :guilabel:`Add AUs`.
3. Select one or more collections of AUs by selecting the checkbox next to the appropriate collection.
4. Click the :guilabel:`Select AUs` button. It may take a bit of time (60+ seconds) for the next screen to appear, while the list of AUs is built.
5. Select one or more AUs from the AU list. You may click :guilabel:`Select All` if you would like to select all AUs. If you choose to use select all AUs, please note that the next step may take some time to load.
6. Click the :guilabel:`Add Selected AUs` button. The time it takes for the page to refresh depends on the number of AUs added. Give the LOCKSS system some time to load the AUs and reload the page before moving on.
7. A screen will show a list of added AUs. Crawling of these new AUs will start automatically -- no further action is necessary unless prompted by a footnote next to an AU's name.

-------------------------
Configuring a Crawl Proxy
-------------------------

If Web crawls must be routed through a Web proxy:

1. In the top-right menu, click :guilabel:`Content Access Options`.
2. In the center menu, click :guilabel:`Proxy Client Options`.
3. Select the :guilabel:`Proxy crawls` checkbox.
4. Enter the hostname and port of the Web proxy in the :guilabel:`HTTP Proxy host` and :guilabel:`Port` text areas, respectively.
5. Click the :guilabel:`Update Proxy Client` button.

------------------------------------------
Managing Access to the Web User Interfaces
------------------------------------------

*This section is under construction.*
