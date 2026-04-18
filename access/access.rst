****************************
Linking Access to SQL Server
****************************

.. note::
	Microsoft Access is **not** supported as a direct backend database connection in the ArcGIS Pro edition of the HLU Tool. The instructions in this section describe how to link a Microsoft Access database as an **administrative front-end** to a SQL Server database, allowing users familiar with Access to view and edit the HLU Tool lookup tables and data tables without requiring SQL Server Management Studio.

Using SQL Server as the relational database system for the HLU Tool will provide performance, reliability and volume benefits over Microsoft Access.

Many users will be more familiar with Access, so linking Access to SQL Server in this way allows users to view and edit the HLU Tool data without needing authority to use SSMS and without any risk of altering the database structure or settings. Using Access as a front-end to the database in this way also allows users to create and share Access queries, forms and reports specific to their needs.

.. note::
	Database administrators need to ensure that users of the Access database have the necessary permissions to view and edit the data tables on the target SQL Server database.


.. raw:: latex

	\newpage

.. index::
	single: Linking Access to SQL

.. _new_link:

Linking a new Access database
=============================

The process of linking an Access database to a SQL Server database can be complex and necessitates that you know the connection settings for the target database. The following instructions describe how to link to an existing installation of the HLU Tool database running on SQL Server. It should not matter which version (i.e. SQL Server or SQL Server Express) is installed or which release, as long as it is meets the :ref:`requirements`.

.. note::
	It is also possible to link the exporter database to other relational databases, such as PostGIS, but instructions for this are not provided in this guide.

.. sidebar:: Other Access versions

	The steps in this procedure are based on using Microsoft Access 2012. Instructions for different versions of Microsoft Access may vary.

The following instructions describe how to link an Access database to a SQL Server database:

	1. Make sure your SQL Server service is running and the HLU Tool database is attached.

	2. Open the destination Access database in which you wish to create the linked tables.

	3. On the 'External Data' tab, in the 'Import & Link' group, click :guilabel:`ODBC Database` as shown in :ref:`figALED`.

		.. _figALED:

		.. figure:: figures/AccessLinkExternalDataTab.png
			:align: center
			:scale: 90

			External Data tab


	.. raw:: latex

		\newpage

	4. Select :guilabel:`Link to the data source by creating a linked table` (as shown in :ref:`figALODD`) and then click :guilabel:`OK`.

		.. _figALODD:

		.. figure:: figures/AccessLinkODBCDataDialog.png
			:align: center
			:scale: 85

			Get External Data - OBDC Database dialog

	.. raw:: latex

		\newpage

	5. In the 'Select Data Source' dialog box as shown in :ref:`figALSDSD`, if the DSN file you want to use already exists, locate and select the DSN file. If you haven't yet created a DSN file for the target database skip to :ref:`create_dsn` then continue from the next step.

		.. _figALSDSD:

		.. figure:: figures/AccessLinkSelectDataSourceDialog.png
			:align: center
			:scale: 85

			Select Data Source dialog

	.. note::
		If have haven't already created a data source name (DSN) file for the HLU Tool database see :ref:`create_dsn`.

	.. raw:: latex

		\newpage

	6. Click :guilabel:`OK`. Access will display the 'Link Tables' dialog box as shown in :ref:`figALSLTD`.

		.. _figALSLTD:

		.. figure:: figures/AccessLinkSelectTablesDialog.png
			:align: center
			:scale: 85

			Select Link Tables dialog

	7. Under 'Tables', click each table that you want to link to, and then click :guilabel:`OK`.

	.. note::
		Many of the tables in the list are internal SQL Server tables. Do not select these - only select the HLU Tool export, data and lookup tables.

	8. If the 'Select Unique Record Identifier' dialog box appears, Access was unable to determine which field or fields uniquely identify each row of the source data. In this case, select the field or combination of fields that is unique for each row, and then click :guilabel:`OK`. If you are not sure, check with the SQL Server database administrator.

	.. raw:: latex

		\newpage

	9. If the link is successful Access will display the new linked tables in the Objects Navigation Pane as shown in :ref:`figALATD`.

		.. _figALATD:

		.. figure:: figures/AccessLinkObjectsNavigationPane.png
			:align: center
			:scale: 85

			Access Objects Navigation Pane


.. raw:: latex

	\newpage

.. index::
	single: Linking Access to SQL; Creating a DSN

.. _create_dsn:

Creating a new DSN file
=======================

.. sidebar:: Other Access versions

	The steps in this procedure are based on using Microsoft Access 2012. Instructions for different versions of Microsoft Access may vary.

