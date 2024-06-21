# SDG_Leaflet
Create a global SDG Choropleth Map using Leaflet
See a live working version here https://bricker0.github.io/leaflet.html  
## Steps
•	Convert your shapefile to geojson<br>
•	Create a webmap using the Leaflet API<br>
•	Reference your geojson file on your webmap<br>
## Prepare your data in QGIS
Open your shapefile with the countries and joined data. <br>
Open the attribute table. <br>
Please make sure you write down the goal, target, and indicator title year the data were collected and any other relevant info that you might want to include in the text on your website about the map. <br>
The SDG value – if it is more than 2 decimal places, please convert the value to an integer.  <br>
To do this – when the attribute table is open and editable –click field calculator this icon. <br>
Toggle “Create New Field” and name it SDG<br>
Then cut and paste this expression and replace SDG_Field with the name of the field with your SDG indicator in it. <br>
```
To_int(“SDG_Field”)
```
Then click ok and the new field should generate. <br>
Now we will  export and Convert to GeoJSON. <br>
Right-click and the layer <b>Export</b> Save Vector Layer As<br>
Format change to GeoJSON<br>
Name your file and make sure you see where it is being saved.<br>
You only need to keep the attribute with the name of the country and the value – so only toggle the country name and the SDG value field you just created.<br>
##Open the new GeoJSON file in a text editor
One line one before the open brackets Add 
```
var nationData=
```

Next Click File Save As and name it and save it with .js extension

Close this file. <br>

## Modify the HTML file
Next open the HTML file found here. Find all the places I left UPDATE in the comments. These are the places you need to make changes to reference your documents. You can control f to find those places.
<br>
Good luck!
