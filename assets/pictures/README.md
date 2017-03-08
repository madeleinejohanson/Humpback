#UrbanCoDe
This the documentation and practical work of Madeleine Johanson and Nazmul Azim Khan, as we conduct our Computational  Design Honours research at UNSW and in collaboration with COX Architects Sydney.  Our previous study at COX included developing a data 'pipe' between computational tools such as grasshopper and web platforms, enabling designers to create computational tools to perform tasks with a simpler user interface. This visual, graphical interface therefore has the potential to increase communication not only between the architect and the client, but also within the architectural firm. 
<br><br>
Continuing from this research, we will aid in the developmental 'UrbanPinboard.' Urban Pinboard is a new tool for collaboration that connects the public, private and community sectors in a single conversation with innovative digital technology to drive smart city transformation. Urban Pinboard will be also unique and powerful because, unlike other one-way e-platforms in use around the world, it will allow these three sectors to not just access data but also exchange their ideas, thus creating a real and powerful feedback loop. It can be considered as a library of open urban data, represented graphically in a global map interface. The platform creates an interface between unreadable datasets and its users such as government policies, survey information and development proposals. UrbanPinboard has the potential to unlock communication barriers through technology, and produce accurate data flows where site potential can be determined through a dynamic platform.
<br><br>
The current research project, UrbanCoDe, aims to be an invaluable to the community and architects alike. With an aim to improve design culture and equality of information, design proposals can be presented to the public in a clear graphical format, engaging the wider community of Sydney in urban design outcomes and solutions. Creating a platform for informed community discussion, individuals actively engage in public issues and solutions, allowing  a glimpse into the psychology behind decision making processes. Aspects such as environment, transport connections and aesthetics can be judged for their function and form.  Design variables and their relationships to one another can be simulated and understood. This exploration into the capabilities of computational design showcases how we can algorithmically deal with urban space possibilities.
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

deconstruct/analyse brep for geojson conversion <br>
explain component cluster made<br><br>

merging geojson geometries bug <br>
FeatureCollections....can only handle one. when we merge data we need to get rid of (code)<br><br>

exported building <br><br>

creation of merge component <br><br>

toggle map layers <br>
easy representation, show multiple map configurations to clients, layers of building, etc 

