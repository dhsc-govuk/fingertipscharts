# Plot trend chart

Plot trend chart

## Usage

``` r
trends(
  data,
  timeperiod,
  value,
  area,
  comparator,
  area_name,
  fill,
  lowerci,
  upperci,
  title = "",
  subtitle = "",
  xlab = "",
  ylab = "",
  point_size = 4
)
```

## Arguments

- data:

  data.frame or tibble which will be fed into ggplot functions. This
  object should contain the fields used for the arguments within this
  function

- timeperiod:

  unquoted field name for the field containing the time period

- value:

  unquoted field name for the field containing the value variable which
  will be plotted on x axis

- area:

  unquoted field name for the field containing the area names

- comparator:

  string; name of comparator area (this value should exist in the field
  described by the area parameter)

- area_name:

  string; name of the area to be displayed (this value should exist in
  the field described by the area parameter)

- fill:

  unquoted field name for the field to be used to determine the
  colouring of the bars; usually reflecting significance. The values
  that values that can be used in this field with predetermined colours
  are: 'Better', 'Higher', 'Similar', 'Lower', 'Worse', 'Not compared',
  'None'

- lowerci:

  unquoted field name for the field containing the variable to be
  plotted as lower confidence interval (optional)

- upperci:

  unquoted field name for the field containing the variable to be
  plotted as upper confidence interval (optional)

- title:

  string; title of chart

- subtitle:

  string; subtitle of the chart

- xlab:

  string; x-axis title

- ylab:

  string; y-axis title

- point_size:

  number; size of point

## Value

a ggplot of trends for an indicator alongside a comparator

## See also

Other quick charts: [`box_plots()`](box_plots.md),
[`compare_areas()`](compare_areas.md),
[`compare_indicators()`](compare_indicators.md), [`map()`](map.md),
[`overview()`](overview.md), [`population()`](population.md)

## Examples

``` r
library(dplyr)
df <- create_test_data()

df_trend <- df %>%
        arrange(IndicatorName) %>%
        mutate(Timeperiod = rep(c("2011", "2012", "2013", "2014", "2015", "2016"),
                                each = 111))
p <- trends(df_trend,
            timeperiod = Timeperiod,
            value = Value,
            area = AreaCode,
            comparator = "C001",
            area_name = "AC142",
            fill = Significance,
            lowerci = LCI,
            upperci = UCI,
            title = "Trend compared to country",
            subtitle = "For area AC142",
            xlab = "Year",
            ylab = "Value (%)")
p
```
