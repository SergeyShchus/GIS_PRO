# GIS PRO (Python) - створення бази та наповнення даними з каталогів

[Data - naturalearth](http://naciscdn.org/naturalearth/packages/Natural_Earth_quick_start.zip)


Створіть новий проект і блокнот Python

У блокноті запутіть код, вказавши вірний шлях до каталогу з даними та назву бази (буде створена у каталозі поточного проекту)

```
import os

workspace = r'--folder--' #вказати каталог

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

![result](https://github.com/SergeyShchus/GIS_PRO/blob/main/Notebook/shp-data(folders)-to-database_GisPro/result.PNG?raw=true)
