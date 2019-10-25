<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">


<h2 align="center"> Mapping renters vs owners in Portland </h2>
<h3 align="center"> Part III: Creating a comparitive choropleth map </h3>

The US Census makes owner/renter information readily available for census block geometries, in this lab series we are going to view the owner/renter information in different ways: 

1) Mapping the per-person level information, and 
2) Viewing the relative incidence of owners to renters using a choropeth map. 

For this first exercise, we will be creating two choropleth maps that display 1) the percentage of owners, and 2) the percentage of renters in Portland, Oregon. 

### In this tutorial you will:

- [Add data](https://www.mapbox.com/help/uploads/) to Mapbox
- Call on map layers using GL-JS
- Learn about GL-JS and adding interactivity, styling your layers 
- Learn additional tools and tricks such as how to [swipe between maps](https://docs.mapbox.com/mapbox-gl-js/example/mapbox-gl-compare/)

----------

### Get started

To create a web map, you'll need to have some familiarity with HTML, CSS, and JavaScript. If you are new to web maps, explore our [tutorials](https://docs.mapbox.com/help/tutorials/) and [documentation](https://docs.mapbox.com/help/how-mapbox-works/web-apps/) to help you get started.
Here’s what you’ll need to get started:

- [Github account](https://github.com/join)
- [JSFiddle Text Editor](https://jsfiddle.net/)

*This is a very beginner intro by a non-developer - there’s a lot more to learn about developing more complex web apps and sites, but we’re focusing just on a simple web map. For more complex projects and teams, you’ll want to learn more about version control and using Github properly, with pull requests etc.*

----------

### Data

- [Percentage of renters, owners and total population by block group 2017](https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Data/Owner-Renter-Pop.geojson) - [Source: US Census](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml) 


----------

### Upload data as a tileset to Mapbox

To add the percentage of renters vs owners data to Mapbox as a tileset, you need to upload it to your account. Go to your [**Tilesets**](https://studio.mapbox.com/tilesets/) page in Mapbox Studio to upload your data.

On your Tilesets page, click the **New tileset** button. Select the geojson data containing your renters and owners data and upload it to your account. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/tilesets.png">
  </p>


<br>

In the last few tutorials we used Studio to dynamically style all of our layers. For this tutorial, we will be using one of Mapbox's custom styles and writing our styling rules directly in our code. 

----------

### Initializing the map!


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map in JSFiddle. 

```HTML
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title>Swipe between maps</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.1/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.1/mapbox-gl.css' rel='stylesheet' />
    <style>
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
    </style>
</head>
<body>

<style>
body {
    overflow: hidden;
}

body * {
   -webkit-touch-callout: none;
     -webkit-user-select: none;
        -moz-user-select: none;
         -ms-user-select: none;
             user-select: none;
}


.map {
    position: absolute;
    top: 0;
    bottom: 0;
    width: 100%;
}
</style>

<script src='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.js'></script>
<link rel='stylesheet' href='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.css' type='text/css' />

<div id='map' class='map'></div> 

<script>
mapboxgl.accessToken = 'YOUR ACCESS TOKEN';
var map = new mapboxgl.Map({
    container: 'map',
    style: 'mapbox://styles/mapbox/dark-v10', //Mapbox dark style 
    center: [0, 0], // change the long/lat coordinates to -122.67745971679688, 45.52751668442124],
    zoom: 0 // change the zoom level to 10 
});

</script>

</body>
</html>
```


Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/)in the section that says "ACCESS TOKEN GOES HERE" (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).

----------

### Changing the map location and zoom level 

Now that we’ve initialized the webmap, let’s try to make some changes to our code. Currently, your map is zoomed out to see the whole world when it loads. We need to change the location and the zoom level so that we can only view Portland, Oregon. 

1. Locate the line of code that is telling the map where to center the view.
2. Try changing the center location to the center of the US by picking a new coordinate using [http://geojson.io/](http://geojson.io/#map=2/20.0/0.0).
3. Change the coordinates in your code and run your changes.
4. Change the zoom level to 10. 
5. Click ‘Run’ to see the changes to your map. 


----------

### The load event

What is a callback?

Initializing the map on the page does more than create a container in the map div. It also tells the browser to request the Mapbox Studio style. This can take variable amounts of time depending on how quickly the Mapbox server can respond to that request, and everything else you're going to add in the code relies on that style being loaded onto the map. As such, it's important to make sure the style is loaded before any more code is executed.

Fortunately, the map object can tell your browser about certain events that occur when the map's state changes. One of these events is load, which is emitted when the style has been loaded onto the map. Through the map.on method, you can make sure that none of the rest of your code is executed until that event occurs by placing it in a callback function that is called when the load event occurs.

To make sure the rest of the code can execute, it needs to live in a callback function that is executed when the map is finished loading.

```
map.on('load', function() {
  // the rest of the code will go in here
});

```

Next, we will add our owner and renter data layer to the map using map.addLayer(). Remember that this goes inside of the load function. 


```
       map.addLayer({
         id: 'Owner Data',
         type: "fill",
         source: {
           type: 'vector',
           url: 'mapbox://YOUR URL' //input your tileset url
         },
           'source-layer': 'YOUR SOURCE LAYER NAME, //input your source layer name
         paint: {
           'fill-color': '#cb1515',
         }

       });

```

Beofore you hit 'run', you will need to make some changes to this code. Hit **run** to see your changes! You should see your vector layer on your map. 


<p align='center'>
  <img src="">
  </p>
  
### Data driven styling 

You can assign a color to each block group based on its field and variables. For our first map, we want to create a choropleth map that displays the percentage of the Portland population that owns a home. In order to style by homeownership, you will need to change the 'fill-color' parameter of the layer you just added to your map. 

Replace '#cb1515' with the following: 

```
[
   "step",
   ["get", "Own"],
   "hsl(225, 100%, 97%)",
   16.81,
   "hsl(203, 47%, 82%)",
   22.338,
   "hsl(202, 57%, 63%)",
   27.32,
   "#3182bd",
   31.942,
    "hsl(210, 90%, 32%)"
   ],
   "fill-opacity": 0.7
                
 ```
 
This code is very similar to the process we used in Studio. We are filtering the data from our layer by the data range found in the 'Own' field. Each of the five steps is assigned a color and the fill-opacity is set to 0.7. 



