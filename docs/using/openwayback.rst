======================================
Replaying Web Content with OpenWayback
======================================

----------------------------------------
Accessing the OpenWayback User Interface
----------------------------------------

Given that your primary hostname is samp:`{<HOST>}`, you can use your browser to connect to the Pywb user interface (UI) at :samp:`http://{<HOST>}:8080/wayback`.

---------------
Replaying a URL
---------------

To view a URL from OpenWayback:

1.  Enter the URL you want to replay in the URL search box.

2.  Click the :guilabel:`Search` button.

3.	Select the :guilabel:`Year* or leave as :guilabel:`All`

4.  Click :guilabel:`Take Me Back`.

----------------------------------
Finding a URL From an AU to Replay
----------------------------------

There are multiple ways to discover URLs belonging to an AU in the Configuration Service UI:

1. Obtaining a URL by clicking on "pages fetched" inside of crawl status

   *  In the top-right menu, click :guilabel:`Daemon Status`.

   *  Open the control in the middle of the screen that says *Overview* and select :guilabel:`Crawl Status` from the drop down menu.

   *  Picking an AU from the active crawls, click on the number associated with :guilabel:`Pages Fetched` to bring up a list of URLs that have been crawled.

   *  Copy one of the URLs and paste it in the OpenWayback interface as described previously.

2. Obtaining a Substance URL

   *  In the top-right menu, click :guilabel:`Daemon Status`.

   *  Open the control in the middle of the screen that says :guilabel:`Overview` and select :guilabel:`Archival Units` from the drop down menu.  If prompted, enter your Username and Password again.  It will take a bit of time for the next screen to appear while the AU list is being built.

   *  Select an AU by clicking on the AU title in the first column.

   *  Open the :guilabel:`Substance URLs` link

   *  Copy one of the URLs and paste it in the OpenWayback interface as described previously.
