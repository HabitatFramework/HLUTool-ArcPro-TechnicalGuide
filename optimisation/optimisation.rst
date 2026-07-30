************
Optimisation
************

The design of the HLU Tool has been optimised as far as possible and there are no known simple technological enhancements that can be made to significantly improve it's performance further.

It is important, therefore, to ensure performance is optimised elsewhere wherever possible through user configuration and operation. The following suggestions show some simple approaches to improving performance.

.. index::
	single: Optimisation; GIS

.. _gis_optimisation:

GIS Optimisation
================

GIS Layers
----------

Attribute indexes
	Certain functions in the HLU Tool will perform attribute searches on the HLU layer, typically using the **INCID** and/or **TOID** fields. It is, therefore, recommended that individual attribute indexes are created on both of these fields.

Spatial Indexes
	It is advisable to create a spatial index on all HLU layers referenced by the tool to improve performance when ArcGIS Pro redraws the layer(s) or when features are selected.


Creating an ArcGIS Pro Project
------------------------------

It is recommended that an ArcGIS Pro project (:file:`.aprx`) is opened when using the HLU Tool. This should be optimised to ensure maximum performance, which should include the following:

* Ensure that the project only contains one copy of the HLU layer (or one copy of each HLU layer if split into separate layers).
* Add display scale ranges to datasets so that detailed datasets such as the HLU layer(s) and aerial photography are not displayed at smaller scales than necessary.

Tips for ArcGIS Pro users
-------------------------

It can take significant time for ArcGIS Pro to draw or query an entire HLU layer, so care should be taken when using certain functions. The following tips may help avoid some long delays:

* 'Zoom to Selection' is useful for identifying the habitat features on the map. However, if scale range limits are not used it may take a significant length of time to display the result depending upon the number of features selected and their geographical distribution.
* 'Seelcted Filtered INCIDs' selects the features for all filtered INCIDs in the dockpane. If a large number of INCIDs are in the filter it may take a long time to select all of the features.
* It is strongly recommended that the HLU layer is stored as a file geodatabase or enterprise geodatabase feature class rather than a shapefile.

.. caution::
	The tool will be significantly slower if HLU layers are stored as shapefiles due to the performance limitations of that file format.

.. raw:: latex

	\newpage

.. index::
	single: Optimisation; Database

.. _database_optimisation:

Database Optimisation
=====================

Database Type
-------------

The HLU Tool ArcGIS Pro edition supports **SQL Server**, **PostgreSQL** and **Oracle** database backends.
Such systems are optimised to handle large data volumes and complex queries, and hence will support optimum performance when querying and updating the attribute data in the database.

.. note::
	Microsoft Access is **no longer** supported as a database backend.

Local vs. Network Storage
-------------------------

It is important to remember that application performance will depend upon the data transfer speed between where the ArcGIS Pro application is running and where the database and HLU layers are stored. Data stored locally on a single computer will provide good performance, but will limit access to the data to a single user. Data stored on a network drive is accessible to all users, but performance will be limited by the speed that the data can be transferred across the network.

Data Management
---------------

Database copies
	Only one copy of the database and the HLU layer should be used to avoid data becoming corrupted. Changes to one copy of the database or layer will not be reflected in any other copy, causing a mismatch between attribute and spatial data.

	.. caution::
		If there is more than one copy of the database, e.g. a live and a test copy, the ``data_version`` attribute in the 'lut_version' table to reflect the contents and use of the database, e.g. 'Live' or 'Test'. The attribute should always be changed whenever a database is copied from a 'Live' environment to a 'Test' environment, or vice versa. See 'lut_version' in :Ref:`configuring_luts` for more information.

Direct updates
	Habitat data must not be edited directly in either the database or the HLU layers. Any modifications made outside the HLU Tool could cause data corruption particularly if unique identifiers are altered. However, if additional entries are required in the lookup tables, these may be added to the database directly. See :ref:`configuring_luts` for more information on configuring the database.
