---
layout: default
title: Generating Coordinate Points
nav_order: 6
---



To solve this problem, we're first going to get a grid of points over Vancouver Island that we can then import into ClimateNA, where we will be able to pull our climate data from.

**Pull in an OSM layer**

This will allow us to see where we need to start drawing!

**Create a new vector layer**

We'll want to draw out a polygon around Vancouver Island, our study area.

1. Create a new vector layer.
2. Provide a file name.
3. Select `Polygon` for the Geometry type.
4. Add a new field called `Study area` and keep the defaults for data type and length.
5. Hit `Ok`.

**Draw your polygon**

1. Select the layer you just created.
2. Select the pencil to edit the layer.
3. Select the `draw polygon` tool.
4. Go to town with as much or as little detail as you'd like. Your left mouse button will create a new point. When you're done, your right mouse button will close the loop.
5. Select the pencil icon again to save your changes. *If you don't save your changes now, your grid point creation will fail.*

**Generate a grid of points**

We want to generate a point for every kilometre.

1. Go to your `Processing Toolbox` (availbale under `View > Panels` if not already visible).
2. Search for `Create grid` and open the dialogue box.
3. Set the
   1. `Grid type` to `Point`.
   2.  `Grid extent` to match your polygon layer.
   3. Horizontal and Vertical spacing to `1 Kilometer`
4. Select `run`. This will probably take just shy of 2 minutes.
5. Admire the big colourful box blocking your view of the Island.

**Clean up the grid**

We only need those grid points that are actually on Vancouver Island, so we'll get rid of the excess.

1. In your toolbox, search for `Intersection`.
2. For the `Input layer`, select your point grid you just created.
3. For the `Overlay layer` select your polygon trace of the Island.
4. Give your new data set a file name and select `Run`
5. In your layers panel, uncheck the first grid layer you created, and voila, you've got your island back.

**Reproject your data**

One small issue now. We spaced our grid at 1km intervals. But e need to know the decimal degree coordinates of our grid points for ClimateNA. So we'll convert the projection from one based on metres (EPSG:3857) to one that uses decimal degrees (EPSG:4326).

1. In your toolbox, search for `Reproject layer`.
2. In the dialogue box, select your Island point layer for the `Input layer`
3. Ensure the `Target CRS` is set to `EPSG:4326 - WGS 84`
4. Give your new layer a file name to be saved to and select `Run`

**Get your lat and long**

Your attribute table at this point won't look much different for this new layer. While it's now in a different CRS, we still need to input the lat and long into the attribute table.

1. Open the attribute table for your latest layer.
2. Select the pencil to edit the attribute table.
3. Select the `Open field calculator` icon.
4. In the `Output field name` type something to indicate that this is your `lat` measure.
5. In the `Output field type`, select `Decimal number (real)`.
6. In the `Expression` box type `$y`, that is, the y-intersect.
7. Hit `Ok` and give it a second to run.
8. Repeat this process, calling the second field something like `long` and using the x-intersect - `$x` - in the `Expression` box.

**Get your elevation data**

**Export your data to csv**

We'll need our lat, long, and elevation in csv for import into ClimateNA.

1. Right click on your degree decimal layer and select `Export > Save Features As...`
2. In the dialogue box, for `Format`, select `csv`.
3. Provide a reasonable file name
4. Ensure the `CRS` is set to `EPSG:4326 - WGS 84`
5. Hit `Ok`

You're all ready to get some climate data now for each of your coordinates. Yay!