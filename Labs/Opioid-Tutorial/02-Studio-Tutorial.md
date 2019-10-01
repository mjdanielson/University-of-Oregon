
<h2 align="center"> Mapping opioid-related prescriptions <br> and overdose rates in the U.S.<h2>


### Part II: Creating custom styles and simple web maps

In this tutorial you will:

- [Create a style](https://www.mapbox.com/help/how-map-design-works/#how-map-styles-work) for a basemap for a dynamic, [interactive web map or app](https://www.mapbox.com/help/how-web-apps-work/)
- [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
- [Add data](https://www.mapbox.com/help/uploads/) to a style
- Make [beautiful custom styles](https://www.mapbox.com/designer-maps/)
- Use [dynamic styling rules](https://blog.mapbox.com/studio-expressions-design-81012e2dab55) (e.g. based on zoom level, based on field in the data etc.)
----------

### **Software Requirements:** 
- [Tippecanoe](https://github.com/mapbox/tippecanoe#installation) 

----------

### **Uploading overdose data to Studio** 

To add the overdose data to a style in Mapbox Studio, you need to upload it to your account. Go to your [**Tilesets**](https://www.mapbox.com/studio/tilesets) [page](https://www.mapbox.com/studio/tilesets) in Mapbox Studio to upload your data.
On your Tilesets page, click the **New tileset** button. Select the zipped shapefile data containing your opioid death rate data and upload it to your account. 




![](https://lh5.googleusercontent.com/CboPoM6tlmD_KI-al25bDrfi3IWeY6tRmV6FB9iNIntVbY3DQuZBLmqA04iXcSeJ1Mtld879e5ga7m9ACmDES2Hg2IH8I0qyGCspLBEduJAJai4pbNEIdk9ilz7m-e5DCkCLaKHY)



When the upload is complete, click on the arrow next to the filename to open its information page.

![A screenshot of a cell phone  Description automatically generated](https://lh3.googleusercontent.com/FHdNMS_iLm68G8uX6X31froWYWyFYh_eTz3oHSEs3vWlZkKe4DYt6JpMe0ZaXWa8X3ilrh0AMa2-eUE9XNOzHTaVOR3GXeMNGHKpxUTG6gUdZf_2T2EaNry_EypJzWRX3Hfi1NIx)

----------

### Inspect the Tile 

When you upload vector data to your Mapbox account, our servers convert it to a [vector tileset](https://docs.mapbox.com/help/glossary/tileset) so it can be rendered quickly and efficiently in the Mapbox Studio style editor and with Mapbox GL JS. The tileset information page shows some useful information about the tileset that was created from your uploaded data.

![A screenshot of a cell phone  Description automatically generated](https://lh4.googleusercontent.com/yu3oKmeeWE-2T0okNRFi8SAZbC-czAkV4wC9AtH3H9cHKTOShM6KeuIfL2aKHVBq7i6QmLjZHXhmwvYwTHBWws_ptgb9bRDIcQ0MNqxdLQhfc_6Tp6HL-kkJTFYKAg6BUBA-FWfX)



- In the center, you can see the properties from the original GeoJSON file: **State name, Region, rate of drug overdose deaths by state, state abbreviation, and number of drug overdose deaths by state,**. The uploaded tileset maintains the properties from the original data file, which you can use when adding style rules for the tileset.
- The **map ID** is the unique identifier for this tileset.
- **Format**, **Type**, **Size**, and **Bounds** provide general information about the tileset.
- **Zoom extent** tells you the zoom levels at which tiles were generated for your uploaded data. Don't worry about this number. Vector tiles are comprised of vector data and can be [overzoomed](https://docs.mapbox.com/help/glossary/overzoom/) and styled up to zoom level 22.

----------

### Create a new style** 

After you've inspected your data, it's time to create a new style so you can put it on the map! Go to your [Styles page](https://www.mapbox.com/studio/). Click the **New style** button. Find the *Basic Template* style and click **Create**.

Excellent! Welcome to the Mapbox Studio style editor. This is where you will create your map style.

![](https://lh3.googleusercontent.com/fMNOioayLpDZr_NH9DSciUX81KkH7uf3ygVV2a4LFX5aBO97QAJtVpsP9kCYBw1v0LTZS4ouQ1Xu13ZtETuYCoACXlzF0gi_kdoygXDmyVZpIm0E9hPeZTetEUj1qJrv-eFBHYui)


Rename the style so that you can find it later. Click into the title field in the upper left side of the screen to change the title from Basic Template to ‘2017 Drug Overdose’.

![](https://lh3.googleusercontent.com/i099mTQPPnxp4NMAZyyO21cIIHzBqjncCHoQGnXJ8GL2zRcZRNgYXp-4cEVbPPpVe2F_ZpztaQT14jMaQwBtpIFuVBILNgwZLxY4Sw5wbN8In49E2pJj8NMR1YnsPLH2CvFi3FHg)


*You can always refer to the* [*Mapbox Studio Manual*](https://www.mapbox.com/studio-manual/reference/styles/) *for more information on getting started.*

----------

### Add a new layer

To add and style the population density data, you will need to add a new layer to the map. At the top of the layer panel, click **+ Add layer**.

![](https://lh5.googleusercontent.com/zw8twmUt_HJ9Pe9Fv5-qc74dyEUMsKSbQ8LSkK2SKFxcsSVY6paqyff0eey13PPD532-1Xn8kPkqKTpdp92eqgwB7PIVNgYmvrZ_5Zpbon1DOzeultSsL6ll-XDcUV8g-WdRzOTO)


The editor is now showing your map in “x-ray mode.” X-ray mode shows all the data in the sources added to the style, regardless of whether there is a layer to style it.
In the *New layer* panel, look in the list of *Data sources* for the Opioid source. Click the tileset and then select the source layer as the source for this new style layer.
The default Basic map view is not centered on the United States. Mapbox Studio recognizes that the data you have uploaded is focused on a different location, so it displays the message *"This tileset isn't available from your map view."* Click **Go to data**, and the map view will refocus on the United States.

![](https://lh4.googleusercontent.com/1WfnJt7yJT1CuE6b9U1AfY0k5OfFKqEZzLa14JUlI44iSoH_ZDk5b6OgZbfTKvh-QX3PPLWRT_WFzE_uTq_lTH4AtezS-pDlu6wX6HDG4nGYPH09wI4ASJbzpcYf-AICHbYXNBYD)


Your new layer will be highlighted on the x-ray map.

![](https://lh3.googleusercontent.com/COE6byA0ie8AGp3fNWp3myK4-1cd5tv3875_CcbXs3O_K91MwES20APIxvkUMvDXWmQ1AFO3njdRu2GEpX9bGVBbUhHsgBOHbYsQ88-CGjfoQDqQr6jzn5f_s_Jgy7KcBbLf7uw_)


Click the **Style** tab and the map will switch back to style mode displaying your new layer. You will see the state data on the map with a default style (black with 100% opacity).

![](https://lh5.googleusercontent.com/w2KAi-79LlGDpnW-vDvsuqqHk-GkiZapt6mEiNyWx9r5o-N6f6p5CIFL8p-wIcvpx2Y-J9-rvW4yonO1vEnD3vLqBukmkO_796a7xXOK-IvFNpMCdPHZ8y4nR3TQKwNf51aoYL8J)


You can rename a layer by clicking on the name of the layer at the top of the panel. Rename your new layer opioid.

----------

### Style the layer

Each layer in Studio can be styled individually by clicking on the name of the layer in the Layer list. There are several layer types to choose from. Each layer type has a unique set of layer properties that can be specified. There are a few options for specifying property values. You can pick values individually, based on a data attribute, based on the zoom level, or the value of another property. For more information on layer types and their styling rules check out this [reference guide](https://docs.mapbox.com/studio-manual/reference/styles/).

![](https://lh5.googleusercontent.com/oAlFehCB1fnEumx5zpP28jfDZzj_cwgh3zSDHbJg3hwouRYVBG7v38xLhxm4O4AheOcm8uVKpLMPgbgtRrbaR-s6_VNO4bS5dmibl0FRaz0ldkKcUfCDURDLk8f9n3-z1rCc5i2V)


On the original CDC map, the data is styled based on the number of age-adjusted rates of drug overdose deaths by each state in 2017:

![](https://lh3.googleusercontent.com/FIOOhzPUgPyHXREzdn3oBfZYsAXWu-Gd13BRG7MeFeDfq3uh-e9GUuCY6haFsHadIDjgjKzvaxkHadX14vAnLYMXHN_Lh73q11iUdCHyFqWDB4Dd_if8F0aRIvcLNh1xe_Pou1xE)

We can use a similar color ramp here. (Or, you can explore [http://colorbrewer2.org/](http://colorbrewer2.org/) to create your own color ramp.)

----------

### Data driven style

In the Mapbox Studio style editor, you can assign a color to each state based on its population density. Click the Style link in the opioid layer. Next, click **Style across data range**.
Under *Choose a numeric data field to interpolate over a range*, select overdose_rate since you want to style each state according to its age-adjusted overdose rate for 2017.

![](https://lh6.googleusercontent.com/KU4ZUN5jEHugMIQtRSZ65FwnQ4SvFDUdG5QZ__5qdZbpFt1f4YHf7EjhZ-QPzj_f5m01DNiMuRLHaRbL1F_qIGf1bxQFJqZ9-XCUtpsKnsVgjABJVbg2IORSGM1bFy-N4W21Hh_-)


The rate of change is set to **Linear**. Click **Edit** and select **Step** instead. Click **Done**. Since you have set the rate of change to step, the colors for each range of density between stops will be uniform.

![](https://lh5.googleusercontent.com/-HBfsdVw-gA_HVAyf_Xf214SqcmOKBYU-p7QW9xtK5ztY9uCgUSe1-S1LLEdfIsNrDdHGGFuqORqEXbXyL_Vn3J_FvQMMSFBAs-QZ17PR9MvR3_ULVys0lRuULX4L1zdsybfHxE_)


Now it's time to start adding stops and colors! You will create several stops to break states up into groups with similar overdose rates. Click on **Edit** in the first overdose rate stop. The first stop is fixed at 8.1, based on the information in the data set you uploaded. Click on it and change the color to #**e9d3d3** (or your own color ramp). Click **Done**.

![](https://lh6.googleusercontent.com/Yk6Ia1r5D9vflPVfM_jEFnUTLaOkH7mKdlFzBKeskLQ5qc4qVTSD9AD7GPr4fOsaiw4r-FDBsMjB30oC0Xp9XW0iN0j9pfmbPaXNZBD_QRjnPoie-aK2D18c6cyFpf0bGIvGWg29)


Change *overdose rate* of the next stop to 11, and change the color to **#f5c0ad**.  Click **Done**.

![](https://lh4.googleusercontent.com/AcaocwkK0SOl4GzMpR_Pf9WeoA8mbdoIEZg20siK4yUsvCF3GSSK_-Vw_KnLJvjP5kQD7hFDb3PuWgo7_ERGQB7N4dfyKdpnje6PuiIH1D3iEjOejGx-7ga-0PM7Bv_6fVWAIlTg)


Click **+ Add another stop**. Change *overdose rate* to 13.5, and change the color to **#f0a184**. Click **Done**.
Create the following additional stops:

- 16:  #cc6f61
- 18.5: #c44936
- 21: #911f0d

(or your own color ramp from [http://colorbrewer2.org/](http://colorbrewer2.org/) or a similar tool)

![](https://lh6.googleusercontent.com/8Fwz7TYSSlfbjik62B5f6pdPM351sixc7BPyLZkPxOroVO3KMbxHY8ksAWukng6RoBNVGcfd4hSTh0nOw3mRrYiOMlfAd663p6TIAh_3DDwPRJmaoSiJCqAb4qAn5vNTDW6nb1of)


As you start adding stops, you will see the map change on the right to reflect the new stops. In this case, all states with an overdose rate between 0-8.1 will be assigned the color #e9d3d3, all states with an overdose rate from 8.1-11 will be assigned the color #f5c0ad, and so on.

![A screenshot of a cell phone  Description automatically generated](https://lh6.googleusercontent.com/dYMOQi5CdAAZcdwQ8YFsPJly-28di6CnpPBxph6kbt4MbQBdJtZeEbSz0-6c61Y9YKA8sTR3Mp_gcFAa7QLr95pDZ_ZCD0mE4brZ0Q1CGKfAJ158hwn8-JtzOdymvIy7EOOl6Mi8)


Give your states a fancy outline style to help your readers distinguish between neighboring states. 

![](https://docs.google.com/a/mapbox.com/drawings/d/sF2Rjb7jVr3ELvqsw4o1bPg/image?w=87&h=6&rev=1&ac=1&parent=1IxPmIUkArMzJRXK1h695z3KTepNyrHOKoFTIer-JiJM)


Change the *1px stroke* style property to #FFF.


----------

### Uploading prescription data to Studio 

Repeat the steps you followed to upload your opioid overdose data to studio with your prescription drug GeoJSON. 
Before adding your data to your style, inspect your tileset. Notice that the zoom extent is set to z5-z10, which means that the data will not be visible below zoom 5. 


![A screenshot of a social media post  Description automatically generated](https://lh4.googleusercontent.com/9Bs_p1V6pdOYe3DsLqhRNay1V0RblNUxUTugNOtGMxP1kDWdFiAhRXnakXKa4QdcYAfmDuuNsowy7wuP0QOqeI5vT0MhEKEJ2JaJKmCedfwiGeTdumBPoqmGuIcCm_o74TjB9lyL)


Let’s find out how this impacts your map by adding your new layer to your existing style and zoom out so that you are able to view the entire contiguous United States. 

![A screenshot of a cell phone  Description automatically generated](https://lh3.googleusercontent.com/0KCuKOmZptxDGSwqnP71AxxlYQKU90lqQYXq20eJPKWFqggcP9C2YfdNI8YVTJ0n0uNUZK0pTPvX6P43QgV5JaOEm0T9VHeWSEkPxERw8Oyj8QQbG2bY6TwVus4LzsXIWfWTt53x)


From this zoom extent, we can’t see the prescription layer that we just added to our map. Try zooming into the state level (around Z5). What do you see? 
When we zoom into the state level, the layer becomes visible. 

![](https://lh3.googleusercontent.com/u7w8Z5jj6kEEdg-83nrsYzQOkIOGe6Ud0kcRupNfnyLKTKo1c-tkn1qlsx6J5UXwiQ2L92BEKKFQFF2Pb6I-Bxct5OvPwUKJZLmXQ5Q7tzd4ZJjgKJ2qikJA6P5ffJia1TAiMczn)

When you upload data to your Mapbox account as a tileset, you may notice that your data has been simplified or that it is not rendered at all zoom levels. The Mapbox Streets source data is also limited to specific zoom levels. For context, the opioid state data has a zoom extent of z3-z8.
**Why this happens:** Data simplification and zoom level limiting make your map load faster and limit the file size of the resulting tileset.
In order to create our map, we need to correct the zoom extent for this file so that we can view our prescription rate data when we are zoomed out to the contiguous US. 
Before we edit our GeoJSON, go ahead and delete the prescription layer from your style and delete the prescription tileset from your Mapbox account.

----------

### Adjust tileset zoom extent

This [guide](https://docs.mapbox.com/help/troubleshooting/adjust-tileset-zoom-extent/#transform-data-with-tippecanoe) provides an explanation for why this happens. It also describes some techniques for manually adjusting the zoom extent of your tilesets and for adding your own sources with custom zoom levels.
Before changing the zoom level, you will need to install [tippecanoe](https://docs.mapbox.com/help/troubleshooting/large-data-tippecanoe). 
Once you have tippecanoe installed, you can run the following command in your terminal/command prompt to change the zoom levels of your prescription data to match the zoom levels of your opioid death rate data (remember replace the input file path and name with your file path and name): 
tippecanoe -o prescription.mbtiles -Z 3 -z 8 user/desktop/inputfile.geojson

Check your documents folder for your output file. Once you’ve located your output data, upload the new mbtile to your account and add it to your style. You should now be able to view your prescriptions layer when zoomed out to the contiguous US!
![A screen shot of a computer  Description automatically generated](https://lh5.googleusercontent.com/54C49eQmslgtYQFP7Evu6jjpKw633XpmTkKGtlZG5W-AzuKEq5DbLJW8En74xi1pL9UDUXd041Rlb4VIB7bSZdjHBAOTibxC4yIPGG_x980m06bG3WRG5pjxAbHyoRHJm1phji2p)


----------

### Style your layer

Below is the CDC representation of prescribing rates in the US by county: 

![A close up of a map  Description automatically generated](https://lh3.googleusercontent.com/MgRi6t82oIC0ah4A180CEkDmrcBK8Q1ViLht0mF8y0PL4z22p7M5lW-4BjI1yupNamOG3GUlbql7Qqo-dLOImYgXMc-jBFeTC-3e0Iz0iYbDCQr99tFeoGBmvgHwIqXWowqekdt8)


Use the same binning techniques as seen on the CDC website to style your data, but feel free to change the colors! If you want to recreate the color scheme from the CDC map, try using [HTML color picker.](https://imagecolorpicker.com/) 
**Note: Remember that we set our ‘Null’ or missing data to 1000.** 

![A screenshot of a cell phone  Description automatically generated](https://lh4.googleusercontent.com/x5XlQItQjhFr1xoUnlhIRLTbkhFpfkSjmW24RWX02bbNDuJx5U3SReiC_vJ3KvkEiqS0CK9wcKcYvuvXBf7lN_A5sg8Q0het75D8ANBkPLsHgmG9P4UWfjY4OzYd9DQeYqYe-4TA)

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


