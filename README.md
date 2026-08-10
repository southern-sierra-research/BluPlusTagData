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
