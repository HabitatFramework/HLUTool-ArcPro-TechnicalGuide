************
Optimisation
************

The design of the HLU Tool has been optimised as far as possible and there are no known simple technological enhancements that can be made to significantly improve performance.

It is important therefore to ensure performance is optimised elsewhere wherever possible through user configuration and operation. The following suggestions show some simple approaches to improving performance.

.. index::
	single: Optimisation; GIS

.. _gis_optimisation:

GIS Optimisation
================

GIS Layer Indexing
------------------

Attribute indexes
	Certain functions in the HLU Tool will perform attribute searches on the HLU layer, typically using the **INCID** and/or **TOID** fields. It is, therefore, recommended that individual attribute indexes are created on both of these fields.

Spatial Indexes
	If users frequently zoom in and out whilst the HLU layer is visible when reviewing or editing using the HLU Tool, it may be advisable to create one or more spatial indexes on the HLU layer to improve performance when ArcGIS Pro draws the layer. The choice of scales will depend upon the number, size and density of the features and the preferred working practices of the users.


Creating an ArcGIS Pro Project
------------------------------

An ArcGIS Pro project (:file:`.aprx`) must be prepared for use with the HLU Tool. This should be optimised to ensure maximum performance, which should include the following:

	* Ensure that the project only contains one copy of the HLU layer (or one copy of each HLU layer if split into separate layers).
	* Save the project at a sensible zoom level such as 1:10,000 scale rather than the full extent of the HLU dataset, to save time when opening.
	* Add display scale ranges to datasets so that detailed datasets such as the HLU layer and aerial photography are not displayed at smaller scales than necessary. Recommended scale ranges are shown in the table below:

	.. tabularcolumns:: |L|C|C|

	.. table:: Recommended maximum display scale ranges

		+------------------------------------+-----------+--------------------+
		|          GIS Application           | HLU layer | Aerial Photography |
		+====================================+===========+====================+
		| ArcGIS Pro (Do not display beyond) | 1:24,000  | 1:10,000           |
		+------------------------------------+-----------+--------------------+


Tips for ArcGIS Pro users
-------------------------

It takes a significant length of time for ArcGIS Pro to draw or query an entire HLU layer, therefore care should be taken when using certain functions. The following tips may help avoid some performance issues:

	* 'Zoom to Selection' is useful for identifying the habitat features on the map, however if scale range limits are not used it may take a significant length of time to display the result depending upon the number of features selected and their geographical distribution.
	* 'Filter by Attributes' performs complex queries and selects the results in the map. If a large number of results are returned, it could take a long time to select the spatial features.
	* If the HLU layer is taking a long time to draw, use the **Cancel Drawing** button (the stop icon in the bottom-left corner of the map view) to interrupt the draw.
	* We strongly recommend that the HLU layer is stored as a file geodatabase or enterprise geodatabase feature class rather than a shapefile.

	.. caution::
		The tool will be significantly slower if the HLU layer is stored as a shapefile due to the limitations of the file format.


.. raw:: latex

	\newpage

.. index::
	single: Optimisation; Database

.. _database_optimisation:

Database Optimisation
=====================

Database Type
-------------

The HLU Tool ArcGIS Pro edition supports **SQL Server**, **PostgreSQL** and **Oracle** database backends. Microsoft Access is not supported.

Database management systems such as SQL Server, PostgreSQL and Oracle are optimised to handle large data volumes and complex queries, and can be significantly faster than a desktop database. It is therefore recommended that the HLU Tool is used with SQL Server or a similar enterprise-grade database management system as this will improve performance when filtering database records and updating attribute data.


Local vs. Network Storage
-------------------------

It is important to remember that application performance will depend upon the data transfer speed. Data stored locally on a single computer will provide good performance, but will limit access to the data to a single user. Data stored on a network drive is accessible to all users, but performance will be limited by the speed that the data can be transferred across the network.


Data Management
---------------

Only one copy of the database and the HLU layer should be used to avoid data becoming corrupted. Changes to one copy of the database or layer will not be reflected in any other copy, causing a mismatch between attribute and spatial data.

Habitat data must not be edited directly in either the database or the HLU layer. Any modifications made outside the HLU Tool could cause data corruption particularly if unique identifiers are altered.

However, if additional entries are required in the lookup tables, these may be added to the database directly. It is essential that the structure of these tables is not altered and we recommend that any updates to the data in these tables are carried out solely by the database administrator.


.. raw:: latex

	\newpage

