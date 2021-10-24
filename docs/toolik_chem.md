---
title: "toolik_chem"
author: "Nikhil D."
date: "10/23/2021"
output:  
  html_document:
    keep_md: true
---




```r
toolik_biochem <- read_csv(here::here("data", "2011_Kling_Akchem.csv")) %>% clean_names
```

```
## Rows: 154 Columns: 45
```

```
## -- Column specification --------------------------------------------------------
## Delimiter: ","
## chr  (43): SortChem, Site, Date, Distance_km, Elevation_m, Description_Treat...
## dbl   (1): Depth_m
## time  (1): Time_hr_dst
```

```
## 
## i Use `spec()` to retrieve the full column specification for this data.
## i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
# skim(toolik_biochem)

inlet_biochem <- toolik_biochem %>% select(p_h,doc_u_m,tdn_u_m,site) %>% filter(site=='Toolik Inlet')
inlet_biochem2 <- toolik_biochem %>% filter(site=='Toolik Inlet') %>% select(doc_u_m,tdn_u_m) 

# change character vectors to numerics
for (i in c(1,2,3)){
  inlet_biochem[[i]] <- as.numeric(inlet_biochem[[i]])
}
```

```
## Warning: NAs introduced by coercion
```

```r
inlet_biochem
```

```
## # A tibble: 26 x 4
##      p_h doc_u_m tdn_u_m site        
##    <dbl>   <dbl>   <dbl> <chr>       
##  1  5.3      995    24.3 Toolik Inlet
##  2  5.86     917    20.5 Toolik Inlet
##  3  5.87     803    20   Toolik Inlet
##  4  6.75     731    18.5 Toolik Inlet
##  5  6.18     676    17   Toolik Inlet
##  6  7.53     396    10.5 Toolik Inlet
##  7  7.56     338    10.6 Toolik Inlet
##  8  7.41     244    11.1 Toolik Inlet
##  9  7.52     451    10.5 Toolik Inlet
## 10  7.86     246    13.5 Toolik Inlet
## # ... with 16 more rows
```

```r
# calculate means
for (i in c(1,2,3)) {
  print(mean((inlet_biochem[[i]]),na.rm = TRUE))
}
```

```
## [1] 7.063182
## [1] 409.9615
## [1] 13.36538
```

```r
apply(X = inlet_biochem, MARGIN = 2, FUN = mean)
```

```
## Warning in mean.default(newX[, i], ...): argument is not numeric or logical:
## returning NA
```

```
## Warning in mean.default(newX[, i], ...): argument is not numeric or logical:
## returning NA

## Warning in mean.default(newX[, i], ...): argument is not numeric or logical:
## returning NA

## Warning in mean.default(newX[, i], ...): argument is not numeric or logical:
## returning NA
```

```
##     p_h doc_u_m tdn_u_m    site 
##      NA      NA      NA      NA
```

```r
# 
# inlet_biochem %>% 
#   summarize(across(where(is.numeric), mean, na.rm = TRUE))




apply(X = mtcars, MARGIN = 2, FUN = mean)
```

```
##        mpg        cyl       disp         hp       drat         wt       qsec 
##  20.090625   6.187500 230.721875 146.687500   3.596563   3.217250  17.848750 
##         vs         am       gear       carb 
##   0.437500   0.406250   3.687500   2.812500
```

```r
skim(mtcars)
```


Table: Data summary

|                         |       |
|:------------------------|:------|
|Name                     |mtcars |
|Number of rows           |32     |
|Number of columns        |11     |
|_______________________  |       |
|Column type frequency:   |       |
|numeric                  |11     |
|________________________ |       |
|Group variables          |None   |


**Variable type: numeric**

|skim_variable | n_missing| complete_rate|   mean|     sd|    p0|    p25|    p50|    p75|   p100|hist                                     |
|:-------------|---------:|-------------:|------:|------:|-----:|------:|------:|------:|------:|:----------------------------------------|
|mpg           |         0|             1|  20.09|   6.03| 10.40|  15.43|  19.20|  22.80|  33.90|▃▇▅▁▂ |
|cyl           |         0|             1|   6.19|   1.79|  4.00|   4.00|   6.00|   8.00|   8.00|▆▁▃▁▇ |
|disp          |         0|             1| 230.72| 123.94| 71.10| 120.83| 196.30| 326.00| 472.00|▇▃▃▃▂ |
|hp            |         0|             1| 146.69|  68.56| 52.00|  96.50| 123.00| 180.00| 335.00|▇▇▆▃▁ |
|drat          |         0|             1|   3.60|   0.53|  2.76|   3.08|   3.70|   3.92|   4.93|▇▃▇▅▁ |
|wt            |         0|             1|   3.22|   0.98|  1.51|   2.58|   3.33|   3.61|   5.42|▃▃▇▁▂ |
|qsec          |         0|             1|  17.85|   1.79| 14.50|  16.89|  17.71|  18.90|  22.90|▃▇▇▂▁ |
|vs            |         0|             1|   0.44|   0.50|  0.00|   0.00|   0.00|   1.00|   1.00|▇▁▁▁▆ |
|am            |         0|             1|   0.41|   0.50|  0.00|   0.00|   0.00|   1.00|   1.00|▇▁▁▁▆ |
|gear          |         0|             1|   3.69|   0.74|  3.00|   3.00|   4.00|   4.00|   5.00|▇▁▆▁▂ |
|carb          |         0|             1|   2.81|   1.62|  1.00|   2.00|   2.00|   4.00|   8.00|▇▂▅▁▁ |