The following instructions describe how to create a new .dsn file for the HLU Tool database:

	1. Click :guilabel:`New` to create a new data source name (DSN) file. The 'Create New Data Source' wizard will start.

	2. Select **SQL Server** in the list of drivers (as shown in :ref:`figALSDD`) and then click :guilabel:`Next`. If you are connecting to a different database then select the relevant driver.

		.. _figALSDD:

		.. figure:: figures/AccessLinkSelectDriverDialog.png
			:align: center
			:scale: 85

			Create New Data Source - Select Driver dialog

	.. raw:: latex

		\newpage

	3. If you wish to enter the 'Server Name' and 'Database Name' at this stage click on :guilabel:`Advanced...` and enter them under the DRIVER keyword (see :ref:`figALADD` for example). Then click :guilabel:`OK` to return to the 'Create New Data Source' wizard.
	
		.. _figALADD:

		.. figure:: figures/AccessLinkAdvancedDSNDialog.png
			:align: center
			:scale: 90

			Create New Data Source - Advanced DSN dialog

		.. note::
			If you don't enter the 'Server Name' and 'Database Name' here you will be prompted for them later.

	4. Click :guilabel:`Next` and then choose a suitable file path and file name for your new DSN. Then click :guilabel:`Save`.

	.. raw:: latex

		\newpage

	5. The file path and file name of the select DSN will be displayed (see :ref:`figALSDSND` for example). Click :guilabel:`Next`.

		.. _figALSDSND:

		.. figure:: figures/AccessLinkSelectDSNDialog.png
			:align: center
			:scale: 80

			Select Data Source dialog

	6. A summary of the DSN settings will be shown (see :ref:`figALOSSD` for example). Click :guilabel:`Finish`.

		.. _figALOSSD:

		.. figure:: figures/AccessLinkSummaryODBCDialog.png
			:align: center
			:scale: 80

			ODBC Setup Summary dialog

	.. raw:: latex

		\newpage

	7. If you didn't enter the server and database names earlier you will be prompted for them now. Enter a description for the data source and then from the list choose which server you want to connect to (see :ref:`figALSSD` for example). Then click :guilabel:`Next`.

		.. _figALSSD:

		.. figure:: figures/AccessLinkSelectServerDialog.png
			:align: center
			:scale: 85

			Create New Data Source - Select Server dialog

		.. tip::
			If the server doesn't appear in the list then manually type the server name it into the Server field

	.. raw:: latex

		\newpage

	8.	Choose either **Windows NT authentication** or **SQL Server authentication**, as shown in see :ref:`figALAD`, depending on how the security settings have been defined in the SQL Server database then click :guilabel:`Next`. If you are not sure, check with the SQL Server database administrator.

		.. _figALAD:

		.. figure:: figures/AccessLinkSQLAuthenticationDialog.png
			:align: center
			:scale: 85

			Create New Data Source - Authentication dialog

	9.	Select the 'Change the default database to' checkbox and then from the list select which database to connect to (see :ref:`figALSDBD` for example). Then click :guilabel:`Next`.

		.. _figALSDBD:

		.. figure:: figures/AccessLinkSelectDatabaseDialog.png
			:align: center
			:scale: 85

			Create New Data Source - Select Database dialog

	10.	Leave all the settings as the default values and click :guilabel:`Finish`.

	.. raw:: latex

		\newpage

	11.	A summary of the ODBC Setup will be displayed (see :ref:`figALSD` for example). Click :guilabel:`Test Data Source ...` to ensure the settings are correct and the connection works and then click :guilabel:`OK` to close the test window.

		.. _figALSD:

		.. figure:: figures/AccessLinkSummaryDialog.png
			:align: center
			:scale: 85

			Create New Data Source - Summary dialog

	12.	Click :guilabel:`OK` to save the DSN. You will then be returned to the 'Select Data Source' window to continue linking a new database (see :ref:`new_link`).
 

.. note::
	Once you have defined a DSN for your HLU Tool database you won't need to repeat steps 6 to 14 if you need to link another Access database in future.


.. raw:: latex

	\newpage

.. index::
	single: Linking Access to SQL; Updating Linked Tables

.. _update_link:

Updating a linked table
=======================

Each time you open a linked table you will see the latest data displayed in it. However, structural changes made to a SQL Server table are not automatically reflected in a linked table. In this case you will need to update the linked table by applying the latest SQL Server object structure.

.. sidebar:: Other Access versions

	The steps in this procedure are based on using Microsoft Access 2012. Instructions for different versions of Microsoft Access may vary.

The following instructions describe how to update the links from an Access database to a SQL Server database:

	1. Make sure your SQL Server service is running and the HLU Tool database is attached.

	2. Open the destination Access database in which you wish to create the linked tables.

	3. On the 'Database Tools' menu click :guilabel:`Linked Table Manager` as shown in :ref:`figARED`.

		.. _figARED:

		.. figure:: figures/AccessRelinkExternalDataTab.png
			:align: center
			:scale: 90

			External Data tab

	4. The 'Linked Table Manager' dialog will appear as shown in :ref:`figARTMD`.

		.. _figARTMD:

		.. figure:: figures/AccessRelinkTableManagerDialog.png
			:align: center
			:scale: 90

			Linked Table Manager dialog

	.. raw:: latex

		\newpage

	5. Select the :guilabel:`Always prompt for new location` check box.

	6. Click the tables that you wish to update or click the :guilabel:`Select All` button (see :ref:`figARTMSD` for example) and then click :guilabel:`OK`.

		.. _figARTMSD:

		.. figure:: figures/AccessRelinkTableManagerSelectedDialog.png
			:align: center
			:scale: 90

			Linked Table Manager selected tables

	7. If the update if successful Access will display a message to that effect as shown in :ref:`figARSD`. Otherwise Access will display an error message.

		.. _figARSD:

		.. figure:: figures/AccessRelinkSuccessDialog.png
			:align: center

			Linked Table Manager Success dialog

	8. Click :guilabel:`OK` to close the Linked Table Manager.

