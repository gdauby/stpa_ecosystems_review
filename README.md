---
title: "Readme"
author: "Gilles Dauby"
date: "2021-06-04"
output: 
  html_document:
    keep_md: true
---





This page provide resources used or produced and codes used in the chapter __"Typification, distribution and biodiversity of terrestrial ecosystems in the Gulf of Guinea Oceanic Islands"__ of the book *"Biodiversity of the Gulf of Guinea Oceanic Islands: Science and Conservation"*.
   
For an interactive exploration of the proposed synthetic ecosystem classification of Sao Tomé & Principe, click on the following link:
[https://gdauby.shinyapps.io/stpa_classification/](https://gdauby.shinyapps.io/stpa_classification/).


# Datasets





<table class="table" style="margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> dataset </th>
   <th style="text-align:left;"> Source or method of acquisition </th>
   <th style="text-align:left;"> Unit </th>
   <th style="text-align:left;"> Nature </th>
   <th style="text-align:right;"> Resolution </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Elevation </td>
   <td style="text-align:left;"> Downloaded using the elevatr R package (Hollister, J.W., Tarak Shah, 2017). Source: https://registry.opendata.aws/terrain-tiles/ </td>
   <td style="text-align:left;"> m </td>
   <td style="text-align:left;"> Raster </td>
   <td style="text-align:right;"> 0.0000858 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Topography </td>
   <td style="text-align:left;"> Using the elevation raster, we first computed the Topographic Position Index, then converted it to categories using thresholds. </td>
   <td style="text-align:left;"> None. Categorical. </td>
   <td style="text-align:left;"> Raster </td>
   <td style="text-align:right;"> 0.0008333 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Slope </td>
   <td style="text-align:left;"> Computed in degrees using fasterTerrain function of fasterRaster R package. </td>
   <td style="text-align:left;"> Degrees </td>
   <td style="text-align:left;"> Raster </td>
   <td style="text-align:right;"> 0.0008333 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Annual rainfall </td>
   <td style="text-align:left;"> Soares et al. 2020 Animal conservation, digitalization of mean annual precipitation map in millimetres from Silva HLE. 1958. Esboço da carta de aptidão agrícola de São Tomé e Príncipe. Garcia de Orta 6:61-86. Tenreiro F. 1961. A ilha de São Tomé. Junta de Investigações Científicas do Ultramar, Lisboa. </td>
   <td style="text-align:left;"> mm </td>
   <td style="text-align:left;"> Raster </td>
   <td style="text-align:right;"> 0.0008333 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cloud cover </td>
   <td style="text-align:left;"> Remote sensed dataset from https://www.earthenv.org/cloud (Wilson &amp; Jetz 2016). Monthly dataset were downloaded. We computed the mean monthly data and the standard deviation of monthly data. The original resolution is 0.008333333. We resampled the raster to 0.0008333251 </td>
   <td style="text-align:left;"> % </td>
   <td style="text-align:left;"> Raster </td>
   <td style="text-align:right;"> 0.0008333 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Non-forested areas </td>
   <td style="text-align:left;"> A polygon with several types (built area, roads, non forested area (not road or built)). </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Secondary forests </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Forested agricultural lands </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Palm industrial plantation </td>
   <td style="text-align:left;"> Digitalization from google earth. </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fire frequency </td>
   <td style="text-align:left;"> Remote sensed fire recording FIRMS (Fire Information for Resource Management System) 'https://firms.modaps.eosdis.nasa.gov/). We selected archive shapefiles. We counted the frequency of each point for each year for a grid of 1x1 km. </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Coastal shores </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Total coast polygon </td>
   <td style="text-align:left;"> Retreived from OSM data. Smaller islands were combined with mainlainds, by merging their polygons obtained using osm R package: add_osm_feature(key = 'boundary', value = "administrative"). The polygons were then converted into polylines and a buffer of 50 m was added. </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Beaches areas </td>
   <td style="text-align:left;"> Retreived from OSM data using osm R package: add_osm_feature(key = 'natural', value = 'beach'), then manually edited for adding missing areas in the west. </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Palustrine areas </td>
   <td style="text-align:left;"> Retreived from OSM data using osm R package: add_osm_feature(key = 'natural', value = 'water') </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Mangroves </td>
   <td style="text-align:left;"> Herrero-Barrencua, A., Haroun, R. &amp; Abreu, A.D. 2017. Caracterización preliminar de los manglares de la Isla de Príncipe (São Tomé e Príncipe). IU-ECOAQUA, Univ. Las Palmas de Gran Canaria. 70 pp. Disponible en: www.ecoaqua.eu </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Polygons </td>
   <td style="text-align:right;"> NA </td>
  </tr>
</tbody>
</table>


# Mapping
  
Below, you will find codes to produce an interactive map in R.
Make sure you download all the data in the data directory, or clone the github repository locally.


```r
### needed packages, make sure you use a recent R version (>= 4.x) 

library(sf)
library(tidyverse)
library(leaflet)
```


```r
inland_upland_montane <- st_read("./data/sao_tome/inland_upland_montane.shp")
inland_upland_submontane <- st_read("./data/sao_tome/inland_upland_submontane.shp")
inland_dry_north <- st_read("./data/sao_tome/inland_dry_north.shp")
inland_wet_south_lowland <- st_read("./data/sao_tome/inland_wet_south_lowland.shp")
all_shores_eco <- st_read("./data/sao_tome/all_shores_st.shp")
all_shores_eco <- 
  all_shores_eco %>% 
  mutate(type = replace(type, grepl("Mangrove", type), "mangrove")) %>% 
  mutate(type = replace(type, grepl("mangrove_", type), "mangrove"))
```



```r
mytext_shores <- paste(all_shores_eco$type,
  sep="") %>%
  lapply(htmltools::HTML)

mytext_dry <- paste(inland_dry_north$type,
                       sep="") %>%
  lapply(htmltools::HTML)

mytext_sub <- paste(inland_upland_submontane$type,
                    sep="") %>%
  lapply(htmltools::HTML)

mytext_mont <- paste(inland_upland_montane$type,
                    sep="") %>%
  lapply(htmltools::HTML)

mytext_wet <- paste(inland_wet_south_lowland$type,
                     sep="") %>%
  lapply(htmltools::HTML)


all_ecosystems <-
  leaflet() %>%
  addProviderTiles(providers$Esri.WorldImagery, group =  "Esri") %>%
  addProviderTiles(providers$OpenStreetMap, group =  "OSM") %>%
  addProviderTiles(providers$OpenTopoMap, group =  "OpenTopoMap") %>%
  addPolygons(
    data = st_transform(all_shores_eco, 4326), 
    stroke = T,
    weight = 0.5,
    opacity = 0.5,
    dashArray = "1",
    fillOpacity = 0.5,
    color = ~ colorFactor("viridis", type)(type),
    group = 'Coastal shores',
    label = mytext_shores,
    highlight = highlightOptions(
      weight = 5,
      color = "white",
      dashArray = "1",
      fillOpacity = 0.1,
      bringToFront = TRUE
    ),
    labelOptions = labelOptions( 
      style = list("font-weight" = "normal", padding = "3px 8px"), 
      textsize = "13px", 
      direction = "auto"
    )
  ) %>%
  addPolygons(
    data = st_transform(inland_dry_north, 4326), 
    stroke = T,
    weight = 0.5,
    opacity = 0.5,
    dashArray = "1",
    fillOpacity = 0.5,
    color = ~ colorFactor("magma", type)(type),
    group = 'Lowland deciduous forest and woodlands',
    label = mytext_dry,
    highlight = highlightOptions(
      weight = 5,
      color = "white",
      dashArray = "1",
      fillOpacity = 0.1,
      bringToFront = TRUE
    ),
    labelOptions = labelOptions( 
      style = list("font-weight" = "normal", padding = "3px 8px"), 
      textsize = "13px", 
      direction = "auto"
    )
  ) %>%
  addPolygons(
    data = st_transform(inland_upland_submontane, 4326), 
    stroke = T,
    weight = 0.5,
    opacity = 0.5,
    dashArray = "1",
    fillOpacity = 0.5,
    color = ~ colorFactor("plasma", type)(type),
    group = 'Submontane rainforests',
    label = mytext_sub,
    highlight = highlightOptions(
      weight = 5,
      color = "white",
      dashArray = "1",
      fillOpacity = 0.1,
      bringToFront = TRUE
    ),
    labelOptions = labelOptions( 
      style = list("font-weight" = "normal", padding = "3px 8px"), 
      textsize = "13px", 
      direction = "auto"
    )
  ) %>%
  addPolygons(
    data = st_transform(inland_upland_montane, 4326), 
    stroke = T,
    weight = 0.5,
    opacity = 0.5,
    dashArray = "1",
    fillOpacity = 0.5,
    color = ~ colorFactor("inferno", type)(type),
    group = 'Montane rainforests and grasslands',
    label = mytext_mont,
    highlight = highlightOptions(
      weight = 5,
      color = "white",
      dashArray = "1",
      fillOpacity = 0.1,
      bringToFront = TRUE
    ),
    labelOptions = labelOptions( 
      style = list("font-weight" = "normal", padding = "3px 8px"), 
      textsize = "13px", 
      direction = "auto"
    )
  ) %>%
  addPolygons(
    data = st_transform(inland_wet_south_lowland, 4326), 
    stroke = T,
    weight = 0.5,
    opacity = 0.5,
    dashArray = "1",
    fillOpacity = 0.5,
    color = ~ colorFactor(palette.colors(n=5), type)(type),
    group = 'Lowland moist and wet forests',
    label = mytext_wet,
    highlight = highlightOptions(
      weight = 5,
      color = "white",
      dashArray = "1",
      fillOpacity = 0.1,
      bringToFront = TRUE
    ),
    labelOptions = labelOptions( 
      style = list("font-weight" = "normal", padding = "3px 8px"), 
      textsize = "13px", 
      direction = "auto"
    )
  ) %>% 
  addLayersControl(
    baseGroups = c("OSM", "ESRI", "OpenTopoMap"),
    overlayGroups = c("Coastal shores", 
                      "Lowland deciduous forest and woodlands",
                      "Submontane rainforests", 
                      "Montane rainforests and grasslands",
                      "Lowland moist and wet forests"),
    options = layersControlOptions(collapsed = FALSE)
  )
```




# Codes

Below you can find example of codes used for creating the synthetic ecosystem classification.
  
Open-source shapefiles were downloaded on the [GeoFrabicks website](http://download.geofabrik.de/africa/sao-tome-and-principe.html) that provide OpenStreetMap (OSM) datasets.



```r
library(cleangeo)
library(sf)
library(sp)
library(tidyverse)
```



The code below was used to build the road network with a buffer of 10 metres based on OSM dataset.


```r
main_roads <- 
  st_read("gis_osm_roads_free_1.shp")

main_roads <- st_transform(main_roads, 32632)
main_roads_buff <- 
  st_buffer(main_roads, 10)
main_roads_buff <- as(main_roads_buff, "Spatial")
main_roads_buff <- gUnaryUnion(main_roads_buff)
report <- clgeo_CollectionReport(main_roads_buff)
summary <- clgeo_SummaryReport(report)
main_roads_buff_cleaned <- clgeo_Clean(main_roads_buff)
main_roads_buff_cleaned_sf <- as(main_roads_buff_cleaned, "sf")
st_crs(main_roads_buff_cleaned_sf) <- 32632
```



