# Plot a choropleth map for an indicator

Plot a choropleth map for an indicator

## Usage

``` r
map(
  data,
  ons_api,
  area_code,
  fill,
  type = "static",
  value,
  name_for_label,
  title = "",
  subtitle = "",
  copyright_size = 4,
  copyright_year = Sys.Date()
)
```

## Arguments

- data:

  data.frame or tibble which will be fed into ggplot functions. This
  object should contain the fields used for the arguments within this
  function

- ons_api:

  string; GeoJSON url of a shape file. This can be found on the ONS
  geography portal

- area_code:

  field containing area codes to join to shape file imported from ONS
  API

- fill:

  unquoted field name for the field to be used to determine the
  colouring of the bars; usually reflecting significance. The values
  that values that can be used in this field with predetermined colours
  are: 'Better', 'Higher', 'Similar', 'Lower', 'Worse', 'Not compared',
  'None'

- type:

  string; the output map required. Can be "static" or "interactive"

- value:

  if interactive map, unquoted field name for the field containing
  values to be used for label of polygons when hovering

- name_for_label:

  if interactive map, unquoted field name for the field containing area
  names to be used for label of polygons - optional

- title:

  string; title of chart

- subtitle:

  string; subtitle of the chart

- copyright_size:

  number; used to control the size of the copyright text

- copyright_year:

  number (length 4 characters) or Date class; the copyright year
  displayed at bottom of the map. Applies to static maps only

## Value

a either a static or interactive ggplot choropleth map

## See also

Other quick charts: [`box_plots()`](box_plots.md),
[`compare_areas()`](compare_areas.md),
[`compare_indicators()`](compare_indicators.md),
[`overview()`](overview.md), [`population()`](population.md),
[`trends()`](trends.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ons_api <- "https://services1.arcgis.com/ESMARspQHYMw9BZ9/arcgis/rest/services/Counties_and_Unitary_Authorities_December_2021_EN_BUC/FeatureServer/0/query?outFields=*&where=1%3D1&f=geojson"

p <- map(mapdata,
         ons_api = ons_api,
         area_code = AreaCode,
         fill = Significance,
         title = "Map example",
         subtitle = "An indicator for Upper Tier Local Authorities England",
         copyright_year = 2019)

p

## For an interactive (leaflet) map
p <- map(mapdata,
         ons_api = ons_api,
         area_code = AreaCode,
         fill = Significance,
         type = "interactive",
         value = Value,
         name_for_label = AreaName,
         title = "An indicator for Upper Tier<br>Local Authorities England")
p} # }
```
