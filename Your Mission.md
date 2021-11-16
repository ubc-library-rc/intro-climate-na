**Your Mission**

Should you choose to accept it...

There is concern over the recent introduction of an herbaceous perennial *Herbacicus invadicus* to coastal BC. In particular, it is not known just how well established the plant is on Vancouver Island. Your research team has been tasked with identifying locations on the Island that would be suitable for establishment for follow up with further study. We have certain known environmental conditions *H. invadicus* requires to survive, including:

* Air temperature hardy to -5 degrees Celsius
* Root temperature hardy to -10 degrees Celsius
* Drought sensitive when annual precipitation is below 60mm
* Heat sensitive when max temperatures exceed 35 degrees Celsius
* Found only at elevations below 1000m

Your task is to identify where on Vancouver Island these climatic conditions are met, potentially allowing for establishment of *H invadicus*.

**Process**

In QGIS

1. Ttrace out Vancouver Island
2. Create a grid point with the following attributes
   1. ID1, ID2, Lat, Long, Elev
3. Isolate points only within Vancouver Island
4. Convert to decimal degree
5. Import location data for weather stations
6. Clean up removing all fields except ID1, ID2, Lat, Long, Elev
7. Export to csv

**Need to merge in Elevation data and drop elevation levels below a certain threshold - when do we do this?**

In ClimateNA

1. Import csv
2. Select values and reference year to calculate
   1. Min annual temp
   2. Max annual temp
   3. Average precipiation
3. Export

QGIS

1. Import ClimateNA file
2. Add a field that estimates soil temperature min
3. Add a field to calculate needed parameters of
   1. precipitation
   2. temperature (min and max allowable)
   3. soil temperature
4. Visualize the resulting clusters
5. Export the relevant data points