<<<<<<< HEAD

## Grasshopper Components
The grasshopper components we have created for writing and reading GeoJSON include:
### Brep to Polygon
Takes in Breps, and deconstructs to a curve. Records the height and base_height of the brep for later use in the Polygon to GeoJSON component.<br>
![Alt text](/assets/pictures/brepTpPolygon.jpeg)
### Polygon to GeoJSON 
Writes a polygon to a GeoJSON file, where keys can be defined. These keys will be picked up by MapBox and used to render the geometry in the website.
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
    tag
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


###File Write
Writes the produced GeoJSON Feature Collection to a file. <br>
![Alt text](/assets/pictures/fileWrite.png)
####Content 
Plug in the results from the Polygon to GeoJSON component
####File Path
Where the new file will be saved to.
####File Name
What the new file will be called.
####Activate
Connect a Boolean toggle to save the file
 
###Merge GeoJSON to one file
If you have multiple polygon to geojson components and wish to merge them into one geojson file, plug the data streams into the GeoJSON Merge component. This creates one feature collection to write to file. You may want to do this so parts of the building express different qualities when rendering (eg: windows blue, mullions black, floor plates red)
<br> ![Alt text](/assets/pictures/geojsonMerge.jpg)
### GeoJSON to Polygon
Converts a GeoJSON file to a geometry in Grasshopper
![Alt text](/JSONPolygon.png)
#### GeoJSON (J)
Input GeoJSON File.
#### Polyline Curve (P)
Outputs Close Polygon Curve.
#### Closed Brep (B)
Outputs Closed Brep if the GeoJSON contains a property called 'height' with a numeric value.
#### Colour (C)
Outputs a colour value if the GeoJSON contains a property called 'colour'. 
<br><br>
=======
#UrbanCoDe
UrbanCoDe aims to be an invaluable to the community and architects alike. Using the API of Mapbox, design proposals can be presented to the public in a clear graphical format, engaging the wider community of Sydney in urban design outcomes and solutions. Creating a platform for informed community discussion, individuals actively engage in public issues and solutions, allowing  a glimpse into the psychology behind decision making processes. Aspects such as environment, transport connections and aesthetics can be judged for their function and form.  Design variables and their relationships to one another can be simulated and understood. With an aim to improve design culture and equality of information, this exploration into the capabilities of computational design showcases how we can algorithmically deal with urban space possibilities. 
<br><br>
##Project Progress 
Stage one of the research progress requires showing geometry created in Rhino and Grasshopper in a dynamic website, in this case we are using Mapbox. Mapbox is a flexible mapping platform used in the development of many apps that require live data visualisations and directions in traffic. It sources its geographical data from Open Street Maps. A new feature in Mapbox is visualising buildings in 3D. <br><br>
![Alt text](/mapbox.jpg)
<br><br>
It is through this feature that we can insert our own 3d geometries into Mapbox. Mapbox requires the format of the geometry be in geoJSON, a format that may represent a geometry (in this case a polygon), and a collection of features. These features can be read by the Mapbox API and used to visualise the geometry. We can control the geometries shape, colour, base height and extrusion height. <br>
We do this by adding a layer in the script section of the HTML code
```javascript    
map.addLayer({
        "id": "fromgrasshopper",
        "type": "fill-extrusion",
        "source": "json-buildings",
           'paint': {
                'fill-extrusion-color' : {
                    'property': 'colour',
                    'type': 'identity'
                },
                'fill-extrusion-height' : {
                    'type': 'identity',
                    'property': 'height'
                },
                'fill-extrusion-base' : {
                    'type': 'identity',
                    'property': 'base_height'
                },
                 'fill-extrusion-opacity': .6
            }
});
```
We can insert any geoJSON file into the code and it will display in Mapbox. However, generating this geoJSON file may prove challenging without the right tools available. Through Grasshopper, it is possible that a user can draw a geometry in Rhino, assign attributes and properties, have grasshopper then deconstruct the geometry, and write a geoJSON file so it can be reconstructed in Mapbox. This tool can later be packaged and uploaded to Food4Rhino as a Grasshopper plugin.


>>>>>>> origin/master
![Alt text](/testsite.png)
<br><br>
here is a case of geometry being created and exported from Grasshopper to Mapbox. The variables of geographical points, colour, base height and top height differ depending on the geometry.
<br><br>
In our case, we are using Grasshopper to create a geoJSON that is able to specifically communicate with Mapbox and display geometries there for the purpose of UrbanPinboard. However, there are many other possible applications with this Grasshopper tool, for those that want to produce geoJSON files from Rhino and Grasshopper geometries. 
<<<<<<< HEAD
=======
<br><br>
##Use of Components in a Case Study
We have created our own components for exporting GeoJSON from Grasshopper. We have managed to export entire buildings from Grasshopper to the website with floor plates, windows and mullions different colours identifying each.
To place different buildings in the map, we simply add a layer containing the GeoJSON to be visualised. 
```javascript    
map.addSource('json-buildings', {
                    'type': 'geojson',
                    'data': './GeoJSON/test_upload.GeoJSON'
                }),
    map.addLayer({
        "id": "fromgrasshopper",
        "type": "fill-extrusion",
        "source": "json-buildings",
           'paint': {
                'fill-extrusion-color' : {
                    'property': 'colour',
                    'type': 'identity'
                },
                'fill-extrusion-height' : {
                    'type': 'identity',
                    'property': 'height'
                },
                'fill-extrusion-base' : {
                    'type': 'identity',
                    'property': 'base_height'
                },
                'fill-extrusion-opacity': .6
            }
    });	
```
When different buildings are in different layers, we can toggle the visibility on and off. This allows easy representation, showing multiple map configurations to clients, layers of building, etc
<br> insert gif of toggle <br>
Next, using the tag property from the GeoJSON file, we can extract the text describing aspects of the building and place them in a pop up when a certain area is clicked.
<br> insert gif of click <br>
Next we will create a tool in gh to generate built forms in accordance to gov regulations, which will show iterations of potential builds on opportunity sites. When these iterations are exported, their display can be toggled on and off in the website to show clients/gov/the community possible urban configurations that abide by the rules of the council. (psudocode)

>>>>>>> origin/master
