# BluPlusTagData
SSRS managed code for getting Blu+ tag detection data from the CTT Blu+ portal and 
mapping it.

The goal of this project is to quickly generate rleaflet maps to answer spatial
questions like habitat scoring to give covariates not available in GIS layers.

We also have maps with time sliders and all tags in one map to see if common 
corridors of travel can be detected.

Our current examples code detections by confidence score and time to next point.
The idea here is to look at some important habitat features that can be scored 
by looking at the map.  For example, we are interested in knowing how stopovers 
related to cattle yards and wetland complexes.

## Blu+ tag detection tools
### Interactive maps in R leaflet
In order to explore habitat use and movement at a number of spatial and temporal scales we have produced several types of interactive maps with the R (R Core Team, 2026; version 4.6.1) leaflet mapping package (Cheng et al., 2025; version 2.2.3).  The maps have shared characteristics.  They can easily be exported in a sharable format (as a standalone .html file).  They are all zoomable.  There is a control widget that allows the viewer to turn off and on data layers and change the background map.  There is a scale bar and a legend showing what the color and size of individual points mean.  Hovering over points shows a label and clicking on a point shows a description.  The time-focused maps have a time slider that allows you to limit the points displayed to be in a certain datetime range.  To use this, you must first turn off the crowd sourced points and then set the time slider range.  On all maps, if the viewer hovers the mouse over an individual detection, it will display a label that shows sequential ID (equivalent to the row in a spreadsheet to allow you to enter habitat data in the correct row), and Date and time (UTC or local time).  Finally, clicking on individual points produces a description to show confidence score and time to next detection in days, hours, minutes, seconds.

Zoomable maps can be used for several tasks:

1.	Characterize habitat features near where birds were detected:  While GIS approaches using landcover data can give us some information, we have designed interactive maps to allow managers to drill down for each detection by zooming in and recording habitat feature like, for example, livestock operations within a 100m or 1km radius of the detection.  This should make it possible to examine the effects of management practices and to identify important habitat patches.  So, for example, we currently plot two circles (100m and 1km) around each detection to allow scoring each detection for features in those ranges like cattle operations, wetland areas, etc.  Lines are drawn to allow a viewer to move from one detection to the next to understand movements.  We also generate an Excel sheet for recording habitat features.  Time to next detection is output for use in deciding whether detections represent overflights or stop-overs.
    a.	This map shows:
      i.	Zoomed out detections
        1.	The map shows multiple detections near each other as a circle with the count representing the number of nearby detections
        2.	Hovering over the circle shows a convex polygon representing the locations of all the points shown in the count
        3.	If you click on this circle, the map will zoom in, possibly showing individual detections (separating them if possible so you can hover or click on them)
      ii.	Individual detections (once you zoom in close enough)
        1.	Circle size represents CTT’s confidence score, 
        2.	Circle color represents time to next detection, 
    b.	The Excel spreadsheet outputs the location, datetime, month, time of day, time to next detection, and other variables designed for a viewer to score habitat features (e.g., distance to next detection, pond or river in 100m, ditch in 100m, cattle yard in 100m, orchard in 100m, row crop in 100m, fly over, cattle yard in 1km).  These columns can be easily changed or expanded in the code.
3.	Show time of season (month) on map:  To gain a better understanding of how individual tagged birds move around during the season, we generated a map with the following characteristics:
    a.	Individual detections are color coded by month.
4.	Show time of day (categories) on map:  To understand how birds move during the day, we produce a map with:
    a.	Individual detections colored by time period (night, dawn, morning, afternoon, evening)
    b.	You can use the time-slider to limit to certain months or periods by date

### Time of day plot
To get a sense for what focal points in space with large numbers of detections are being used for, we plot a stacked histogram of hour local time.  This shows what times of day detections are being recorded.  It also shows whether these detections have a greater or less than 15 minutes time to next detection.  The idea is that locations with large numbers of short duration visits midday may indicate a foraging site.  On the other hand, if more detections have longer time to next detection, it could indicate either proximity to roosting or nesting sites, or long distance to next detection hot spot.
