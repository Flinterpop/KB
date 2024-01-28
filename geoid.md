Good theoretical notes
https://www.esri.com/news/arcuser/0703/geoid1of3.html






from: https://www.topolynx.com/help/topoxplore/the_geoid_undulation.html

GPS receivers output the height of the GPS antenna, in meters, via the GGA sentence of the NMEA protocol. This height is relative to Mean Sea Level. Many GPS receivers also output the geoid undulation, in meters, via the same GGA sentence.

The geoid undulation is the distance between the geoid and ellipsoid. 
 

Height Above Ellipsoid = Main See Level Height ± Geoid undulation value


This Height Above Ellipsoid value is based on the datum used by the GPS receiver, which is typically WGS84. The default unit for Height Above Ellipsoid value is meter. 

11) Geoidal separation, the difference between the WGS-84 earth ellipsoid and mean-sea-level (geoid), "-" means mean-sea-level below ellipsoid.

Relation to Geoid Undulation

 

H = h - N

 

H:   Ellipsoid height  

h:   Orthometric height (Field 9) (mean-sea-level height)

N:   Geoidal separation (Field 11)

 

What you read in field 9 is an orthometric height (h) corrected by global geoidal separation (N) in meters, based on the official NATO's standard mean-sea-level algorithm (5-degree grid of height).  


To calculate the ellipsoid height (H) use this formula:

H = h - N (NATO) 

(H = Field 9 - Field 11)

Now use the interpolated geoidal separation to calculate the correct ellipsoid height (h).

h = H + N (EGM2008 interpolated)

---
from
https://customersupport.septentrio.com/s/article/Why-is-the-height-reported-by-NMEA-GGA-different-from-the-expected-value#:~:text=The%20GGA%20sentence%20is%20the,geoid%20height%20or%20geoidal%20separation).


The GGA sentence is the only NMEA sentence which reports height information. By definition, this sentence reports the orthometric height and the corresponding undulation: the local difference between the geoidal and the ellipsoidal height (which is sometimes also called the geoid height or geoidal separation). By default, all Septentrio receivers use a fairly coarse geoid model which is a 10 by 10 degree approximation of the WGS84-geoid. Because geoidal models require a lot of memory, it is not possible to upload other geoidal models to Septentrio receivers. For centimeter-level applications, highly accurate external geoid models should be used.


Since the receiver calculates the geoidal height by subtracting the undulation from the ellipsoidal height rather than the other way around, it is possible to use the GGA message to output the ellipsoidal height rather than the geoidal one by defining a manual undulation value of 0.

