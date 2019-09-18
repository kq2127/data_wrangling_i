Data Import
================
Kristal Quispe
9/17/2019

\#\#Load in the litters data

``` r
litters_data = read_csv(file="./data/FAS_litters.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   Group = col_character(),
    ##   `Litter Number` = col_character(),
    ##   `GD0 weight` = col_double(),
    ##   `GD18 weight` = col_double(),
    ##   `GD of Birth` = col_double(),
    ##   `Pups born alive` = col_double(),
    ##   `Pups dead @ birth` = col_double(),
    ##   `Pups survive` = col_double()
    ## )

``` r
litters_data = janitor::clean_names(litters_data)
```

## The package::function syntax lets you use a function from a package without loading the whole library. That’s really helpful, because some packages have functions with the same name (e.g. dplyr::filter and stats::filter), and R has to choose which one you mean. In general, only load the packages you need to prevent this kind of confusion

\#\#Load in the pups data

``` r
pups_data = read_csv("./data/FAS_pups.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Litter Number` = col_character(),
    ##   Sex = col_double(),
    ##   `PD ears` = col_double(),
    ##   `PD eyes` = col_double(),
    ##   `PD pivot` = col_double(),
    ##   `PD walk` = col_double()
    ## )

``` r
puppups_data = janitor::clean_names(pups_data)
```

## Play with Column parsing

``` r
litters_data = read_csv(file = "./data/FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  )
)
```

\#\#Read in an excel file…

``` r
mlb11_data = 
  read_excel(
    path = "./data/mlb11.xlsx",
    range = "A1:D7")

mlb11_data = read_excel(path = "./data/mlb11.xlsx")
```

## Read in SAS…

``` r
pulse_data = haven::read_sas("./data/public_pulse_data.sas7bdat")
```

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax
for authoring HTML, PDF, and MS Word documents. For more details on
using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document. You can embed an R code chunk like this:

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

## Including Plots

You can also embed plots, for example:

![](data_import_files/figure-gfm/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
