# 3D Modeling with a Scanned Shaded Relief Map
Adding three dimensionality to a classic shaded relief map of Yosemite National Park

The [BTAA Geoportal](https://geo.btaa.org/) has a wealth of interesting and beautiful historic scanned maps available to the public to download. Recently, I discovered John Henry Renshawe's shaded relief maps of US national parks from the early 1900s. Using his [Panoramic View of the Yosemite National Park, California](https://geo.btaa.org/catalog/p16022coll230:2495) from 1914, I wanted to demonstrate an open-source technique for adding three dimensionality to these fantastic relief maps.

![Panoramic View of the Yosemite National Park](screenshots/1_yosemite.png)

## Download and Georeference the JPG File

The first step is to download the map [here](https://geo.btaa.org/catalog/p16022coll230:2495) and load it into a georeferencer tool in your favorite GIS software. While I find georeferencing in ArcGIS Pro to be an intuitive breeze, I used the Georeferencer tool in QGIS to keep with an open-source and MacOS-oriented workflow. You can do a lot of amazing GIS work in the comfort of your home with a MacBook!