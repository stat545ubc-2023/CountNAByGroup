
<!-- README.md is generated from README.Rmd. Please edit that file -->

# CountNAByGroup

<!-- badges: start -->
<!-- badges: end -->

The goal of CountNAByGroup is to create a function to count missing
values for all columns in the dataset by group. The name of the function
is `count_all_missing_by_group()`

Given a data frame `data` and a column `group`,
`count_all_missing_by_group()` creates a new data frame with one row per
level of `group`. The first column of the output data frame contains the
levels of `group`, and the rest of the columns contain the number of
missing values for all columns in `data` except `group`.

## Installation

You can install the development version of CountNAByGroup from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("stat545ubc-2023/CountNAByGroup")
```

## Example

This example computes the number of missing values in the `airquality`
dataset grouped by the `Month` column.

``` r
library(CountNAByGroup) # load our package
library(datasets) # load the library containing airquality data
count_all_missing_by_group(airquality, Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

This example has the same output as the last example, but shows off an
alternative way of invoking the `count_all_missing_by_group()`: piping
the dataset into the function.

``` r
airquality |> count_all_missing_by_group(Month) 
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```
