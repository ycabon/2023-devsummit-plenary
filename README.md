# Esri Devsummit 2023 - Plenary

The following demos were presented at the Esri DevSummit 2023 to showcase new client-side raster functions capability of the ArcGIS Maps SDK for JavaScript 4.26 (Mars 2023).

- [Multi-band](https://2023-devsummit-plenary.netlify.app/multi-band.html)
- [NDVI](https://2023-devsummit-plenary.netlify.app/ndvi.html)
- [Mountain Lion](https://2023-devsummit-plenary.netlify.app/mountain-lion.html)
- Scraped ~[Elevation](https://2023-devsummit-plenary.netlify.app/elevation.html)~

Watch on [mediaspace.esri.com](https://mediaspace.esri.com/media/t/1_nljpgowo?st=384&ed=648)

[![image](https://user-images.githubusercontent.com/1074239/228088048-3ceccb21-eb79-43f0-8f4a-c628dd5318d6.png)](https://mediaspace.esri.com/media/t/1_nljpgowo?st=384&ed=648)

## Script

The ImageryTileLayer from the JavaScript Maps SDK fetches, processes, and renders raster data directly in the web browser, enabling new workflows.
Let me show you how it works and some of its features.

### [Demo 1](https://2023-devsummit-plenary.netlify.app/multi-band.html)

[![image](https://user-images.githubusercontent.com/1074239/228088469-d46a275b-203c-4511-bf31-2c0db1331194.png)](https://2023-devsummit-plenary.netlify.app/multi-band.html)

_Open developer tools > Network tab_

This map here displays a multi-band raster from Landsat 8, hosted as an tiled image service.

Like its name suggests, the ImageryTileLayer requests tiles. You know about tiles; they are great because they are cacheable by the browser and the CDN and make the tile service scalable.

If we look at a tile, we can see that these are not images. In fact, each tile contains the actual pixel values from the raster at the tile resolution. 

Even better, if I can configure the layer to display the individual band of the raster or one of the typical compositions like “Natural Color”, “Color Infrared”, or “Agriculture”, notice that there was no additional network request made. This is because the tile contains the pixel values for all the bands at once.

It’s the layer that extracts and processes the values on the client, by converting them to colored pixels.

Now what if we could define that pixel processing…

### [Demo 2](https://2023-devsummit-plenary.netlify.app/ndvi.html)

[![image](https://user-images.githubusercontent.com/1074239/228088548-c24068b5-f795-45ca-873f-e3c7869f8ca7.png)](https://2023-devsummit-plenary.netlify.app/ndvi.html)

Well, we just released in beta: client-side Raster Functions.

A Raster Function takes raster data as input with a few other parameters and outputs a new raster.

In this example, I want to visualize the NDVI, which is the index used to quantify vegetation greenness and health. It is calculated as a ratio using the red and near infrared bands.

_Highlight first raster function._

First, I specify the name of the raster function to execute, NDVI, as well as the ids for the red and near infrared bands as arguments.

Then I chain that function with another one to map the calculated NDVI values to a color ramp. 

Finally, I assign that raster function chain on the layer to display.

_Execute_

Immediately we can spot greener pixels. And using the identify method of the layer, I can display in a UI the calculated NDVI value and the spectral profile chart for any of these pixels.

On greener pixels we can clearly see the difference between the red and near infrared bands.

### [Demo 3](https://2023-devsummit-plenary.netlify.app/mountain-lion.html)

[![image](https://user-images.githubusercontent.com/1074239/228088668-f5043584-69af-4a96-9945-827cf3148b7c.png)](https://2023-devsummit-plenary.netlify.app/mountain-lion.html)

Finally, we can create more advanced processing like this suitability analysis to evaluate the habitat of mountain lions.

I combined several layers into one multi band tiled image, to represent the different habitat preferences of mountain lions like:
-	The distance to roads
-	The area protection status, like state parks and national forests
-	The land cover. Preys hunted by mountain lions tend to prefer forested or shrubby land.
-	The terrain ruggedness, where cliffs for example give an advantage to mountain lions over their preys.

Each band is processed by raster functions and they are all combined together into the final image.

_Show the raster function chain._

Here’s a representation of the full raster function chain. Let’s see the result.

_Show the final result._

What’s cool is that users now can interact with these sliders to change the different parameters and see the analysis output updating in real time, so powerful.

### Outro

Raster functions are available now in beta in the latest JavaScript Maps SDK. These and all the other features of the ImageryTileLayer let you to bring new, fast, and interactive raster analytics to your applications. 

