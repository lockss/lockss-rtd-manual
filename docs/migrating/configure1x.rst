===============================================
Configuring the LOCKSS 1.x System for Migration
===============================================
----------------
Before you begin
----------------
* You will need to have a running instance of the LOCKSS 2.x system,
which you have configured for migration. see :doc:`/migrating/configure2x`

* You will need to know the hostname of the LOCKSS 2.x system,
  if it is running on a different host from LOCKSS 1.x.

* You will need to know the LOCKSS 2.x UI username and password supplied when configuring LOCKSS 2.x system.

* You will need to know the LOCKSS 2.x database username and password supplied when configuring the LOCKSS 2.x system.

------------------
Migration Settings
------------------

Click `Migration Settings` link on the LOCKSS 1.x navigation sidepanel.

Migration Settings Form
-------------------------
mig1.png

Complete the top section of the dialog and enter the LOCKSS 2.x values gathered earlier.

1. :guilabel:`Target Hostname`
  The default value `localhost` should remain unchanged for a same host migration otherwise type the LOCKSS 2.x hostname
2. :guilabel:`Target Configuration Service Port`
  The default port `24621` should remain unchanged.
3. :guilabel:`Username`
  Enter the UI username used by the LOCKSS 2.x system.
4. :guilabel:`Password`
  Enter the UI password used by the LOCKSS 2.x system

Click  `Load Configuration` button

mig2.png

The Metadata Database Configuration will be displayed with the values obtained by querying the LOCKSS 2.x system.

1. :guilable:`Database Password`
  Enter the database password used by the LOCKSS 2.x system.

Migration Options
-----------------

* Perform dry run migration

  Select if you want to test migration without ??? from LOCKSS 1.x to LOCKSS 2.x.

* Delete AUs after migration

  If you are performing a same host migration and there is not enought storage
  space for two copies of the content, then check this box so that the LOCKSS 1.x
  content will be deleted as it is migrated to LOCKSS 2.x.

   .. caution::
 This will permanently remove content from your LOCKSS 1.x cache, it should only be done if you need to reclaim the space as it is running.

Click on `Next` button to navigate to the Migration Control Screen.

------------------------
Migration Control Screen
------------------------
mig3.png

:guilabel:`Select Plugins` pulldown.

To migrate all content select :guilabel:`All plugins`. If you wish to migrate a subset of the content,
you may select a plugin to migrate just that plugins AUs.

mig4.png

* :guilabel:`Copy Content`

  Copy the selected plugin's AUs from LOCKSS 1.x to LOCKSS 2.x

* :guilabel:`Copy and Verify Content`

  Copy the selected plugin's AUs from LOCKSS 1.x to LOCKSS 2.x and verify that AUs' metadata matches.

* :guilabel:`Verify Content`

  Do not copy any AUs but verify that the already copied AUs' metadata matches.

* :guilabel:`Full content compare`

  Cause the verify to perform byte for byte comparison of content.

* :guilabel:`Skip already-copied AUS`

  Do not copy AUS which have already been copied.

:guilable:`Start Migration` button

  Click on the start migration button to begin migrating content from LOCKSS 1.x to LOCKSS 2.x

:guilable:`Abort` button

  Click on abort button to stop the migration in progress. If you click start again it will resume from the where it stopped.

During Migration
----------------
There may be no apparent progress for a while, don't worry.

The migration control screen will display
1. Current activity
2  The next few Aus that will start migrating
3. The list of the AUs that have finished migrating
4. The list of errors.

mig6.png
