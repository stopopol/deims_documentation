==========================================
Retrieving data
==========================================

DEIMS-SDR offers multiple ways of programmatically extracting information that always reflects the latest version of information in the DEIMS-SDR database.

REST-API
============================================================
DEIMS-SDR has a REST-API (https://deims.org/api) following the Open API 3.0 specification.
It allows to get lists (as .json or .csv) of ressources as well as detailed information about every record.
For perfomance reasons, all jsons returned by the API are NOT pretty printed. The usage of a browser plugin for formatting the results is recommended. 

* https://deims.org/api/sites (returns the list of all sites on DEIMS-SDR as .json)
* https://deims.org/api/datasets (returns the list of all datasets on DEIMS-SDR as .json)
* https://deims.org/api/activities (returns the list of all activities on DEIMS-SDR as .json)
* https://deims.org/api/sensors (returns the list of all sensors on DEIMS-SDR as .json)

adding ?format=csv each list can also be returned as .csv, e.g. https://deims.org/api/sites?format=csv

The site list currently allows very basic filtering by network ids and whether or not sites are verified members.

As an example, the following request returns all verified LTER Japan sites:

* https://deims.org/api/sites?network=6a7c82f8-f472-40ad-ae28-3035e239f3b6&verified=true

These lists always include the title, the unique ID used in DEIMS-SDR, coordinates and change date of a site.
The ID can be used to get the detailed record of a resource. 

The following requests are examples for each record type:

* https://deims.org/api/sites/6dfa31b5-f5d2-4579-b869-c329c2b76af6 (for a site record)
* https://deims.org/api/datasets/5ceeb7a8-db86-444b-aef5-24e81c4f4e2f (for a dataset record)
* https://deims.org/api/activities/c67e88ad-84c1-41d2-ba8c-23619585bb14 (for an activity record)
* https://deims.org/api/sensors/588b4026-ea1f-4357-ad3e-fabdd7de382c (for a sensor record)

These records contain all available information and are only available as .json.

Site records can be queried using the following query parameters:

* https://deims.org/api/sites?network=735946e0-4e9e-484a-acee-85e31f4e2a2e&verified=true // networks
* https://deims.org/api/sites?name=rosalia // site name
* https://deims.org/api/sites?country=at // country

WMS/WFS
============================================================
DEIMS-SDR provide WMS/WFS services for site records.
These services can be used to include site information in web maps or in desktop GIS applications.

* https://deims.org/geoserver/ows?service=wms&version=1.3.0&request=GetCapabilities (WMS 1.3.0 GetCapabilities Link)
* https://deims.org/geoserver/ows?service=wfs&version=2.0.0&request=GetCapabilities (WFS 2.0.0 GetCapabilities Link)

The services also allow to download the information featured in the various layers in a variety of formats, e.g. Shapefile, GeoPackage, GeoJSON, CSV, ...

* https://deims.org/geoserver/deims/ows?service=WFS&version=1.0.0&request=GetFeature&typeName=deims:deims_all_sites&outputFormat=shape-zip (all site records on DEIMS-SDR as Shapefile)
* https://deims.org/geoserver/deims/ows?service=WFS&version=1.0.0&request=GetFeature&typeName=deims:deims_all_sites&outputFormat=kml (all ILTER sites on DEIMS-SDR as KML)

For a complete and up to date list of layers, please refer to the GetCapabilities links.


CSW/OAI-PMH
============================================================
DEIMS-SDR provides site, dataset and activity records as ISO19139 served by OGC-CSW and OAI-PMH.
Please be aware that ISO 19139 records only provide a limited subset of information compared to the full records served by the REST-API.

* https://deims.org/pycsw/csw (CSW GetCapabilities Link)
* https://deims.org/pycsw/csw.py?mode=oaipmh&verb=Identify (OAI-PMH OpenSearch site)

For further information on how to implement these services, please consult official documentation for each service.

Python
============================================================
DEIMS-SDR also has a Python package that eases data access. You can find more information here: https://pypi.org/project/deims/
