# 3D Modeling with a Scanned Shaded Relief Map
Adding three dimensionality to a classic shaded relief map of Yosemite National Park

The [BTAA Geoportal](https://geo.btaa.org/) has a wealth of interesting and beautiful historic scanned maps available to the public to download. Recently, I discovered John Henry Renshawe's shaded relief maps of US national parks from the early 1900s. Using his [Panoramic View of the Yosemite National Park, California](https://geo.btaa.org/catalog/p16022coll230:2495) from 1914, I wanted to demonstrate an open-source technique for adding three dimensionality to these fantastic relief maps.

![Panoramic View of the Yosemite National Park](screenshots/1_yosemite.png)

## Download and Georeference the JPG File

The first step is to download the map [here](https://geo.btaa.org/catalog/p16022coll230:2495) and load it into a georeferencer tool in your favorite GIS software. While I find georeferencing in ArcGIS Pro to be an intuitive breeze, I used the Georeferencer tool in QGIS to keep with an open-source and MacOS-oriented workflow. You can do a lot of amazing GIS work in the comfort of your home with a MacBook!

![Georeferencing in QGIS](screenshots/2_georeference.png)

As shown in the screenshot above, I rubbersheeted the scanned Yosemite map by locating a series of six control points shared between the scanned map in the Georeferencer and the Esri Topo World basemap in the QGIS map window. If you are lucky, the map you wish to georeference will have latitude and longitude lines, and you can enter more accurate coordinates for your points at their intersections. However, in this case, I had to locate a few prominent shared features. For my transformation settings, I used a thin plate spline transformation type and a cubic spline resampling method. I find these settings best for older maps, especially when the projection is unknown.

## Download Raster Elevation Data, Merge, and Clip

Next, you will need some raster elevation data at an appropriate resolution for the area of interest. This will be used to generate the three dimensional terrain used to warp the shaded relief map. I downloaded two hgt files from a collection called ["NASA Shuttle Radar Topography Mission Global 1 arc second V003"](https://search.earthdata.nasa.gov/search/granules?p=C2763266360-LPCLOUD&pg[0][v]=f&pg[0][gsk]=-start_date&sb[0]=-119.70264%2C37.47469%2C-119.1709%2C38.2173&tl=1731453010.335!3!!&lat=37.82208275504045&long=-121.453857421875&zoom=7) at NASA's [Earthdata Search](https://search.earthdata.nasa.gov/search) as shown in the image below.

![NASA Earthdata](screenshots/3_nasa_elevation.png)

Then, drag and drop the two raster hgt files into QGIS. You will need to stitch these two files together using the Merge tool, located at Raster > Miscellaneous > Merge within the dropdown options at the top. The merged image will exceed the extent of the shaded relief map, but you can clip the result by creating and using a mask layer. Choose Layer > Create Layer > New Shapefile Layer from the dropdown options at the top and trace the border of the mapped region, as shown below.

![Mask Layer](screenshots/4_mask.png)