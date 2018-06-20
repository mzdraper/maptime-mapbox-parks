# Beginner
Welcome to Maptime @ Mapbox! Today we’re going to build a map of parks around San Francisco. As you can see, we're missing a ton of parks on this map, and we need your help marking them! Can you help us find them?

## Objectives. You’ll learn how to…
- Create a dataset
- Style your own map using Mapbox Studio
- Put markers on a map

## What you’ll need
- A Mapbox Account, sign up [here](https://www.mapbox.com/studio/signup/)
- This [SF Parks dataset](https://github.com/mzdraper/maptime-mapbox-parks/blob/master/Beginner/sf-parks.geojson)

## Step one: dealing with data

Uploading your data to Mapbox Studio as a dataset lets you store an editable version of your data in your Mapbox account. Having an editable version of your data means that you can add, remove, and edit features (points, lines, and polygons) as well as properties for each feature.

- Features are the points, lines, and polygons on your map. You can add new features using the draw tools, edit the placement or shape of features using by clicking and dragging features on the map, or remove features all together by clicking on them and hitting the delete key. You can also click on each feature in the dataset editor to view its properties.
- Properties can be strings, numbers, or booleans. In this example, there are `title` and `description` properties for each point with a unique text string. In the dataset editor you can edit the properties of each feature. You can also add new properties or delete properties in the dataset editor. Make sure any content that you want to display in popups is included as a property while you are working in the dataset editor.

### How to create a dataset:
1. Log into Mapbox Studio.
2. Navigate to the **Datasets** page.
3. Click the **New dataset** button.
4. A new window will open. Select the **Upload** option in the upper right corner.
5. Click to select the GeoJSON you just downloaded.
6. Once your file has completed uploading, click Start editing.
7. The dataset editor will automatically open.

### How to draw a new feature
1. Click inside the Search places field and type in a San Francisco park.
2. Use the point draw tool to create a new point on the map.
3. Click on the new feature and use the properties list on the left hand side to:
  - Add the field name `title` and give it the value of the park's name.

Web maps are made up of map tiles. To add your data to a web map, it needs to be cut up into tiles so the data can be displayed at various zoom levels. In Mapbox maps, the collection of tiles your data is cut up into is called a tileset.

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

## Step two: How to Style a Symbol Layer

In the Mapbox Studio style editor, you can specify the style properties of each layer. This includes the layers in the Mapbox default styles and any layers you’ve added with custom data. For this example, you will style a symbol layer. You can style symbol layers with both text and icons.

1. Click on the sf-parks layer you created in the layer list on the left side of the style editor.
2. When the style panel opens, click the **Style** tab if you’re not already there.
3. Select the Icon tab and click on **Manage icons** in your spritesheet.
4. This opens the Manage style images option in the debug panel. 

![screenshot demonstrating the upload SVG menu in Mapbox studio](https://www.mapbox.com/help/img/studio/point-tutorial-upload-svg.png)

5. Click the **Upload SVG Image** button to and choose the marker you downloaded at the beginning of this tutorial from your files.
6. Once the icon has loaded, choose it from the list. 

![screenshot demonstrating the upload SVG menu in Mapbox studio](https://www.mapbox.com/help/img/studio/point-tutorial-select-icon.png)

7. If you would like to show all the markers, even if they overlap, click on the **Placement** tab. Scroll down to Allow icon overlap and set it to `True`.

You should now see the marker icon appear on all of your points.

![screenshot showing a style with a custom icon loaded in Mapbox Studio](https://www.mapbox.com/help/img/studio/point-tutorial-icons-loaded.png)

## Step three: publish and use

Now that you have finished styling your map, you need to publish your style in order for those changes to be live on the web.

1. Click the **Publish** style button in the top right of the editor.
2. A window will pop up asking you to review your changes.
3. Click **Publish**.
4. Then, click **Share, develop, & use your style**.

![animated gif illustrating how to publish your style](https://www.mapbox.com/help/img/studio/point-tutorial-style-publish.gif)

The [Share, develop, and use](https://www.mapbox.com/help/studio-manual-publish/) page contains the resources you need to publish your style in a web app, mobile app, or with another third party tool.

## Congratulations!

You created your first web map! If you feel like adventuring, go through the challenges or move onto Intermetiate.

### Challenges
- Add 5 more parks to your dataset
- Change the marker's icon
- Style your basemap