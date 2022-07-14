1. [Download data (RTC HH GeoTIFF)](https://www.kaggle.com/datasets/sergiishchus/Regional-Inundation-L-band-SAR)
2. ###Convert the RTC images from linear power to db.
- In ArcMap, load all of the RTC HH GeoTIFF images from the folder. If prompted to create pyramids for an image layer, click No.
- Start the Raster Calculator tool (Spatial Analysis Tools > Map Algebra).
- Create output folder HH_db, and specify output filename as Rnnnnn_db.tif where nnnnn is orbit number.
- Compute db = 10.*Log10 (“RTC_HH_granule”)
- Repeat process for all RTC granules or create model
3. ###Filter images to reduce speckle.
- In the ArcMap top menu, go to Windows > Image Analysis
- Select the first image.
- Under Processing, click on Add Function.
- In the Function Template Editor, right-click on Identity Function, mouse-over Insert Function, and select Speckle Function from the menu.
- In the parameters menu that appears, change the Filter Type setting from “Lee” to “Enhanced Lee” and keep the rest of the parameters set to their defaults.
- The files that result from this are temporary. To save them permanently to the hard drive as a GeoTIFF, use the Copy Raster (Data Management Tools > Raster > Raster Dataset) tool, with the Output Raster Dataset field set to a directory and filename (ending in .tif) of your choice, and all other fields blank.
- Repeat steps 2-6 for all images.
4. ###Require calculation of statistics.
- In ArcMap, display all filtered db images created by the Copy Raster tool.
- Open Batch Calculate Statistics (Data Management Tools > Raster > Raster Properties).
- Drag and drop all images into the input and click OK to calculate statistics for all of the images.
5. App color to tiff
6. Export color-raster
7. Create animation
8. Reclass rasters and create sum rasters in calc
