<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">


<h2 align="center"> Mapping opioid-related prescriptions <br> and overdose rates in the U.S.<h2>


### Part II: Creating custom styles and simple web maps

In this tutorial you will:

- [Create a style](https://www.mapbox.com/help/how-map-design-works/#how-map-styles-work) for a basemap for a dynamic, [interactive web map or app](https://www.mapbox.com/help/how-web-apps-work/)
- [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
- [Add data](https://www.mapbox.com/help/uploads/) to a style
- Make [beautiful custom styles](https://www.mapbox.com/designer-maps/)
- Use [dynamic styling rules](https://blog.mapbox.com/studio-expressions-design-81012e2dab55) (e.g. based on zoom level, based on field in the data etc.)

----------

### **Uploading data to Studio** 

To add the overdose data to a style in Mapbox Studio, you need to upload it to your account. Go to your [**Tilesets**](https://www.mapbox.com/studio/tilesets) [page](https://www.mapbox.com/studio/tilesets) in Mapbox Studio to upload your data.

On your Tilesets page, click the **New tileset** button. Select the zipped shapefile data containing your overdose data and upload it to your account. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/tilesets.png">
  </p>

Next, upload your prescription drug county-level data. 

----------

### Create a new style** 

After you've uploaded your data, it's time to create a new style so you can put it on the map! Go to your [Styles page](https://www.mapbox.com/studio/). Click the **New style** button. Find the *Basic Template* style and click **Create**.

Excellent! Welcome to the Mapbox Studio style editor. This is where you will create your map style.

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/basic_style.png">
  </p>

Rename the style so that you can find it later. Click into the title field in the upper left side of the screen to change the title from Basic Template to ‘2017 Overdose and Opioid Data’.

<p align="center">
  <img src"https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/name-change.gif">
  </p>
  

*You can always refer to the* [*Mapbox Studio Manual*](https://www.mapbox.com/studio-manual/reference/styles/) *for more information on getting started.*

----------

### Add a new layer

To add and style your data, you will need to add a **new layer** to the map. At the top of the layer panel, click **+ Add layer** and select your overdose rate by state data layer that you just uploaded as a tileset. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/add-layer.png">
  </p>


The editor is now showing your map in “x-ray mode.” X-ray mode shows all the data in the sources added to the style, regardless of whether there is a layer to style it.

In the *New layer* panel, look in the list of *Data sources* for the Opioid source. Click the tileset and then select the source layer as the source for this new style layer.

The default Basic map view is not centered on the United States. Mapbox Studio recognizes that the data you have uploaded is focused on a different location, so it displays the message *"This tileset isn't available from your map view."* Click **Go to data**, and the map view will refocus on the United States.


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/xray1.png">
  </p>

Your new layer will be highlighted on the x-ray map.

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/xray2.png">
  </p>

Click the **Style** tab and the map will switch back to style mode displaying your new layer. You will see the state data on the map with a default style (black with 100% opacity).


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/Screen%20Shot%202019-10-02%20at%209.08.30%20AM.png"
       </p>


You can rename a layer by clicking on the name of the layer at the top of the panel. Rename your new layer overdose data. Next, add your prescription data to the map and rename the layer to **opioid prescriptions**.

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


Use the same binning techniques as seen on the CDC website to style your data using the prescription rate field, but feel free to change the colors! Remember to set the stroke color to #ffff and to change the rate of change to **step**. 

If you want to recreate the color scheme from the CDC map, try using [HTML color picker.](https://imagecolorpicker.com/) or use the table below:

| Step Value | Color   |
|------------|---------|
| 0          | #FFE9BD |
| 57.2       | #FF8A73 |
| 82.4       | #E1371  |
| 112.5      | #650511 |
| 1000       | #FFFFF  |


<h3 align="center"> Note: Remember that we set our ‘Null’ or missing data to 1000.</h3>

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/prescription_opacity.png">
  </p>

----------

### Reorder your layers**

![A close up of a map  Description automatically generated](https://lh3.googleusercontent.com/EYedsDStdVzBf9hQZvB4U5645vNrGvw83E5z0aHftoL2MfHc8GYj_LqvKTzev7yDKAOn5V_giPw4JVlcadNQEbFN5ThbumE1jp_jyX7DZ1NUI4-BQ4kejdzfO-GDZtSdEjpc95bE)


One of the coolest things about the Mapbox Studio style editor is that you can reorder any of the elements of the map. Notice that we moved the water features to the top of the layer list. Additionally, we moved the state opioid data to appear above the prescription rate layer. 
Try moving your opioid data to the top of your layer list.  Hover over your opioid layer. Click the 

![](https://lh3.googleusercontent.com/evSCyWB1rWioNKEJB3_m5ziToWhqli4kS9G6QIq0XhvS17eI4ZGtjLq7aXsF1dWpeULDtgosictjdR4m7UkZEqGhRGjoSsBpSJ6dQCRRnWAm0nlBZi20oA57LmRUeaZEUU9tlp53)


next to the layer's name in the layer list on the far left and drag your layer below the place labels.

![](https://lh4.googleusercontent.com/B5H2M_qFAy7f-CttpCQlTig7i1LF3d9GggpChMDA1TviTQjMGTzaUdZ4CPMBg0J_Gp5iDNbXt7N4T4LyOOad84kwPmTF2VBm9NxUpgIyP70PqrIMTULoQZp4Od_kmp_O-7Rz2jFj)


Now that labels are on top of the overdose rate data, city labels are popping out above the more important state labels. To turn off the city labels, click on 

![](https://lh5.googleusercontent.com/zugpLdTGXb1tckpslwN9BjK6zsyHmhgdpKV4PqoBn9xxHkn4clFQJCkjsS0EiUxYebwTJiwwE5dGCOQCMbslj9gvjuSfUrCkBC4NV5mLzxOjc5H6HZHR1LteiNXJ1ADy8J0cE8fO)


and type *place*. This will return all the city label layers. Select multiple layers at once by holding down command (Mac) or CTRL (Windows) while clicking on these layers. Next, click the 

![](https://lh4.googleusercontent.com/8-QwmNQlsK8p7H1wUbmFSjGCYURi21oBH8-RFNe7FPFqXeVZAEddai5xojYQWqL3y7JVCXjO6qeNabdHv2RwKocA7ErRLY4y6iKMkcBY2VlTjAnhWt1on2IZS2sb9fyFPwfyGMXl)


button at the top of the layers pane to turn off these layers' visibility.

![](https://lh5.googleusercontent.com/VNu1UD69zhjUPj_LERpjUh9mWBVosuQP4icsnmb6KIZycQ4es8sYgeklNpbcvlQ20q3ov6aTHN3Ap9e8I9FCdt4sf6HiQvyhaSabb7iYQ8zC-hcgtGiixWYb7NVPEKqMiuc6Cg2C)


To make the boundaries between states more visible, you can move the **admin-state-province** layer above the opioid layer in the layer list. You may also want to move the **water** layer.

![](https://lh6.googleusercontent.com/mfY22ki9FiO5i8fQVd7sEFPBlR34akvQ5g-6erguE0vQYkjwa3Wfp-nPz4FrgM0c2xki-BDQ2fm7oVDCmf_7sU1wCOt0IuQLBlEShbYnOhiCL-bID9V4D1Kz_EFZ8HvH1k_Y-jHw)


----------

### Style by zoom level

![A screenshot of a cell phone  Description automatically generated](https://lh6.googleusercontent.com/BvLC_mN98P42jhi1Xs7Wlckgn-DmJHBQM6mISH2tWekyAWXYOfdY6cLn0tv5NySKPuHBYabwym4bQmPhTHkQ7IZfBV6ZT_T_b9xqzcCe9lbpB3wemrJdc3YLlV_IREXQg14Xh5SK)

![](https://docs.google.com/a/mapbox.com/drawings/d/saGj0J-GKgbo6reIelcr97w/image?w=50&h=75&rev=1&ac=1&parent=1IxPmIUkArMzJRXK1h695z3KTepNyrHOKoFTIer-JiJM)


We have successfully added and styled both of our data sets, but at this point we can only view the overdose rates by state. In order to see the prescription drug rates when zoomed into the state level we will need to change the visibility by zoom extent. 

Select the opioid data layer (this should be above your prescription drug layer) and select the Opacity property. 
Select ‘style across a zoom range’ and add a step at zoom level 5 and zoom level 6. Make sure the rate of change is set to linear.  

Change the opacity at zoom level 6 to equal ‘0’ and set the opacity at zoom level 5 to ‘1’. Save your changes.
You should now be able to view your prescription drug data when zoomed in to the state level (~ zoom level 5.5). 

----------

### Publish the style

Now that you've got your map looking good, it's time to publish! Click the **Publish style** button at the top of the toolbar on the right side of the screen, then click **Publish** again on the next prompt.

![](https://lh6.googleusercontent.com/nK_EaEb2L_iwKCNoUZ_tlL9d-CrewNxRy2OIivNtiC_z7EuCUx1H6fqljoSFEvosd9jr9L5jvwC2_OS-R4iqO_2iDnPZ_3nr_XqyXbTchp9Vhg5NKt9LtAhLCdwaIlkDKZ-AWdk_)



Hooray! Your style is now published! If you go back to your Styles page, you will see your new style at the top of the list.
You can use your ‘Share URL’ to open your style in a new browser tab and share it with collaborators for review.

----------
### Next steps

Head to [part 2](https://docs.google.com/document/d/1yhHejuKunNx8YsYxwGc5HEeE8y0bMW-QxWaEK9-G8QQ/edit#heading=h.cn5mabarfy4y) to learn how add interactive elements to your map and publish it to the web with Mapbox GL JS.
Or, try:

- Exporting your style for a [print map](https://docs.mapbox.com/help/how-mapbox-works/static-maps/)
- Using your style as a basemap in [QGIS, Tableau, or other tools](https://www.mapbox.com/help/mapbox-arcgis-qgis/)


