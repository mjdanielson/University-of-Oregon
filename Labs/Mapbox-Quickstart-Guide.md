## Mapbox Quick Start Guide

This step-by-step guide will quickly get you started on Mapbox basics, including setting up a Leaflet map, working with markers, polylines and popups, and dealing with events.

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

Next, we’ll initialize the map and set its view to our chosen geographical coordinates and a zoom level:

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
<img src= "https://media.giphy.com/media/ely3apij36BJhoZ234/giphy.gif">
</p>

### Markers, circles and polygons 

