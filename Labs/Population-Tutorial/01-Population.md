<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">


<h2 align="center"> Mapping renters vs owners in Portland </h2>

The US Census makes owner/renter information readily available for census block geometries, in this lab series we are going to view the owner/renter information in different ways: 1) by mapping the per-person level information and 2) by viewing the relative incidenec of owners to renters using a choropeth map. For this first exercise, we will be creating a point map that displays the each individual renter and owner in Portland by block group. 

### In this tutorial you will:

- [Create a style](https://www.mapbox.com/help/how-map-design-works/#how-map-styles-work) for a basemap for a dynamic, [interactive web map or app](https://www.mapbox.com/help/how-web-apps-work/)
- [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
- [Add data](https://www.mapbox.com/help/uploads/) to a style
- Make [beautiful custom styles](https://www.mapbox.com/designer-maps/)
- Use [dynamic styling rules](https://blog.mapbox.com/studio-expressions-design-81012e2dab55) (e.g. based on zoom level, based on field in the data etc.)

----------

### Data

- [Portland renters by block group 2017](https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Data/Renters.mbtiles) - [Source: US Census](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml) 

- [Portland homeowners by block group 2017](https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Data/Owners.mbtiles) - [Source: US Census](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml) 

----------

### Uploading data to Studio

To add the renter data to a style in Mapbox Studio, you need to upload it to your account. Go to your [**Tilesets**](https://www.mapbox.com/studio/tilesets) [page](https://www.mapbox.com/studio/tilesets) in Mapbox Studio to upload your data.

On your Tilesets page, click the **New tileset** button. Select the zipped shapefile data containing your overdose data and upload it to your account. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/tilesets.png">
  </p>


<br>
Next, upload your owner data to Mapbox. 

----------

### Create a new style** 

After you've uploaded your data, it's time to create a new style so you can put it on the map! Go to your [Styles page](https://www.mapbox.com/studio/). Click the **New style** button. Find the *Dark Template* style and click **Create**.

Excellent! Welcome to the Mapbox Studio style editor. This is where you will create your map style.

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Dark_style.png">
  </p>

Rename the style so that you can find it later. Click into the title field in the upper left side of the screen to change the title from Dark Template to ‘Renters vs Owners’.

<p align="center">
  <img src"https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Name_Change-Generic.gif">
  </p>
  

*You can always refer to the* [*Mapbox Studio Manual*](https://www.mapbox.com/studio-manual/reference/styles/) *for more information on getting started.*

----------

### Add a new layer

To add and style your data, you will need to add a **new layer** to the map. At the top of the layer panel, click **+ Add layer** and select your **renter** layer that you just uploaded as a tileset. 


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/zray.png">
  </p>


The editor is now showing your map in “x-ray mode.” X-ray mode shows all the data in the sources added to the style, regardless of whether there is a layer to style it.


In the *New layer* panel, look in the list of *Data sources* for the **owner** source. Click the tileset and then select the source layer as the source for this new style layer.

The default Basic map view is not centered on the United States. Mapbox Studio recognizes that the data you have uploaded is focused on a different location, so it displays the message *"This tileset isn't available from your map view."* Click **Go to data**, and the map view will refocus on the United States.


Your new layer will be highlighted on the x-ray map.


Click the **Style** tab and the map will switch back to style mode displaying your new layer. You will see the state data on the map with a default style (black with 100% opacity).


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Style-Layers.png"
       </p>


You can rename a layer by clicking on the name of the layer at the top of the panel. 

----------

### Style the layer

Each layer in Studio can be styled individually by clicking on the name of the layer in the Layer list. There are several layer types to choose from. Each layer type has a unique set of layer properties that can be specified. There are a few options for specifying property values. You can pick values individually, based on a data attribute, based on the zoom level, or the value of another property. For more information on layer types and their styling rules check out this [reference guide](https://docs.mapbox.com/studio-manual/reference/styles/).


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/style_layer.png">
  </p>


On the original CDC map, the data is styled based on the number of age-adjusted rates of drug overdose deaths by each state in 2017:

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/cdc.png">
  </p>
  
  
  
We can use a similar color ramp here. (Or, you can explore [http://colorbrewer2.org/](http://colorbrewer2.org/) to create your own color ramp.)

----------

### Data driven style

In the Mapbox Studio style editor, you can assign a color to each state based on its population density. Click the Style link in the opioid layer. Next, click **Style across data range**.

Under *Choose a numeric data field to interpolate over a range*, select overdose_rate since you want to style each state according to its age-adjusted overdose rate for 2017.


The rate of change is set to **Linear**. Click **Edit** and select **Step** instead. Click **Done**. Since you have set the rate of change to step, the colors for each range of density between stops will be uniform.


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/Screen%20Shot%202019-10-02%20at%209.21.19%20AM.png">
  </p>



Now it's time to start adding stops and colors! You will create several stops to break states up into groups with similar overdose rates. Click on **Edit** in the first overdose rate stop. The first stop is fixed at 8.1, based on the information in the data set you uploaded. Click on it and change the color to #**e9d3d3** (or your own color ramp). Click **Done**.

Change *overdose rate* of the next stop to 11, and change the color to **#f5c0ad**.  Click **Done**.

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/choroplet2.gif">
  </p>
  
  

Click **+ Add another stop**. Change *overdose rate* to 13.5, and change the color to **#f0a184**. Click **Done**.
Create the following additional stops:


- 16:  #cc6f61
- 18.5: #c44936
- 21: #911f0d


(or your own color ramp from [http://colorbrewer2.org/](http://colorbrewer2.org/) or a similar tool)


As you start adding stops, you will see the map change on the right to reflect the new stops. In this case, all states with an overdose rate between 0-8.1 will be assigned the color #e9d3d3, all states with an overdose rate from 8.1-11 will be assigned the color #f5c0ad, and so on.

Give your states a fancy outline style to help your readers distinguish between neighboring states. 



<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/Screen%20Shot%202019-10-02%20at%209.29.10%20AM.png">
  </p>



Change the *1px stroke* style property to #FFF.


### Style your prescription data layer

Below is the CDC representation of prescribing rates in the US by county: 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/cdc2.png">
  </p>


Use the same binning techniques as seen on the CDC website to style your data using the prescription rate field, but feel free to change the colors! Remember to set the stroke color to #ffff and to change the rate of change to **step**. Set the opacity for this layer to 0.75

If you want to recreate the color scheme from the CDC map, try using [HTML color picker.](https://imagecolorpicker.com/) or use the table below:

| Step Value | Color   |
|------------|---------|
| 0          | #FFE9BD |
| 57.2       | #FF8A73 |
| 82.4       | #E1371  |
| 112.5      | #650511 |
| 1000       | #FFFFF  |

**Note: Remember that we set our ‘Null’ or missing data to 1000.**


----------


### Reorder your layers**


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/Screen%20Shot%202019-10-02%20at%2011.00.12%20AM.png"
       </p>
  

One of the coolest things about the Mapbox Studio style editor is that you can reorder any of the elements of the map. Notice in the photo above that we moved the water features to the top of the layer list. Additionally, we moved the state overdose data to appear above the prescription rate layer. 

To make your map match the example above, try moving your **water** data to the top of your layer list.  


Next, move the **state** labels below the water data. 


Lastly, move the **overdose** date below the state data but above the **prescription** data. 


To make the boundaries between states more visible, you can move the **admin-state-province** layer above the overdose layer in the layer list. 



----------


### Style by zoom level


We have successfully added and styled both of our data sets, but at this point we can only view the overdose rates by state. In order to see the prescription drug rates when zoomed into the state level we will need to change the visibility by zoom extent. 

Select the **overdose** data layer (this should be above your prescription drug layer) and select the Opacity property. 
Select ‘style across a zoom range’ and add a step at zoom level 5 and zoom level 6. Make sure the rate of change is set to linear.  

Change the opacity at zoom level 6 to equal ‘0’ and set the opacity at zoom level 5 to ‘1’. Save your changes.
You should now be able to view your prescription drug data when zoomed in to the state level (~ zoom level 5.5). 


<p align='center'>
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/opacity.gif">
</p>


----------


### Publish the style


Now that you've got your map looking good, it's time to publish! Click the **Publish style** button at the top of the toolbar on the right side of the screen, then click **Publish** again on the next prompt.

<p align='center'>
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/publish_styel.png">
</p>

Hooray! Your style is now published! If you go back to your Styles page, you will see your new style at the top of the list.
You can use your ‘Share URL’ to open your style in a new browser tab and share it with collaborators for review.

----------

### Next steps


Head to [part 2](https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/02-Interactivity.md) to learn how add interactive elements to your map and publish it to the web with Mapbox GL JS. 



