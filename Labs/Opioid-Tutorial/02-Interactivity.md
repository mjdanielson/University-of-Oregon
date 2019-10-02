<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">

<h2 align="center"> Mapping opioid-related prescriptions and overdose rates in the U.S. </h2>
<h3 align="center"> Part II: Adding interactivity to web maps through GL-JS </h3>

<br></br>
### In this tutorial you will:


- Publish a map style without adding layers
- Learn about GL-JS and adding interactivity
- Call on map layers using GL-JS
- Learn additional tools and tricks for creating compelling maps

A few additional resources for Mapbox GL JS:

- [https://www.mapbox.com/mapbox-gl-js/api/](https://www.mapbox.com/mapbox-gl-js/api/)
- [https://www.mapbox.com/mapbox-gl-js/examples](https://www.mapbox.com/mapbox-gl-js/examples) 
- Example finished maps that use Mapbox GL JS for more design control and interactivity: [https://native-land.ca/](https://native-land.ca/) or [https://www.mapbox.com/amnesty/](https://www.mapbox.com/amnesty/) or [https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html](https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html) 
- This exercise is based on: [https://docs.mapbox.com/help/tutorials/choropleth-studio-gl-pt-2/](https://docs.mapbox.com/help/tutorials/choropleth-studio-gl-pt-2/)

<br></br>
----------
<br></br>
### Get started

To create a web map, you'll need to have some familiarity with HTML, CSS, and JavaScript. If you are new to web maps, explore our [tutorials](https://docs.mapbox.com/help/tutorials/) and [documentation](https://docs.mapbox.com/help/how-mapbox-works/web-apps/) to help you get started.
Here’s what you’ll need to get started:

- [Github account](https://github.com/join)
- [JSFiddle Text Editor](https://jsfiddle.net/)

*This is a very beginner intro by a non-developer - there’s a lot more to learn about developing more complex web apps and sites, but we’re focusing just on a simple web map. For more complex projects and teams, you’ll want to learn more about version control and using Github properly, with pull requests etc.*

----------
<br></br>
### Part 1. Orientation to your tools


For this lesson, we will be using a program called JSFiddle. You can sign up for a free acount at: [https://jsfiddle.net/](https://jsfiddle.net/)
JSFiddle is a simple tool for building and testing code for web development. We recommend using JSFiddle in a Chrome browser
For simplicity, we recommend that you change the editor layout settings in JSFiddle to display by ‘tabs’


<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/jsfiddle-tabs.gif">
</p>


----------
<br></br>

###Part 2. Writing your first code


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map in JSFiddle. 


1. Copy [this sample code](https://www.mapbox.com/mapbox-gl-js/example/simple-map/) and paste it into the **HTML section** of your JSFiddle.
2. Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/) in row 18 (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).
3. Click ‘Run’ in the upper left

<br></br>

<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/changes_map1.png">
</p>

<br></br>

4. Add a title and description and hit save!

5. See your map in fullscreen: Grab your JSFiddle unique ID (url), paste it into a new tab and add `/show` to the end. For example: ‘https://jsfiddle.net/4up1vwsm/show’


 **You’ve just made a web map! Not too shabby!**

<p align="center">
<img src="https://images.app.goo.gl/DDk7vku73SkityXGA">
</p>

----------

**Orientation to the browser developer console**
In Chrome, click `View` then `Developer` then `Developer Tools` and look at the `Elements` tab. As you hover over lines in the Elements tab, you’ll see things be highlighted in the webpage.

![](https://lh6.googleusercontent.com/5K7_xI9IWcZvSR39T_dU4chWWiL-hXnHuYnt53V_3_kxO8_NMcmZnyK4kWg5aZpqIJu62VqYbLT3v81xCHWqSV6WpMTNkp6NW1lN5_U5l1dTfvm4fWmSyvq3Dcx0R5-LoTOFt0To)


You can use the ‘Javascript Console’ to help troubleshoot errors in your code (we’ll practice this):

![](https://lh4.googleusercontent.com/T2mHZ4lt6dEJ_k9sH2fORiic_tY7olbQNR012tXWJhYOCek8lDCIrr6gLhmBySMG6GEi6YfL87Z3WxLssA-jEfFgv4pGOX7W4Csd8YU5iEjmBDdQjHSe0ziEMbXYCPKtfvcOfWE1)


*Note*: *Because we are looking at the code for the whole JSFiddle page, not only our webmap, the Console is slightly off about which row number it thinks has a problem. It should be that if you subtract* ***41*** *from the Console’s suggested row number, you’ll get the correct row in your JSFiddle HTML code.*

----------
## **Part 3. Editing your code**

Now that we’ve initialized the web and become more familiar with JSFiddle and our developer tools, let’s try to make some changes to our code. Currently, your map is centered on New Jersey when it loads. We need to change the location and the zoom level so that we can view the entire contiguous United States. 

1. Locate the line of code that is telling the map where to center the view.
2. Try changing the center location by picking a new coordinate using [http://geojson.io/](http://geojson.io/#map=2/20.0/0.0) (or looking at the bottom of the right-hand panel in the Mapbox Studio style editor).
3. Change the coordinates in your code and run your changes.
4. Change the zoom level to 3. 
5. Click ‘Run’ to see the changes to your map. 
![](https://lh4.googleusercontent.com/QhPa635tjRaHf8U2UHsD37384ITQmnXGifDEmePtWY5ea3NBkZJ0Rm7kGHNd44fZ4Tstr7ZHTmM7VXyzi7tRIRc97-TT80ew33amHToIwV1cgALBxBeaEOgktOGTjOC77Mag-Ehm)

----------

**Adding your custom style** 
**Style**: The map loads a style via the URL mapbox://styles/mapbox/streets-v11. This is a URL to a remote file that the map will download to determine the [tilesets](https://docs.mapbox.com/help/glossary/tileset/) it includes and how they are styled for the end-user. Mapbox GL JS permits URLs instead of literal data in several places, including data sources. To load the style that you created in the previous assignment, you need to go to go your Mapbox Studio account and find your Style URL ([how to find your Style URL](https://docs.mapbox.com/help/glossary/style-url/)):


![](https://lh3.googleusercontent.com/NYzNEZM2Y137jQzrnpV8-I9Jr2dTjxD3H9Be8D1kPhRXSoap3h7IRXsGw1h7TV7fPia9ZBCM_mGWrkIW9nMICkc397v3pzC9-6hjJychIFPrxiI6ErhVl0Vxf7Kr5HFXdQmmMHLX)



Or

![A screenshot of a cell phone  Description automatically generated](https://lh4.googleusercontent.com/9Qqh1-W8qufbm7_1jbKBQKmEmMWOqhl1i-DXCOS0CRHWCRXvCNBJ9JH-6WisMbr4wptL_t6GU6ICShoPM5O74kL2LQzyElet8GT3KLGhQ4qgHCWuRJrmFGBQgO0KpRWP70685yI2)




- Edit the row with the style URL it in your code and run your changes. *(Which row to edit? Look for a row with something that looks similar to your style URL)*
![A screenshot of a computer screen  Description automatically generated](https://lh3.googleusercontent.com/mbzLzkOUN0I_jy8Xhlb9ijef0bHRCRS42kJ6_blGIuw-oCzJ8O5bJyc6LsRMNrQCgyJ3SLjaP1FEXDIkJcBk0V7ckc4HTvoQVGFLJPRbpDtkZk_W-Fa1daEIUk7lDCssXzrxKWUa)

----------
## **Part 4. Add navigation controls**

Let’s try modifying the code to add a new element to the map. Currently, you can zoom in and out using your mouse, but we want to add navigation controls (zoom in, zoom out, and north arrow) to make the zooming functions more obvious to our end users.
To get started, check out this code: [https://www.mapbox.com/mapbox-gl-js/example/navigation/](https://www.mapbox.com/mapbox-gl-js/example/navigation/)
What is the part that’s missing for your current code? Copy and paste the navigation control function into your code after your `var = map` element but before the </script> and click ‘Run’ when you have finished.  

![A screenshot of a cell phone  Description automatically generated](https://lh4.googleusercontent.com/fGfeWBxa8N1L7h0PuOtXMY4SWMPM6Jlv5J4NEqBCAW-bQ2ayKjkQRA2OSaEg8CrpLSmME0Wv_8ToaofTZsCupOHurB8tzEJ_CJ1s-PJwk0CytmBaZsJkC2fcD8Acl_UMDTu8GiIA)



----------
## **Part 5. Adding dynamics legends** 

The map that we styled in studio displayed information about overdose rates by state and opioid prescribing rates by county. When we created our style, we set the dynamic zoom levels so that the state level data would appear at zoom level (X) and the county data would appear at zoom level (X).  We want to add a legend for each data layer depending on zoom level. In order do this, we are going to modify the following [code](https://docs.mapbox.com/mapbox-gl-js/example/updating-choropleth/). 
Copy and paste the following code after your opening  <body> element: 

![](https://docs.google.com/a/mapbox.com/drawings/d/sZGdIP5aN74LZ3yJ_4BUoLw/image?w=666&h=527&rev=1&ac=1&parent=1Aqox_tyu4L9uJLNoY27UXk3M-gmCfQyZlbGOtVdeQ7w)















Next, after your <div id='map'></div> but before your <script>  tag, copy and paste the following code: 

| <div id='state-legend' class='legend'><br><h4>Overdose Rates </h4><br><div><span style='background-color: #e9d3d3'></span>6.9 to 11.0</div><br><div><span style='background-color: #f5c0ad'></span>11.1 to 13.5</div><br><div><span style='background-color: #f0a184'></span>13.6 to 16.0</div><br><div><span style='background-color: #cc6f61'></span>16.1 to 18.5</div><br><div><span style='background-color: #c44936'></span>18.6 to 21.0</div><br><div><span style='background-color: #911e0d'></span>21.1 to 57.0</div><br><div><span style='background-color: #DA9C20'></span>1,000,000</div><br></div><br> <br><div id='county-legend' class='legend' style='display: none;'><br><h4>Opioid Prescribing <br> Drug Rates</h4><br><div><span style='background-color: #ffe9bd'></span>&lt; 57.2</div><br><div><span style='background-color: #ff8a73'></span>57.2 – 82.3</div><br><div><span style='background-color: #e13731'></span>82.4 – 112.5</div><br><div><span style='background-color: #650511'></span>&gt; 112.5</div><br><div><span style='background-color: #ffffff'></span>Missing Data</div><br></div> |                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | </div>                                                                  |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                         |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <div id='county-legend' class='legend' style='display: none;'>          |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <h4>Opioid Prescribing <br>Drug Rates </h4>                             |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <div><span style='background-color: #ffe9bd'></span>&lt; 57.2</div>     |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <div><span style='background-color: #ff8a73'></span>57.2 - 82.3</div>   |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <div><span style='background-color: #e13731'></span>82.4 - 112.5</div>  |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <div><span style='background-color: #650511'></span>&gt; 112.5</div>    |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <div><span style='background-color: #ffffff'></span>Missing Data </div> |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | </div>                                                                  |























Once you’ve added the above elements to your script, hit ‘Run’ and see what happens. 
The legend for the state data has been initialized but when you zoom into your county level data, the legend doesn’t change to match the county level data. This is because we haven’t yet written any code to tell the map to change legend displays at various zoom levels. To add zoom level controls, you first need to set a zoom level threshold. 
Add a new variable called zoomThreshold below your map variable. Set the new zoomThreshold variable to 5. 
var zoomThreshold = 5;
Next, add the following code below your zoomThreshold variable but before your closing </script> tag (hit ‘Run’ when you are finished): 





![](https://docs.google.com/a/mapbox.com/drawings/d/sx5RETgvmxz8NzZDeQJNtyw/image?w=679&h=236&rev=1&ac=1&parent=1Aqox_tyu4L9uJLNoY27UXk3M-gmCfQyZlbGOtVdeQ7w)






----------
## **Part 6. Create your webpage**

*You’ve made a web map! But this is just serving the map directly from the code within JSFiddle, it isn’t a webpage yet… to do that we need some way to host a webpage. Today, let’s use Github Pages.*
**Orientation to Github Pages** 

1. (Create a Github account if you don’t have one)
2. Set up a Github [repository](https://help.github.com/articles/create-a-repo/)
    - Name it whatever you want
    - Make it Public
    - Click the box to ‘Initialize this repository with a README’
![](https://lh3.googleusercontent.com/asCZvCmvq6bxNthgMEgDhmq1uQ1IwHqdLYOkGAKpoQT2yEhf_7e8Rsu5doIZ--mvDJ3Ru6h7Qf_rO95LEn9s7spGUnx2xLI7MleSAML0ra6fR1A6jpbx26qfKL9ksWsi74q1P9uC)

3. **Create a new file** called index.html
4. In the blankindex.html file, paste in the entire code we built in JSFiddle
5. [Enable Github Pages](https://pages.github.com/) (in repo Settings - the gear symbol in the upper right):
6. Then wait a minute, then go to your Github page address (https://[YOUR GITHUB NAME].github.io/[YOUR REPO NAME]/) - you can find this by scrolling back to the Github Pages settings.
7. (You might need to wait another minute if it doesn’t work right away)

***Voila! Now you have a live website with a Mapbox map!*** 

![](https://lh6.googleusercontent.com/29e4qlv_57-w7rxVwqA2ZyvjPGH-VAsy4ybuqD0RJz9WALLBpg2987F_kpAAN3NKdH3DSCZd-iNpr0styzaLQUpR8ly-_Qh-WQlFSQFknQPn8Bqr_7C8mAhX1DuQNtSjO58LrBKc)


**Polishing steps:**

- Currently, the tab for your webpage in your browser says ‘Display a map’ - let’s give it a better title - can you see where in the code to change that?
- Change it in your code, commit your changes in your Github index.html file, give it a minute, and check your webpage.


----------



