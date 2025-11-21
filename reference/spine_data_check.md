# Check function for multiple values for an area in an indicator for spine chart

Check function for multiple values for an area in an indicator for spine
chart

## Usage

``` r
spine_data_check(data, indicator, area_code)
```

## Arguments

- data:

  a data frame to create the spine chart from. The data frame should
  contain records for all area types included in the chart (eg, if
  plotting for County & UA with a comparator of region and a median line
  for national, the data frame should contain records for all of these
  data). The minimum field requirements in the data frame are; value,
  count, area_code, indicator, timeperiod, polarity, significance,
  area_type. See below for the definitions of these fields

- indicator:

  unquoted field name for the field of the field containing the
  indicator labels. Take care as errors will occur where indicator
  labels are the same but data exist for multiple sub-categories (for
  example, sex or age)

- area_code:

  unquoted field name for the field where area codes are stored
  (local_area_code, median_line_area_code and comparator_area_code, if
  using, should all exist in this field)
