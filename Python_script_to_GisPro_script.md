## Створення інструменту сценарію з окремого файлу Python

Sript Python:

```
import os

workspace = r'..\\Natural_Earth_quick_start'

folders = [x[0] for x in os.walk(workspace)]
for folder in folders:
    print ("Checking" + folder + "for shapefiles.")
    #set workspase
    arcpy.env.workspace = folder
    #list shapefiles
    fcs = arcpy.ListFeatureClasses("*.shp")
    #check whether any shp are present
    if len(fcs) > 0:
        print("Shapefiles found! Creating a file gdb..")
        gdb_name = "base " + folder.split("\\")[-1] + ".gdb"
        arcpy.CreateFileGDB_management(folder, gdb_name)
        #for each shapefile, convert to file gdb format
        for fc in fcs:
            print("Converting " + fc + " to file gdb. format.") 
            output_path = os.path.join(folder, gdb_name)
            out_name = arcpy.Describe(fc).baseName    
            arcpy.FeatureClassToFeatureClass_conversion (fc, output_path, out_name)
            
```

Edit script to GisPro format:

```

import os
import arcpy

workspace = arcpy.GetParameterAsText(0)

folders = [x[0] for x in os.walk(workspace)]
for folder in folders:
    arcpy.AddMessage ("Checking" + folder + "for shapefiles.")
    #set workspase
    arcpy.env.workspace = folder
    #list shapefiles
    fcs = arcpy.ListFeatureClasses("*.shp")
    #check whether any shp are present
    if len(fcs) > 0:
        print("Shapefiles found! Creating a file gdb..")
        gdb_name = "base " + folder.split("\\")[-1] + ".gdb"
        arcpy.CreateFileGDB_management(folder, gdb_name)
        #for each shapefile, convert to file gdb format
        for fc in fcs:
            print("Converting " + fc + " to file gdb. format.") 
            output_path = os.path.join(folder, gdb_name)
            out_name = arcpy.Describe(fc).baseName    
            arcpy.FeatureClassToFeatureClass_conversion (fc, output_path, out_name)
            
```




Create new tool, add script

