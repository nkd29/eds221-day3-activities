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
skim(toolik_biochem)
```


Table: Data summary

|                         |               |
|:------------------------|:--------------|
|Name                     |toolik_biochem |
|Number of rows           |154            |
|Number of columns        |45             |
|_______________________  |               |
|Column type frequency:   |               |
|character                |43             |
|difftime                 |1              |
|numeric                  |1              |
|________________________ |               |
|Group variables          |None           |


**Variable type: character**

|skim_variable         | n_missing| complete_rate| min| max| empty| n_unique| whitespace|
|:---------------------|---------:|-------------:|---:|---:|-----:|--------:|----------:|
|sort_chem             |         0|             1|   9|   9|     0|      154|          0|
|site                  |         0|             1|   5|  27|     0|       45|          0|
|date                  |         0|             1|   9|   9|     0|       34|          0|
|distance_km           |         0|             1|   1|   1|     0|        1|          0|
|elevation_m           |         0|             1|   1|   3|     0|       21|          0|
|description_treatment |         0|             1|   1|  23|     0|        7|          0|
|catsort               |         0|             1|   7|   7|     0|        1|          0|
|water_type            |         0|             1|   2|   2|     0|        4|          0|
|temp_c                |         0|             1|   1|   4|     0|       78|          0|
|cond_u_s              |         0|             1|   1|   5|     0|      140|          0|
|p_h                   |         0|             1|   1|   4|     0|      108|          0|
|alk_ueq_l             |         0|             1|   1|   4|     0|      138|          0|
|pco2_uatm             |         0|             1|   1|   5|     0|       12|          0|
|pch4_uatm             |         0|             1|   1|   6|     0|       12|          0|
|co2_u_m               |         0|             1|   1|   4|     0|       12|          0|
|ch4_u_m               |         0|             1|   1|   8|     0|       12|          0|
|doc_u_m               |         0|             1|   1|   4|     0|      129|          0|
|nh4_u_m               |         0|             1|   1|   5|     0|      126|          0|
|po4_u_m               |         0|             1|   1|   7|     0|      126|          0|
|no3_u_m               |         0|             1|   1|   7|     0|      137|          0|
|tdn_u_m               |         0|             1|   1|   4|     0|       87|          0|
|tdp_u_m               |         0|             1|   1|   1|     0|        1|          0|
|pc_ug_l               |         0|             1|   1|   4|     0|      114|          0|
|pn_ug_l               |         0|             1|   1|   4|     0|      112|          0|
|pp_u_m                |         0|             1|   1|   3|     0|        7|          0|
|ca_u_m                |         0|             1|   1|   5|     0|      143|          0|
|mg_u_m                |         0|             1|   1|   5|     0|      141|          0|
|na_u_m                |         0|             1|   1|   4|     0|      121|          0|
|k_u_m                 |         0|             1|   1|   5|     0|      138|          0|
|si_u_m                |         0|             1|   1|   5|     0|      123|          0|
|so4_u_m               |         0|             1|   1|   1|     0|        1|          0|
|cl_u_m                |         0|             1|   1|   1|     0|        1|          0|
|oxygen_mg_l           |         0|             1|   1|   1|     0|        1|          0|
|chla_ug_l             |         0|             1|   1|   3|     0|       29|          0|
|phaeopigment_ug_l     |         0|             1|   1|   3|     0|       22|          0|
|chla_raw_ug_l         |         0|             1|   1|   3|     0|       32|          0|
|secchi_m              |         0|             1|   1|   1|     0|        1|          0|
|thaw_depth_cm         |         0|             1|   1|   4|     0|       12|          0|
|x5cm_soil_temp_c      |         0|             1|   1|   3|     0|       15|          0|
|x10cm_soil_temp_c     |         0|             1|   1|   3|     0|       13|          0|
|well_height_cm        |         0|             1|   1|   4|     0|       10|          0|
|discharge_lsec        |         0|             1|   1|   5|     0|        4|          0|
|stage_cm              |         0|             1|   1|   4|     0|       51|          0|


**Variable type: difftime**

|skim_variable | n_missing| complete_rate|min        |max        |median     | n_unique|
|:-------------|---------:|-------------:|:----------|:----------|:----------|--------:|
|time_hr_dst   |         0|             1|17400 secs |74580 secs |45090 secs |      121|


**Variable type: numeric**

|skim_variable | n_missing| complete_rate| mean|   sd|   p0|  p25|  p50|  p75| p100|hist                                     |
|:-------------|---------:|-------------:|----:|----:|----:|----:|----:|----:|----:|:----------------------------------------|
|depth_m       |         0|             1| 0.02| 0.03| 0.01| 0.01| 0.01| 0.01|  0.1|▇▁▁▁▁ |

```r
inlet_biochem <- toolik_biochem %>% select(p_h,doc_u_m,tdn_u_m,site) %>% filter(site=='Toolik Inlet')
inlet_biochem
```

```
## # A tibble: 26 x 4
##    p_h   doc_u_m tdn_u_m site        
##    <chr> <chr>   <chr>   <chr>       
##  1 5.3   995     24.3    Toolik Inlet
##  2 5.86  917     20.5    Toolik Inlet
##  3 5.87  803     20      Toolik Inlet
##  4 6.75  731     18.5    Toolik Inlet
##  5 6.18  676     17      Toolik Inlet
##  6 7.53  396     10.5    Toolik Inlet
##  7 7.56  338     10.6    Toolik Inlet
##  8 7.41  244     11.1    Toolik Inlet
##  9 7.52  451     10.5    Toolik Inlet
## 10 7.86  246     13.5    Toolik Inlet
## # ... with 16 more rows
```

