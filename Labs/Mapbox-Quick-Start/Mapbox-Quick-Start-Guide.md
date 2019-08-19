## Mapbox Quick Start Guide

This step-by-step guide will quickly get you started on Mapbox basics, including setting up a Leaflet map and working with markers, circles and popups!

### Preparing your page

Before writing any code for the map, you need to do the following preparation steps on your page:

* Include Mapbox JavaScript file:

```
<script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.js'></script>
    
```

* Include Mapbox CSS file __after__ Mapbox’s JavaScript:

```
<link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.css' rel='stylesheet' />
```

Put a div element with a certain id where you want your map to be:

```
<div id='map'></div>

```

You will also want to apply some CSS to visualize what the layout looks like. This is particularly important for the map div, which won't show up on the page until you give it a height:

```
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
```

Now you’re ready to initialize the map and do some stuff with it.

### Setting up the map

Let’s create a map of the centered on Portland with the beautiful Mapbox Streets style. 

The first thing you'll need to do is add your access token. Without this, the rest of the code will not work. Note: all the following code should be between script tags.:

```
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
```

Next, we’ll initialize the map and set its view to our chosen geographical coordinates and a zoom level.

<p align="center">
    <img src= "https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Mapbox-Quick-Start/Images/01_Portland.png">
  </p>

```
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
    center: [-122.67539978027342, 45.52414929707939], // starting position [lng, lat] 
    zoom: 11 // starting zoom 
});
```

That’s it! You have a working Mapbox map now.

<p align = "center">
<img src = "https://media.giphy.com/media/xT0xezQGU5xCDJuCPe/giphy.gif">
</p>

### Markers, circles and polygons 

Besides a basemap, you can easily add other things to your map, including markers, polylines, polygons, circles, and popups.

Let’s [add a marker](https://docs.mapbox.com/mapbox-gl-js/api/#marker):

```
var marker = new mapboxgl.Marker()
  .setLngLat([-122.67539978027342, 45.52414929707939])
  .addTo(map);
```

<p align = "center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Mapbox-Quick-Start/Images/Portland_Marker.png">
 </p>

Now let's [define a circle](https://www.npmjs.com/package/mapbox-gl-circle) using center coordinates and radius (in meters). For bonus points, we will enable interactive editing via draggable center/radius handles. 

<p align="center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Mapbox-Quick-Start/Images/Circle.gif">
 </p>

In order to add a circle to your map you will need to include mapbox-gl-circle.min.js in the <head> of your HTML file to add the MapboxCircle object to global scope:

```
<script src='https://npmcdn.com/mapbox-gl-circle/dist/mapbox-gl-circle.min.js'></script>
```

Next, let's create our circle by defining the central coordinates, the radius size and the fill color. 

```
var myCircle = new MapboxCircle({lat: 45.5, lng: -122.7}, 1000, {
        editable: true,
        minRadius: 1500,
        fillColor: '#29AB87'
    }).addTo(map);
    
```

### Working with popups

<p align = "center">
	<img src ="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Mapbox-Quick-Start/Images/Popup.png">
</p>

Popups are usually used when you want to attach some information to a particular object on a map. In Mapbox, you can [add a popup](https://docs.mapbox.com/mapbox-gl-js/api/#popup) to your features with only a few lines of code! 

First, you will need to initialize your pop-up variable. Make sure this variable is above your marker variable: 

```
var popup = new mapboxgl.Popup({ offset: 25 })
.setText('Hello World. Welcome to Portland!');
```

Next add the .setPopup function to your marker variable:

```
var marker = new mapboxgl.Marker()
		.setLngLat([-122.67539978027342, 45.52414929707939])
    .setPopup(popup)
    .addTo(map);
```

You can also use popups as layers (when you need something more than attaching a popup to an object):


```
var popup2 = new mapboxgl.Popup({closeOnClick: false})
.setLngLat([-122.64, 45.5])
.setHTML('<h1>Hi Portland!</h1>')
.addTo(map);
```

### Dealing with events

Map (and some other classes) emit events in response to user interactions or changes in state. Evented is the interface used to bind and unbind listeners for these events.

<p align = "center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Mapbox-Quick-Start/Images/event.gif">
	</p>

First, let's add some CSS to the body of our map to create an event text box. Add the following code just after the opening <body> tag: 

```
<style type='text/css'>
#info {
display: block;
position: relative;
margin: 0px auto;
width: 70%;
padding: 10px;
border: none;
border-radius: 3px;
font-size: 12px;
text-align: center;
color: #222;
background: #fff;
}
</style>
```

Next, add ```<pre id='info'></pre> ``` just after your map divider. 

Next, let's add our funciton. The first argument of the listener function is an event object — it contains useful information about the event that happened. For example, mapmouse event object (e in the example below) has latlng property which is a location at which the movement occurred.

```
map.on('mousemove', function (e) {
document.getElementById('info').innerHTML =
// e.point is the x, y coordinates of the mousemove event relative
// to the top-left corner of the map
JSON.stringify(e.point) + '<br />' +
// e.lngLat is the longitude, latitude geographical position of the event
JSON.stringify(e.lngLat.wrap());
});
```
