# Humpback Grasshopper Components
To display your 3D GeoJSON buildings in a world map, see https://madeleinejohanson.github.io/UrbanCoDe/ <br><br>
The grasshopper components we have created for writing and reading GeoJSON include:
### Brep to Polygon
Takes in Breps, and deconstructs to a curve. Records the height and base_height of the brep for later use in the Polygon to GeoJSON component.<br>
![Alt text](/assets/pictures/brepToPolygon.jpg)
### Polygon to GeoJSON 
Writes a polygon to a GeoJSON file, where keys can be defined. These keys will be picked up by MapBox and used to render the geometry in the website.<br>
![Alt text](/assets/pictures/PolygonJSON.png)
#### Polyline Curve (P)
Polygon or list of polygons to convert to GeoJSON.
#### Key (K)
Properties used to describe geometry.
<br>
To specify the height, base height, colour and tag of the polygon on Mapbox, use the following keys:

    height
    base_height
    colour 
    layer 
    tag
Layer gives you the ability to turn certain geometry off and on, depending on what key is associated with the layer. Tag enables a on-click text pop up to appear, giving more information about the object. <br>
Please note that the keys are case sensitive.
#### Value (V)
Values of properties. The list should be structured so that the first branch of data is associated with the first key. This allows unique values to be associated with multiple polygons. <br>
Example:<br>
> height : 100
> base_height : 0
> colour : red
> tag : building name
##### GeoJSON (J)
Produces a GeoJSON Feature Collection.


### File Write
Writes the produced GeoJSON Feature Collection to a file. <br>
![Alt text](/assets/pictures/fileWrite.jpg)
#### Content 
Plug in the results from the Polygon to GeoJSON component
#### File Path
Where the new file will be saved to.
#### File Name
What the new file will be called.
#### Activate
Connect a Boolean toggle to save the file
 
### Merge GeoJSON to one file
If you have multiple polygon to geojson components and wish to merge them into one geojson file, plug the data streams into the GeoJSON Merge component. This creates one feature collection to write to file. You may want to do this so parts of the building express different qualities when rendering (eg: windows blue, mullions black, floor plates red)
<br> ![Alt text](/assets/pictures/geojsonMerge.jpg)
### GeoJSON to Polygon
Converts a GeoJSON file to a geometry in Grasshopper<br>
![Alt text](/assets/pictures/JSONPolygon.png)
#### GeoJSON (J)
Input GeoJSON File.
#### Polyline Curve (P)
Outputs Close Polygon Curve.
#### Closed Brep (B)
Outputs Closed Brep if the GeoJSON contains a property called 'height' with a numeric value.
#### Colour (C)
Outputs a colour value if the GeoJSON contains a property called 'colour'. 
