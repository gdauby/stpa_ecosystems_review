This page aims to provide ressources used and produced in the chapter
**“Typification, distribution and biodiversity of terrestrial ecosystems
in the Gulf of Guinea Oceanic Islands”** of the book *“Biodiversity of
the Gulf of Guinea Oceanic Islands: Science and Conservation”*.

For an interactive exploration of the proposed synthetic ecosystem
classification of Sao Tomé & Principe, click on the following link:
<https://gdauby.shinyapps.io/stpa_classification/>.

Below, you will find codes to produce an interactive map in R. Make sure
you download all the data in the data directory, or clone the github
repository locally.

``` r
### needed packages, make sure you use a recent R version (>= 4.x) 

library(sf)
library(tidyverse)
library(leaflet)
```

``` r
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

``` r
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
