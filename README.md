The California Alcohol Beverage Control maintains a [dataset](http://www.abc.ca.gov/datport/DataExport.html) of the current list of alcohol licenses in the state, which is exported weekly. This includes a wide range of license types for various on-premise or off-premise alcohol, each of which carries different privileges (beer only, winegrower, restaurant, etc). A single location can hold multiple license types (a wine grower can also sell wine, a restaurant can also have a bar, etc). The research organization I work for uses this type of data to study spatial relationships between sources of alcohol and alcohol related problems. 

Because of the way that this data is formatted, there are a number of steps that need to be taken along the way before it finds itself in a usable form. ```Pandas```, ```Geopandas```, and ```Geopy``` make this process relatively easy, as I demonstrate below. In the following notebook, I will:

1. Download the most recent export of California alcohol license data
2. Read in the fixed-with text file into Pandas
3. Aggregate license-level data to location-level data, identifying locations of three types of active alcohol outlets: off-premise outlets (liquor stores), bars, and restaurants. 
4. Geocode and get the lat/long coordinates of a subset of the data - all bars in San Francisco
5. Convert lat / long coordinates to projected GeoSeries as part of GeoDataFrame
6. Overlay point locations with a shapefile of SF neighborhoods to look at bar densities
7. Make a simple map using the built-in plotting feature in GeoPandas
8. Export the data as a shapefile for future use