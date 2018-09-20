data\_manipulation
================
Guojing Wu

import data
-----------

``` r
options(tibble.print_min = 3)

litters_data = read_csv("./data_import_examples/FAS_litters.csv",
  col_types = "ccddiiii")
litters_data = janitor::clean_names(litters_data)

pups_data = read_csv("./data_import_examples/FAS_pups.csv",
  col_types = "ciiiii")
pups_data = janitor::clean_names(pups_data)
```

select, remove and rename
-------------------------

``` r
select(litters_data, group, litter_number, gd0_weight, pups_born_alive)
```

    ## # A tibble: 49 x 4
    ##   group litter_number gd0_weight pups_born_alive
    ##   <chr> <chr>              <dbl>           <int>
    ## 1 Con7  #85                 19.7               3
    ## 2 Con7  #1/2/95/2           27                 8
    ## 3 Con7  #5/5/3/83/3-3       26                 6
    ## # ... with 46 more rows

``` r
select(litters_data, group:gd_of_birth)
```

    ## # A tibble: 49 x 5
    ##   group litter_number gd0_weight gd18_weight gd_of_birth
    ##   <chr> <chr>              <dbl>       <dbl>       <int>
    ## 1 Con7  #85                 19.7        34.7          20
    ## 2 Con7  #1/2/95/2           27          42            19
    ## 3 Con7  #5/5/3/83/3-3       26          41.4          19
    ## # ... with 46 more rows

``` r
select(litters_data, -pups_survive)
```

    ## # A tibble: 49 x 7
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>              <dbl>       <dbl>       <int>           <int>
    ## 1 Con7  #85                 19.7        34.7          20               3
    ## 2 Con7  #1/2/95/2           27          42            19               8
    ## 3 Con7  #5/5/3/83/3-3       26          41.4          19               6
    ## # ... with 46 more rows, and 1 more variable: pups_dead_birth <int>

``` r
select(litters_data, GROUP = group, LiTtEr_NuMbEr = litter_number)
```

    ## # A tibble: 49 x 2
    ##   GROUP LiTtEr_NuMbEr
    ##   <chr> <chr>        
    ## 1 Con7  #85          
    ## 2 Con7  #1/2/95/2    
    ## 3 Con7  #5/5/3/83/3-3
    ## # ... with 46 more rows

or you can just use rename

``` r
rename(litters_data, GROUP = group, LiTtEr_NuMbEr = litter_number)
```

    ## # A tibble: 49 x 8
    ##   GROUP LiTtEr_NuMbEr gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>              <dbl>       <dbl>       <int>           <int>
    ## 1 Con7  #85                 19.7        34.7          20               3
    ## 2 Con7  #1/2/95/2           27          42            19               8
    ## 3 Con7  #5/5/3/83/3-3       26          41.4          19               6
    ## # ... with 46 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>

choose a specific pattern

``` r
select(litters_data, starts_with("gd"))
```

    ## # A tibble: 49 x 3
    ##   gd0_weight gd18_weight gd_of_birth
    ##        <dbl>       <dbl>       <int>
    ## 1       19.7        34.7          20
    ## 2       27          42            19
    ## 3       26          41.4          19
    ## # ... with 46 more rows

Learning assessment
-------------------

``` r
select(pups_data, litter_number, sex, pd_ears)
```

    ## # A tibble: 313 x 3
    ##   litter_number   sex pd_ears
    ##   <chr>         <int>   <int>
    ## 1 #85               1       4
    ## 2 #85               1       4
    ## 3 #1/2/95/2         1       5
    ## # ... with 310 more rows
