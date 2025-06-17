# SDG_Leaflet Choropleth Map - light and interactive 
Now that you have followed the tutorial to make a static SDG choropleth map <a href="https://github.com/bricker0/choropleth_map">Choropleth map using SDG data and QGIS here</a> Next, make it interactive and put it online!  
Here, I will show you how to create a global SDG Choropleth Map using Leaflet. Here I explain how to clean your data in QGIS and then I build and modify code from this <a href="https://leafletjs.com/examples/choropleth/"> leaflet tutorial.</a>
See a  <a href="https://bricker0.github.io/leaflet.html"> live working version here</a> 
## Steps
• Pick a Title for your and any relevant notes about the data map - use your favorite text editor<br>
• 	Prepare your data by cleaning your data (only attribute data you need in your webmap) converting your shapefile to geojson in QGIS<br>
•	OPen it in a text editor and save as a .js file	
•	Create a html page and call the Leaflet API to add a map<br>
•	Reference your geojson file on your webmap<br>
•	Stylize your map using CSS<br>

## Start your website with a title for your map
Open your favorite text editor (mine is Sublime) and start a document with the following HTML and change the text to match the dataset you are working with. Save the document as map.html
```

<!DOCTYPE html>
<html lang="en">
<head>
	<base target="_top">
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>SDG Map with Leaflet</title>
	<link rel="shortcut icon" type="image/x-icon" href="docs/images/favicon.ico" />
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>

	<style>
		html, body {
			height: 100%;
			margin: 0;
		}
		.leaflet-container {
			height: 400px;
			width: 600px;
			max-width: 100%;
			max-height: 100%;
		}
	</style>

	<style>#map { width: 800px; height: 500px; }
.info { padding: 6px 8px; font: 14px/16px Arial, Helvetica, sans-serif; background: white; background: rgba(255,255,255,0.8); box-shadow: 0 0 15px rgba(0,0,0,0.2); border-radius: 5px; } .info h4 { margin: 0 0 5px; color: #777; }
.legend { text-align: left; line-height: 18px; color: #555; } .legend i { width: 18px; height: 18px; float: left; margin-right: 8px; opacity: 0.7; }</style>
</head>
<body>
<h2>
<b>SDG 15<b> Protect, restore and promote sustainable use of terrestrial ecosystems, sustainably manage forests, combat desertification, and halt and reverse land degradation and halt biodiversity loss. <br><br> <b>SDG Target 15.1 <b>By 2020, ensure the conservation, restoration and sustainable use of terrestrial and inland freshwater ecosystems and their services, in particular forests, wetlands, mountains and drylands, in line with obligations under international agreements
</h2>
<div id='map'></div>


<script type="text/javascript">

	const map = L.map('map').setView([10, 10], 2);

	const tiles = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
		maxZoom: 19,
		attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
	}).addTo(map);

		map.attributionControl.addAttribution('SDG data &copy; <a href="https://unstats-undesa.opendata.arcgis.com/">UN SDG DataHub</a>');

	//UPDATE legend to match the classes you coded


</script>
</body>
</html>
```

## Prepare your data in QGIS
Open your shapefile with the countries and joined data using QGIS. <br>
Open the attribute table. <br>
Please make sure you write down the goal, target, and indicator title year the data were collected and any other relevant info that you might want to include in the text on your website about the map. <br>
The SDG value – if it is more than 2 decimal places, please convert the value to an integer.  <br>
To do this – when the attribute table is open and editable –click field calculator. <br>
Toggle “Create New Field” and name it SDG_Field<br>
Then cut and paste this expression and replace SDG_Field with the name of the field with your SDG indicator in it. <br>
```
To_int(“SDG_Field”)
```
Then click ok and the new field should generate. <br>
Now we will export and Convert to GeoJSON. <br>
Right-click and the layer <b>Export</b> Save Vector Layer As<br>
Format change to GeoJSON<br>
Name your file and make sure you see where it is being saved.<br>
You only need to keep the attribute with the name of the country and the value – so only toggle the country name and the SDG value field you just created.<br>
Then click okay<br>

##Open the new GeoJSON file in a text editor
On line one, before the open brackets Add the following text
```
var nationData=
```

Next, Finally File Save As and name it and save it with .js extension

Close this file. <br>

## Modify the HTML file
Next open the HTML file found here in your text editor. Find all the places I left UPDATE in the comments. These are the places you need to make changes to reference your documents. You can control f to find those places.
<br>
Good luck!
