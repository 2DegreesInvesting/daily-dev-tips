
<!-- README.md is generated from README.Rmd. Please edit that file -->

# daily-dev-tips

<!-- badges: start -->
<!-- badges: end -->

The goal of daily-dev-tips is to support the Slack channel
\#daily-dev-tips.

``` r
library(tidyverse, warn.conflicts = FALSE)
#> ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
#> ✓ ggplot2 3.3.5     ✓ purrr   0.3.4
#> ✓ tibble  3.1.6     ✓ dplyr   1.0.8
#> ✓ tidyr   1.2.0     ✓ stringr 1.4.0
#> ✓ readr   2.1.2     ✓ forcats 0.5.1
#> ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
#> x dplyr::filter() masks stats::filter()
#> x dplyr::lag()    masks stats::lag()
library(googlesheets4)
```

``` r
url <- "https://docs.google.com/spreadsheets/d/1sFF28BcWonrnDriiV_42uSjiYktxaTMFHsKCjDL1OcQ/edit#gid=0"
```

``` r
curators <- read_sheet(url, sheet = "curators") %>% 
  filter(!is.na(curator))
#> ! Using an auto-discovered, cached token.
#>   To suppress this message, modify your code or options to clearly consent to
#>   the use of a cached token.
#>   See gargle's "Non-interactive auth" vignette for more details:
#>   <https://gargle.r-lib.org/articles/non-interactive-auth.html>
#> ℹ The googlesheets4 package is using a cached token for
#>   'maurolepore@gmail.com'.
#> ✓ Reading from "Dev Tip a Day".
#> ✓ Range ''curators''.

curators
#> # A tibble: 4 × 3
#>   week                curator replacement
#>   <dttm>              <chr>   <chr>      
#> 1 2022-04-11 00:00:00 Mauro   Jackson    
#> 2 2022-04-18 00:00:00 Jackson Linda      
#> 3 2022-04-25 00:00:00 Linda   Mirja      
#> 4 2022-05-02 00:00:00 Mirja   <NA>
```

``` r
disclaimer <- 2
tips <- read_sheet(url, sheet = "tips", skip = disclaimer)
#> ✓ Reading from "Dev Tip a Day".
#> ✓ Range ''tips'!3:5000000'.

tips
#> # A tibble: 5 × 3
#>   date                curator tip                                               
#>   <dttm>              <chr>   <chr>                                             
#> 1 2022-04-11 00:00:00 mauro   "To get 1:1 help on any coding challenge you have…
#> 2 2022-04-12 00:00:00 mauro   "To ask for help with a bug, create a reproducibl…
#> 3 2022-04-13 00:00:00 mauro   "When cloning a repository from GitHub use the SS…
#> 4 2022-04-14 00:00:00 mauro   "You can use all of the most popular R packages f…
#> 5 2022-04-15 00:00:00 mauro   "To work with Git and GitHub you don’t need a ter…
```
