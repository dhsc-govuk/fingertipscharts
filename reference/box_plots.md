# Plot a series of boxplots

Plot a series of boxplots

## Usage

``` r
box_plots(
  data,
  timeperiod,
  value,
  title = "",
  subtitle = "",
  xlab = "",
  ylab = ""
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

  unquoted field name for the field containing the values for the
  indicator that is being plotted

- title:

  string; title of chart

- subtitle:

  string; subtitle of the chart

- xlab:

  string; x-axis title

- ylab:

  string; y-axis title

## Value

a ggplot of boxplots for an indicator for containing values for multiple
areas over time

## See also

Other quick charts: [`compare_areas()`](compare_areas.md),
[`compare_indicators()`](compare_indicators.md), [`map()`](map.md),
[`overview()`](overview.md), [`population()`](population.md),
[`trends()`](trends.md)

## Examples

``` r
library(dplyr)
df <- create_test_data()

df_box <- df %>%
        filter(AreaType == "Local") %>%
        arrange(IndicatorName) %>%
        mutate(Timeperiod = rep(c("2011", "2012", "2013", "2014", "2015", "2016"),
                                each = 100))
p <- box_plots(df_box,
               timeperiod = Timeperiod,
               value = Value,
               title = "Title of chart",
               subtitle = "Boxplot over time",
               ylab = "Proportion (%)")
```
