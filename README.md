# Geolabels
OpenSource lines for cartographic labeling of physical geographic features

## Brief
The purpose of this repository and data is to start a centralized dataset of lines representing physical features used for labeling in various types of cartographic outputs. As of its creation it consists of approximately 1300 geographic line features covering both land and sea globally. The data primarily represents small scale physical features with more detail in the contiguous USA thanks to Tom Patterson's map. The goal is to grow the extent and detail of the lines so they are useful at all scales. 

The intial data was created from two different sources. 

*   Centerlines from [Natural Earth](https://www.naturalearthdata.com/downloads/10m-physical-vectors/10m-physical-labels/) physical label areas and marine areas using the voronoi diagram based [centerline tool](https://github.com/ungarj/label_centerlines). 
*   Lines extracted from Tom Patterson's new [Physical Map of the Contiguous US](http://www.shadedrelief.com/us-physical/) using MapPublisher. 

## The Data
There are two datasets present in this repository. The geojson file in **working_dataset is the one that all pull requests should be against**. The other, **master_dataset** is meant to be a final polished copy with some empty fields automatically populated.

The data consists of single line features with fields for:
*   name
*   type
*   scalerank
*   minzoom
*   maxzoom
*   date_added
*   date_edited
*   verified

### Type Field
All features currently exist as one of the following types:

* basin
* bay
* canyon
* channel
* coast
* delta
* desert
* fjord
* foothills
* geoarea
* gorge
* gulch
* gulf
* inlet
* island
* island_group
* isthmus
* lagoon
* lowland
* pen_cape
* peninsula
* plain
* plateau
* range_mtn
* ridge
* river
* sea
* sound
* strait
* tundra
* valley
* wetlands

### Scalerank
Natural Earth derived ranking number from 0 to 9. Lower numbers being of greater significance on the map, higher numbers being smaller and less prominent features.

### Min and Max Zoom
If using the data for vector or raster tiles the min and max zoom fields help determine when during the zoom a feature should appear on the map.

### Dates added and edited
Date added is the date that the feature was initially added to the data. Date edited will be populated if someone makes changes to a feature.

### Verified
Yes or null values if the feature has been verified for accuracy and validity by another user.

## Contributing
This project is at the ground floor with the hopes that the cartographic community will get involved and expand upon this data for the benefit of all map makers. For now the data exists as a simple geojson file. In time, if involvement increases and the data grows we will explore necessary avenues to improving upon the editing and contribution process.

For now, clone the repository and create a separate branch then edit/add features from **working_dataset/geolabels.geojson** in whatever GIS editing platform you prefer.

When creating new line features, populate the **name** and **type** fields at a minimum. When contributing new features to the data the type field must be populated with one of the existing values listed above. Other fields, if left blank, will be autopopulated later.

**Merge Conflicts**
If multiple people are working on the dataset at the same time merge conflicts will arise when new features are added. You can resolve conflicts by performing a git pull on master into your branch, and opening the conflicting file in a program like VS Code. Scroll to the area of conflict and _accept both changes_. There will likely be a missing comma at the point your new features were inserted so you'll need to fix that for it to be a valid geojson. Using something like [Mapbox geojsonhint](https://github.com/mapbox/geojsonhint) will pinpoint where exactly in the geojson syntax errors occur, as I have yet to find a VS Code linter for geojson files.

## Verification
We are relying on checking each other's work for validity and accuracy. There is a **verified** field in the data which will be populated with `yes` if a feature has been verified to exist by another contributor. This way we can edit and assure accuracy and a user of the data can choose if they want to show all or only verified features on their maps. If you want to help verify new features clone the repo and view/edit in your favorite GIS program and add `yes` to any new features you verify for accuracy. If you discover errors you may correct them and then update the **date_edited** field as well.

## Data to Add
If you don't want to go through the process of adding line features to the geolabels.geojson but have some good line or polygon data you'd like to see added as more geolabels, please include a link to it here as long as the data is free to use.
