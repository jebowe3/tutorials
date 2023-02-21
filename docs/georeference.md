---
title: Georeference
summary: In this tutorial, you will learn how to georeference a historical map by using ArcMap. 
authors:
    - Wenjie Wang
date: 2021-08-16

hide:
 - navigation
---

# Georeference

## Contents
- [Overview of Georeferencing](#overview-of-georeferencing)
- [Download Data](#download-data)
- [Data Processing](#data-processing)
- [Publish Map on ArcGIS Online](#publish-map-on-arcgis-online)

## Overview of Georeferencing

Georeferencing is a commonly used tool to accurately digitize data on a paper map. It uses a series of control points in the digital image to associate this image with spatial locations. The digital image could be an aerial photography, a scanned map, or a picture of a topographic map. The georeferenced map can be used for basic map analysis, such as calculating distances and areas. In this tutorial, you will learn how to georeference a historical map by using ArcMap. 

## Download Data

1. Open BTAA geoportal: https://geo.btaa.org/

2. Search term “Hyde Park Community”

3. Click Original Jpeg button to open the map

4. Right click the map and save image as “G4104-C6-2H9-1920z-U5.jpg”

## Data Processing

1. Open ArcMap

2. Click Add Basemap and choose Streets map

3. Zoom in to the study area: Hyde Park, Chicago, Illinois

![Add Basemap](images/basemap.png)\
**Figure 01**. Add Basemap and Zoom to Hyde Park

4. Click Add data and choose the image “G4104-C6-2H9-1920z-U5.jpg”

5. Click Customize -> Toolbar -> Georeferencing to add georeferenced tool

6. Click Fit To Display to show the image in the study area.

![Fit Display](images/fit-display.png)\
**Figure 02**. Fit Scanned Map to Display

7. Right click Layers -> Properties and select WGS_1984_Web_Mercator_Auxiliary_Sphere as the coordinate system. 

![Set Coordinate System](images/set-coord-sys.png)\
**Figure 03**. Set Coordinate System

8. Click Viewer to show the image in a new window.

9. Click Add control Points to select control points. Select control points from the viewer window, and then choose the corresponding location in the street map.

![Add Control Points](images/control-points.png)\
**Figure 04**. Add Control Points

10. Select control points in the area close to the four corners of the map.

11. Select additional control points. The more points you assign the more accurate your georeferenced map will be.

![More Control Points](images/point-diagram.png)\
**Figure 05**. More Control Points

Here are some tips for choosing control points:

- The number of control points needed depends on the image being used. Normally, at least four control points are required for georeferencing.

- Choose road crossings or sidewalk intersections, because the edges of roads may change over time.

- The control points should be spread across the unreferenced image.

12. Click View Link Table. It is up to you to determine the acceptable residual values. If a link has a residual value much larger than others, the link should be deleted. 

![Residual Values](images/residual-values.png)\
**Figure 06**. More Control Points

13. After georeferencing, click Rectify to save the result.

14. In the layer property, change transparency to 50%. It is an easy to compare the georeferenced map locations with the real world locations.

![Transparency](images/transparency.png)\
**Figure 07**. Make Map Overlay Semi-Transparent

## Publish Map on ArcGIS Online

- This topic is optional. to publish a hosted layer, you will need publishing privileges in your ArcGIS organizational account.

- Publishing a tiled service to ArcGIS Online will consume credits, which are the currency used   across ArcGIS. To estimate how many credits you will need to perform specific transactions or store data, you can refer to this website: https://doc.arcgis.com/en/arcgis-online/administer/credits.htm

1. Sign in with your university account.

2. Remove Basemap

3. Click File -> Share as -> Service

4. Choose Public a service

5. Choose a connection and enter service name

![Share Service](images/share-service.png)\
**Figure 08**. Share as a Service

6. Select Tiled Mapping

7. Enter information in Item Description

8. In the Sharing tab, you can choose to share your service with yourself (private), your organization, or everyone (public) 

![Enter Service Information](images/service-info.png)\
**Figure 09**. Enter Service Information

9. Select appropriate levels of detail. Do not choose extreme large cashe size, which may consume all your credits. 

10. Click Publish button to publish this service.

11. Tile Packages can be used to save credits. You will not be charged for generating tiles. You will only be charged for tile storage. For more information, please refer to:  https://www.esri.com/about/newsroom/arcuser/use-tile-packages-to-save-credits/

![Scale Range](images/tile-scales.png)\
**Figure 10**. Define Scale Range for Tiles

12. Log in to ArcGIS Online and open the published map in your Content. The map can be digitized for further usage. For more information, please refer to the Digitizing tutorial, which was prepared by Nicole Kong.

![Open in ArcGIS Online](images/open-arcgis-online.png)\
**Figure 11**. Open in ArcGIS Online