---
title: 11 Build a Zonal Stats Tool with Python and Jupyter Notebook 
summary: This tutorial is meant to show users how to create an open-source GUI tool that accepts a raster file and a polygon shapefile as inputs and calculates the coverage of a given range of raster classes within the shapefile polygon.
authors:
    - Jay Bowen
date: 2021-06-09
hide:
 - navigation
---

!!! Info

    *This tutorial is part of an educational series produced by members of the [Big Ten Academic Alliance Geospatial Information Network](https://geo.btaa.org).*

    :fontawesome-solid-user: Prepared by: Jay Bowen, Geographic Information Specialist, University of Iowa (jay-bowen@uiowa.edu). 

    :material-creative-commons: These slides and the accompanying activities are licensed under a [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) license.

------------------------------

??? Note "Note for Instructors"

    This tutorial is intended for both MacOS and Windows GIS users with a cursory understanding of how to use python scripts, regardless of whether they are graduate, undergraduate, or faculty/staff users. These users may wish to create easy to use free-standing analytical tools that they can run without desktop GIS software, but are unsure of how to write a script to create GUI-driven tools. 

    This tutorial is meant to show users how to create an open-source GUI tool that accepts a raster file and a polygon shapefile as inputs and calculates the coverage of a given range of raster classes within the shapefile polygon. 

    The tutorial was designed for self-guided independent learning.

------------------------------


## Introduction

You may need to know the percentage of a specific area devoted to a type of land cover, also known as a zonal statistic. For example,  you may work for a city government office charged with researching climate change mitigation strategies. You know that more trees are associated with a reduction of extreme heat. You might wish to calculate how much of the land in your city is covered by tree canopy to compare this to a desired benchmark.

Usually, people calculate this by turning to the ArcGIS tool suite, or by running ArcPy in the ArcGIS Python Window. However, ArcGIS can be expensive and out of reach for many users. Moreover, apart from ArcGIS Online, the software depends on Windows, limiting its use. This tutorial will show users how to derive zonal statistics without ArcGIS tools or ArcPy scripting. 

In this example, you will begin with a land cover raster for the State of Iowa and a shapefile of Iowa City. The tutorial will walk through the installation and use of open-source Python packages in Jupyter Notebook and Anaconda-Navigator to calculate the percentage of Iowa City covered by tree canopy (represented by classes 3, 4, 5, and 6 in the raster data). 

??? Note "Note"

    **This code is not meant to be run in IDLE or the ArcGIS Python Window.**

## Learning Objectives

Students will:

1.  Use basic Terminal or Command Prompt scripts

2.  Learn how to install and import Python packages, such as tkinter, gdal, and rasterstats.

3.  Implement these packages with Python scripting using Jupyter Notebook in Anaconda-Navigator to calculate zonal statistics for a range of raster classes within an area of interest defined by a shapefile polygon (% of Iowa City covered by tree canopy).

## Don’t have time to download and install Anaconda-Navigator and Jupyter Notebook?

-   That's fine! You can run the entire tutorial in [this Binder site for Jupyter Notebook](https://notebooks.gesis.org/binder/v2/gh/ui-libraries/Zonal_Statistics_Tool_JupyterNotebook/HEAD). Just follow the embedded link and click on the "ZonalStatistics_withWidgets.ipynb" file.

-   If you decide to use the Binder tutorial, you may close out of this presentation.

??? Note "Note" 
    
    The Binder tutorial replaces the tkinter GUI with ipywidgets in order to handle user inputs within Binder over the web.

## Prepare Directory Structure

-   Open Terminal on Mac, or Command Prompt on Windows.

-   If you are using Windows Command Prompt on an institutional or office PC and it defaults to a drive other than the C drive and your user name (such as H:\>), input the following to point it to the correct place on the C drive (replace "johnsmith" with your own user name) and press enter:

```shell 
cd /d C:\Users\johnsmith
```

-   In Mac Terminal,  input the following and leave Terminal open:

```bash
mkdir Desktop/zonal_statistics && mkdir Desktop/zonal_statistics/data && curl https://raw.githubusercontent.com/jebowe3/zonalstats_jupyternotebook/main/ZonalStatistics.ipynb -L -o Desktop/zonal_statistics/ZonalStatistics.ipynb
```

-   In Windows Command Prompt, type the following and leave Command Prompt open:

```shell
mkdir Desktop\zonal_statistics && mkdir Desktop\zonal_statistics\data && curl https://raw.githubusercontent.com/jebowe3/zonalstats_jupyternotebook/main/ZonalStatistics.ipynb -L -o Desktop/zonal_statistics/ZonalStatistics.ipynb
```

-   This will create a folder on your desktop called "zonal_statistics" and another folder called "data" within the desktop "zonal_statistics" folder. It will also download the Jupyter Notebook .ipynb file with all of the python code.

<figure markdown>

![Media Options](images/directory-structure.png)<figcaption>Directory Structure</figcaption>

</figure>

## Gather and Prepare Data

-   Open the [BTAA Geoportal](https://geo.btaa.org/)

-   In the search bar, type "High Resolution Land Cover of Iowa in 2009 Counties: Iowa"

-   Choose and open the [result](https://geo.btaa.org/catalog/2265abfa-0513-4a83-87a7-38304384d736) and click the "Original Raster Dataset" button at the right side of the page

<figure markdown>

![Media Options](images/high-res-lc.png)<figcaption>Original Raster Dataset</figcaption>

</figure>

-   From the list of counties, choose "Johnson"

-   Download, unzip, and save the folder inside the "Desktop/zonal_statistics/data" folder you just created

<figure markdown>

![Media Options](images/johnson-zip.png)<figcaption>Download, Unzip, & Save</figcaption>

</figure>

-   Return to Terminal or Command Prompt and type the following code to download the Iowa City boundary files to your data folder:

```bash
curl https://github.com/jebowe3/zonalstats_jupyternotebook/raw/main/IowaCity_Shapefile.zip -L -o Desktop/zonal_statistics/data/Iowa_City_Poly.zip
```

-   Unzip this folder so that you have access to the shapefile within it

<figure markdown>

![Media Options](images/unzipped-folder.png)<figcaption>Unzip Iowa_City_Poly.zip</figcaption>

</figure>

## Download Necessary Programs