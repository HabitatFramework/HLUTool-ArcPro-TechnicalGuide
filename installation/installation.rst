************
Installation
************

.. index::
	single: System Requirements

.. _requirements:

System Requirements
===================

Hardware
--------

.. sidebar:: System Requirements

	Hard disk space requirements are given as a guideline. The actual amount of disk space required will depend upon the size of the GIS layers and database files. In addition to these files space is required for temporary files during processing.

**Minimum specification:**

	* 3 GHz processor
	* 8 GB RAM
	* 1 GB available hard disk space

**Recommended specification:**

	* 3 GHz Dual Core PC or better
	* 16 GB RAM
	* 5 GB available hard disk space

.. Tip::
	For increased performance a multiple core PC with as much RAM as possible is recommended.

Software
--------

**Required software:**

	* ArcGIS Pro 3.4 or later (version 3.x only)
	* Microsoft .NET 8 runtime or later

**Supported databases (one required):**

	* Microsoft SQL Server 2012 or later
	* PostgreSQL 12 or later
	* Oracle DB 12c R2 or later

.. note::
	Microsoft Access is **not** supported as a backend database by this edition of the HLU Tool. For Access-backed installations please use the `ArcGIS Desktop / MapInfo edition <https://github.com/HabitatFramework/HLUTool/releases>`_.

.. _latest_release:

Latest Release
==============

The latest release of the add-in can be downloaded from `GitHub <https://github.com/HabitatFramework/HLUTool-ArcPro/releases>`_. A single :file:`.esriAddinX` file is provided — one version supports all compatible ArcGIS Pro installations.

.. raw:: latex

	\newpage

.. index::
	single: Installation

.. _installing:

Installing the HLU Tool
=======================

The HLU Tool is distributed as an ArcGIS Pro add-in (:file:`.esriAddinX` file). No traditional installer is required.

To install the add-in:

	1. Download the latest :file:`HLUTool.esriAddinX` file from the `GitHub releases page <https://github.com/HabitatFramework/HLUTool-ArcPro/releases>`_.
	2. Close ArcGIS Pro if it is running.
	3. Double-click the :file:`.esriAddinX` file. ArcGIS Pro will open the **Esri ArcGIS Add-In Installation Utility** and prompt you to confirm the installation.
	4. Click :guilabel:`Install Add-In`. The add-in will be installed into your user profile add-ins folder.
	5. Open ArcGIS Pro. A new **HLU Tool** tab will appear on the ribbon.

.. tip::
	The add-in can also be installed manually by copying the :file:`.esriAddinX` file into the ArcGIS Pro user add-ins folder, typically located at :file:`C:\\Users\\<username>\\Documents\\ArcGIS\\AddIns\\ArcGISPro`.

.. note::
	The add-in must be installed for each Windows user account that will use it. Installing for one user will not make the add-in available to other users on the same machine.

.. _uninstalling:

Uninstalling the HLU Tool
=========================

To remove the add-in:

	1. Open ArcGIS Pro and go to **Project > Add-In Manager**.
	2. Select the **HLU Tool** add-in from the list.
	3. Click :guilabel:`Delete This Add-In` and confirm when prompted.
	4. Restart ArcGIS Pro.
