---
title: Types of Geospatial Information
summary: This tutorial is designed to introduce you different types of geospatial information that are usually used in GIS and can be found from geospatial data portals such as the BTAA Geoportal.
authors:
    - Nicole Kong
date: 2021-05-19

hide:
 - navigation
---

# Types of Geospatial Information

## Contents
- [Introduction](#introduction)
- [Geospatial Information Types](#geospatial-information-types)
  - [Vector Data](#vector-data)
  - [Raster Data](#raster-data)
  - [Vector vs. Raster](#vector-vs-raster)
  - [Tabular Data](#tabular-data)
  - [Scanned Maps](#scanned-maps)
  - [Web Services - GIS](#web-services-gis)
- [How to Find These Data in the BTAA Geoportal](#how-to-find-these-data-in-the-btaa-geoportal)
  - [Search by Resource Class](#search-by-resource-class)
- [Related Resources](#related-resources)
- [Exercise](#exercise)
- [Wrapping Up](#wrapping-up)

## Introduction

* There are many types of data that can be brought into GIS.

* The “type” introduced in this tutorial refers to the different data models that can usually be discovered from a geodata portal or other data portal sites. Or, the data models that GIS professionals usually use to collect and share information.

* It doesn’t refer to the topic, content, or the purpose of the information, the information source, or any other aspects.

* BTAA Geoportal Project Glossary of Terms
https://sites.google.com/umn.edu/btaa-gdp/about/project-documents/glossary

## Geospatial Information Types

* GIS data are usually stored in one of the following data models
  * Vector
  * Raster
  * Tabular

* Geospatial information can be found from scanned maps

* GIS data can be hosted online using web services

<table>
  <tr>
    <td>Vector</td>
    <td rowspan="4">Web Services</td>
  </tr>
  <tr>
    <td>Raster</td>
  </tr>
  <tr>
    <td>Tabular</td>
  </tr>
  <tr>
    <td>Scanned Map</td>
  </tr>
</table>

### Vector Data

<table>
  <tr>
    <th style="color:red;">Vector</th>
    <td rowspan="4">Web Services</td>
  </tr>
  <tr>
    <td>Raster</td>
  </tr>
  <tr>
    <td>Tabular</td>
  </tr>
  <tr>
    <td>Scanned Map</td>
  </tr>
</table>

* Vector data are comprised of vertices and lines (or arcs), represented explicitly in the form of XY coordinates.

* The 3 basic geometry types for vector data are:

  * Points - XY coordinates

    * Example: cities, schools, incident locations

  * Lines - connecting the points in a set order

    * Example: roads, streams

  * Polygons - a set of points in a particular order and close it (the 1st and last point are the same)

    * Example: a state, county, or census block

* Most GIS applications do not allow mixed geometry type
In a single layer

![Vector Data Types](images/vector-data.png)  
**Figure 01**. Vector Data Types *Used by permission of Paul Bolstad, GIS Fundamentals

* Each vector feature has attribute data that describe it.

![Attribute Data](images/attributes.png)  
**Figure 02**. Attribute Data

* Vector data are usually saved as a shapefile or a feature class in a geodatabase (In Arc/Info (1980-1999), it can also be saved in coverage format).

* Vector symbology:

![Single Symbol](images/single-symbol.png)  
**Figure 03**. Single Symbol

![Categorical Symbol](images/categorical-symbol.png)  
**Figure 04**. Categorical Symbol

![Quantitative Symbol](images/quantitative-symbol.png)  
**Figure 05**. Quantitative Symbol

### Raster Data

<table>
  <tr>
    <td>Vector</td>
    <td rowspan="4">Web Services</td>
  </tr>
  <tr>
    <th style="color:red;">Raster</th>
  </tr>
  <tr>
    <td>Tabular</td>
  </tr>
  <tr>
    <td>Scanned Map</td>
  </tr>
</table>

* Raster data is made up of pixels with each pixel has its own 
Value.

* Raster data is usually used to represent surfaces.

* Raster data model is commonly used for digital elevation models (DEM), aerial and satellite imagery, and land use land cover maps.

* Raster data resolution: cell dimension, or the size of pixels.

* Raster images can consume a large amount of storage space.

![Raster Data Types](images/raster-data.png)  
**Figure 06**. Raster Data Types *Used by permission of Paul Bolstad, GIS Fundamentals

* Two types of raster data: **continuous** and **discrete**

  * **Discrete** rasters have distinct themes or categories. Each class can be discretely defined, usually ba integer values. Example, land cover/use map.

  * **Continuous** rasters are grid cells with gradual changing data such as elevation and temperature.

![Raster Two Types](images/raster-two-types.png)  
**Figure 07**. Continuous and Categorical Data *Used by permission of Paul Bolstad, GIS Fundamentals

* Raster data are usually saved in the format of raster dataset, GeoTIFF, or many other formats.

### Vector vs. Raster

|   |**Vector**|**Raster**|
|---|---|---|
|**Positional Precision**|Can be precise|Defined by cell size|
|**Attribute Precision**|Poor for continuous data|Good for continuous data|
|**Output Quality**|Very good, map like|Fair to poor, depending on resolution|
|**Data Structure**|Often complex|Often quite simple|
|**Storage Requirement**|Relatively small|Often quite large|
|**Spatial Analysis**|Good topology relationship|Good for modeling|

### Tabular Data

<table>
  <tr>
    <td>Vector</td>
    <td rowspan="4">Web Services</td>
  </tr>
  <tr>
    <td>Raster</td>
  </tr>
  <tr>
    <th style="color:red;">Tabular</th>
  </tr>
  <tr>
    <td>Scanned Map</td>
  </tr>
</table>

* Tables with geospatial information can be used for mapping purpose in GIS.

  * Tables with information that can be joined with an existing map 
  Reference: Tutorial about table join

  * Tables with XY coordinate information

  * Tables with address information

    * Geocoding

### Scanned Maps

<table>
  <tr>
    <td>Vector</td>
    <td rowspan="4">Web Services</td>
  </tr>
  <tr>
    <td>Raster</td>
  </tr>
  <tr>
    <td>Tabular</td>
  </tr>
  <tr>
    <th style="color:red;">Scanned Map</th>
  </tr>
</table>

* A scanned map stored as an image file.

    * Georeferenced scanned map: has a linked file that stores spatial information so that it can be overlayed with other digital maps in GIS. Usually stored as GeoTIFF.

    * Un-georeferenced scanned map: The presence of coordinates in the record’s metadata does not make the map georeferenced. Can be saved as TIFF or JPG, etc.

![Scanned Map](images/scan-map.png)  
**Figure 08**. A Scanned Map

### Web Services - GIS

<table>
  <tr>
    <td>Vector</td>
    <th rowspan="4" style="color:red;">Web Services</th>
  </tr>
  <tr>
    <td>Raster</td>
  </tr>
  <tr>
    <td>Tabular</td>
  </tr>
  <tr>
    <td>Scanned Map</td>
  </tr>
</table>

* A streaming GIS layer that can be viewed and queried in a
browser or GIS application.

* Types of GIS web services - they are often provided using either Esri format or open standard defined by Open Geospatial Consortium (OGC)

<table>
  <tr>
    <th rowspan="4">Esri</th>
    <td>ArcGIS Dynamic Map Layer Service</td>
    <td>Vector data. Map image layers are dynamically rendered.</td>
  </tr>
  <tr>
    <td>ArcGIS Feature Layer Service</td>
    <td>Displays vector data as individual or collected features.</td>
  </tr>
  <tr>
    <td>ArcGIS Image Map Layer Service</td>
    <td>Displays raster data (a grid of cells used to store imagery).</td>
  </tr>
  <tr>
    <td>ArcGIS Tiled Map Layer Service</td>
    <td>Displays set of web-accessible tiles that reside on a server.</td>
  </tr>
  <tr>
    <th rowspan="2">OGC</th>
    <td>Web Mapping Service (WMS)</td>
    <td>Renders a geospatial dataset as map images.</td>
  </tr>
    <td>Web Feature Service (WFS)</td>
    <td>Serves queryable geographic features.</td>  
  <tr>
    <th>IIIF</th>
    <td>International Image Interoperability Framework (IIIF)</td>
    <td>Displays an image from a server. This image can be panned and zoomed.</td>
  </tr>
</table>

## How to Find These Data in the BTAA Geoportal

The [Big Ten Academic Alliance Geoportal](https://geo.btaa.org/) connects users to digital geospatial resources, including **GIS datasets**, **web services**, and **digitized historical maps** from multiple data clearinghouses and library catalogs. The site is solely a search tool and does not host any data.

### Search by Resource Class

Once you are at the search results page of BTAA Geoportal, you have filter options on the left of the screen. You can filter your search by **Resource Class**.

* **Datasets:** vector or raster data

* **Maps:** scanned maps and photographs

* **Web Services:** for items with a web service, such as an ArcGIS REST service, an OGC web service, or IIIF.

* **Imagery** Aerial photography and satellite imagery

* **Collections:** describe a group of records, typically as a description of and website link to the group’s original geoportal or library.

* **Websites:** interactive web resource, such as dashboard.

## Related Resources

* [BTAA Geoportal Project Glossary of Terms](https://sites.google.com/umn.edu/btaa-gdp/about/project-documents/glossary)

* [Finding Geospatial Data (Tutorial)](https://docs.google.com/presentation/d/1xL_DnaKo6ECf7qcLVHdXPTVafcFk0wCHB7CLBayRPnA/edit#slide=id.g86c86e5ff3_0_881)

* [Linking tabular data to geospatial data (Tutorial)](https://docs.google.com/presentation/d/16wAdW9CNF_-8uzbShy5BCR_DXCQwsnpJ5mRWvp4Hubw/edit#slide=id.p1)

* [Using GIS web services (Tutorial)](https://docs.google.com/presentation/d/1wDmTt4HCwKOFn_4uSUBW2rrJlxWODiFfs-lP8-CWLQU/edit#slide=id.p2)

## Exercise

* Find an example for each of following type of data from BTAA geoportal. Discuss the use cases of each data type, as well as pros/cons of the particular data type.
  * Vector data
  * Raster data
  * Scanned map
  * Web service

## Wrapping Up

This tutorial is part of an educational series produced by members of the [Big Ten Academic Alliance Geoportal](https://geo.btaa.org/). The BTAA Geoportal connects users to digital geospatial resources, including GIS datasets, web services, and digitized historical maps from multiple data clearinghouses and library catalogs. The site is solely a search tool and does not host any data.

To access additional tutorials in this series that cover various other topics, visit: https://sites.google.com/umn.edu/btaa-gdp/tutorials. 

**License statement:**
Except where otherwise noted, content in this tutorial is licensed under a [Creative Commons Attribution 4.0 International license](https://creativecommons.org/licenses/by/4.0/).


**Providing attribution for this work:**
“Types of Geospatial Information” by [Nicole Kong](https://www.lib.purdue.edu/people/kongn) is licensed under a [Creative Commons Attribution 4.0 International license](https://creativecommons.org/licenses/by/4.0/).