# Advanced
Welcome to Maptime @ Mapbox! Today you’re going to build… something! We'll be using iNaturalilst data of species spottings around the Bay Area. We'll help you get set up using Mapbox, but the rest is up to you!

## Objectives. You’ll learn how to…
- Upload data to Mapbox
- Deploy a web map
- Use GL JS to build a web app

## What you’ll need
- A Mapbox Account, sign up [here](https://www.mapbox.com/signup/)
- A text editor of your choice, we recommend Sublime or Atom
- (iNaturalist dataset](https://github.com/mzdraper/maptime-mapbox-parks/blob/master/Advanced/iNaturalist.geojson)
  * Or you can clone this whole repo: https://github.com/mzdraper/maptime-mapbox-parks

## Step one: create an HTML file
In your text editor, make a new HTML file called `index.html`. Create a new HTML file in your text editor in order to initialize a Mapbox GL JS map.

### Initialize your map
1. Open your text editor.
2. Copy and paste the code below into your text editor to initialize your Mapbox GL JS map.
3. Make sure `mapboxgl.accessToken` is set equal to your access token.
  - You can find your access token on your Access tokens page when you sign into your Mapbox Account .
4. Replace `your-style-URL-here` with your own style URL.
  - You can find your style URL on the Share, develop, and use page for your new style.
5. Save your file as “index.html.”
6. Open the file in a browser.
7. You should see a map displaying your data in a browser window.

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

## Step two: build a web app
Now that you have your web map and data ready, what do you wanna do with it? We’ve constructed a filtering example to help get you started, but we highly recommend going through out [examples](https://www.mapbox.com/mapbox-gl-js/example/simple-map/) page to see what else is possible. Let us know if you get stuck, we’re happy to help 🙂 Check out the Challenges for some inspiration to keep going!

### Challenges

- Can you create a web app that filters the spottings whether you typed in the common OR scientific name?
- Can you make a heat map of this data?
- Can you find out which spotting is closest to your location? 
- Where are these `common_name` plants?
  * Dandelions
  * Kale
  * Umbrella papyrus
  * Lemon
  * Western honey bee
  * Annual yellow sweetclover
  * Blue-gray gnatcatcher
  * Big berry manzanita
