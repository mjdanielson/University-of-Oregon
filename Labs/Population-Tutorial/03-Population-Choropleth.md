<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">


<h2 align="center"> Mapping renters vs owners in Portland </h2>
<h3 align="center"> Part III: Creating a comparitive choropleth map </h3>

The US Census makes owner/renter information readily available for census block geometries, in this lab series we are going to view the owner/renter information in different ways: 

1) Mapping the per-person level information, and 
2) Viewing the relative incidence of owners to renters using a choropeth map. 

For this first exercise, we will be creating two choropleth maps in order to display and compare the percentage of owners and renters in Portland, Oregon. 

### In this tutorial you will:

- [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
- [Add data](https://www.mapbox.com/help/uploads/) to a style
- Use [dynamic styling rules](https://blog.mapbox.com/studio-expressions-design-81012e2dab55) (e.g. based on zoom level, based on field in the data etc.)
- Learn about GL-JS and adding interactivity
- Call on map layers using GL-JS
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

### Uploading data to Studio

To add the percentage of renters vs owners data to a style in Mapbox Studio, you need to upload it to your account. Go to your [**Tilesets**](https://www.mapbox.com/studio/tilesets) [page](https://www.mapbox.com/studio/tilesets) in Mapbox Studio to upload your data.

On your Tilesets page, click the **New tileset** button. Select the zipped shapefile data containing your overdose data and upload it to your account. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/tilesets.png">
  </p>


<br>

In the last few tutorials we used Studio to dynamically style all of our layers. For this tutorial, we will be using one of Mapbox's custom styles and writing our styling rules directly in our code. 

----------

### Initializing the map!


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map in JSFiddle. 

```
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







