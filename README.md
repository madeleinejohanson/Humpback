## Grasshopper Components
The grasshopper components we have created for writing and reading GeoJSON.
### Polygon to GeoJSON 
![Alt text](/PolygonJSON.png)
#### Polyline Curve (P)
Polygon to convert to GeoJSON.
#### Key (K)
Properties used to describe geometry.
<br>
To specify the height, base height and colour of the polygon on Mapbox, use the following keys:

    height
    base_height
    colour 
Please note that the keys are case sensitive.

#### Value (V)
Values of properties. The list should be structured so that the first branch of data is associated with the first key. This allows unique values to be associated with multiple polygons.

##### GeoJSON (J)
GeoJSON Feature Collection.


### GeoJSON to Polygon
![Alt text](/JSONPolygon.png)
#### GeoJSON (J)
Input GeoJSON File.
#### Polyline Curve (P)
Outputs Close Polygon Curve.
#### Closed Brep (B)
Outputs Closed Brep if the GeoJSON contains a property called 'height' with a numeric value.
#### Colour (C)
Outputs a colour value if the GeoJSON contains a property called 'colour'. 

### deconstruct/analyse brep for geojson conversion 

###Merge GeoJSON to one file

<br><br>
![Alt text](/testsite.png)
<br><br>
here is a case of geometry being created and exported from Grasshopper to Mapbox. The variables of geographical points, colour, base height and top height differ depending on the geometry.
<br><br>
In our case, we are using Grasshopper to create a geoJSON that is able to specifically communicate with Mapbox and display geometries there for the purpose of UrbanPinboard. However, there are many other possible applications with this Grasshopper tool, for those that want to produce geoJSON files from Rhino and Grasshopper geometries. 
<br><br>
##Use of Components in a Case Study
exporting a whole building with floor plates, windows and mullions into from gh to Mapbox with geoJSON<br>
why? blurb to represent a building in mapbox must be exported...want detailed representations etc <br><br>
