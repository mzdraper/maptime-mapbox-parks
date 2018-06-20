# Intermediate
Welcome to Maptime @ Mapbox! Today we’re going to build a map of parks around San Francisco. The intermediate-level exercise requires writing code. Whether you’re comfortable with code or feel like you’ve always wanted to learn, try it out! We’re here to help 🙂 

## Objectives. You’ll learn how to…
- Create a dataset
- Style your own map using Mapbox Studio
- Put markers on a map
- Add interactivity to your markers!

## What you’ll need
- A Mapbox Account, sign up [here](https://www.mapbox.com/studio/signup/)
- A text editor of your choice, we recommend Sublime or Atom
- This [SF Parks dataset](https://github.com/mzdraper/maptime-mapbox-parks/blob/master/Intermediate/sf-parks.geojson)

## Step one: dealing with data

Uploading your data to Mapbox Studio as a dataset lets you store an editable version of your data in your Mapbox account. Having an editable version of your data means that you can add, remove, and edit features (points, lines, and polygons) as well as properties for each feature.

### How to create a dataset:
1. Log into Mapbox Studio.
2. Navigate to the **Datasets** page.
3. Click the **New dataset** button.
4. A new window will open. Select the **Upload** option in the upper right corner.
5. Click to select the GeoJSON you just downloaded.
6. Once your file has completed uploading, click Start editing.
7. The dataset editor will automatically open.

### How to draw a new feature
1. Click inside the Search places field and type the name of an SF park.
2. Use the point draw tool to create a new point on the map.
3. Click on the new feature and use the properties list on the left hand side to:
  - Add the field name `name` and give it the value of an SF park name.

### How to Export as a Tileset
1. Click the **Save** button in the upper right to save your changes.
2. Click the **Export** button.
3. Name your tileset and click **Export** in the open window.
4. After your tileset has succeeded, click View all your tilesets.
Step two: adding points to a web map

On your Styles page in Mapbox Studio, click the **Create** button and choose a style to begin editing in Mapbox Studio.

### How to Create a New Layer
1. When the style editor opens, click **+Add layer** in the upper left.
2. Next to **Source**, click on the box and find your sf-parks tileset. Click the name of the tileset to add it as the source for the layer.

![screenshot illustrating how to add a new layer in Mapbox Studio](https://www.mapbox.com/help/img/studio/point-tutorial-add-layer.png)

3. Mapbox Studio recognizes that the data you have uploaded is focused on a different location, so it displays the message “This tileset isn’t available from your map view.” Click Go to data, and the map view will refocus on the Bay Area.
4. Select the **Symbol** layer option so you can create a layer with markers.
5. Click **Create layer**.

![screenshot illustrating how to create a new layer in Mapbox Studio](https://www.mapbox.com/help/img/studio/point-tutorial-create-layer.png)

## Step two: create an HTML file

In your text editor, make a new HTML file called `index.html`. Create a new HTML file in your text editor in order to initialize a Mapbox GL JS map.

### Initialize your map
1. Open your text editor.
2. Copy and paste the code below into your text editor to initialize your Mapbox GL JS map.
3. Make sure `mapboxgl.accessToken` is set equal to your access token.
  - You can find your access token on your Access tokens page when you sign into your Mapbox Account .
4. Replace `your-style-URL-here` with your own style URL.
  - You can find your style URL on the Share, develop, and use page for your new style.
1. Save your file as “index.html.”
2. Open the file in a browser.
3. You should see a map displaying your data in a browser window.

```
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset='utf-8' />
        <title>Points on a map</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.2/mapbox-gl.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.2/mapbox-gl.css' rel='stylesheet' />
        <style>
          body {
            margin: 0;
            padding: 0;
          }
    
          #map {
            position: absolute;
            top: 0;
            bottom: 0;
            width: 100%;
          }
        </style>
      </head>
      <body>
        <div id='map'></div>
        <script>
        mapboxgl.accessToken = 'pk.eyJ1IjoibXpkcmFwZXIiLCJhIjoiY2poZ3J5MDdlMDB6ajM2cDF6bmNpNWVqaiJ9.f9viSl0MaQiYFBfA2P67NA'; // replace this with your access token
        var map = new mapboxgl.Map({
          container: 'map',
          style: 'your-style-URL-here', // replace this with your style URL
          center: [-122.447916, 37.760038],
          zoom: 10
        });
        // code from the next step will go here
        </script>
      </body>
    </html>
```

## Step three: add popups
After you have successfully displayed your map, you will need to add a little more code to allow the user to interact with your markers. Use the `queryRenderedFeatures` method in Mapbox GL JS to generate a list of all the points on your map and the feature properties associated with each. Then use `mapboxgl.Popup` to create popups that show certain feature properties. Finally, you will add an event listener so that popups are only shown when the user clicks a marker.

### Add more code
1. Copy and paste the code below into your HTML file after the code that initializes your map, but before the `</script>` tag.
  - Replace `layer-name-here` with the name of your layer as seen in the style editor. This is likely `sf-parks` if you have been following the earlier tutorials in this series.
  - Make sure that the properties match the name of the properties you would like to display in your popups. In this example, you will display the `title` and `description` properties.
1. Open in your browser and refresh.
2. You should be able to click on the markers and see titles and descriptions displayed in popups.

```
    map.on('click', function(e) {
      var features = map.queryRenderedFeatures(e.point, {
        layers: ['layer-name-here'] // replace this with the name of the layer
      });
    
      if (!features.length) {
        return;
      }
    
      var feature = features[0];
    
      var popup = new mapboxgl.Popup({ offset: [0, -15] })
        .setLngLat(feature.geometry.coordinates)
        .setHTML('<h3>' + feature.properties.title + '</h3><p>' + feature.properties.description + '</p>')
        .setLngLat(feature.geometry.coordinates)
        .addTo(map);
    });
```

## Congratulations!
You’ve made a map using the Mapbox Studio dataset editor, Mapbox Studio style editor, and Mapbox GL JS that incorporates custom data and styles and allows for user interaction.

### Challenges
- Can you find out which park is closest to your location?
- Can you make a [heat map](https://www.mapbox.com/mapbox-gl-js/example/heatmap-layer/) of the parks?