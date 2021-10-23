---
title: "conditionals_loops"
author: "Nikhil D."
date: "10/23/2021"
output:  
  html_document:
    keep_md: true
---
# SETUP


# TASK 1

```r
# Old example
species <- c("dog", "elephant", "goat", "dog", "dog", "elephant")

# And their respective ages in human years:
age_human <- c(3, 8, 4, 6, 12, 18)

# Convert ages to "animal years" using the following:
# 1 human year = 7 in dog years
# 1 human year = 0.88 in elephant years
# 1 human year = 4.7 in goat years

for (i in seq_along(species)) {
  if (species[i] == "dog") {
    animal_age <- age_human[i] * 7
  } else if (species[i] == "elephant") {
    animal_age <- age_human[i] * 0.88
  } else if (species[i] == "goat") {
    animal_age <- age_human[i] * 4.7
  }
  print(paste("The",age_human[i],"year old",species[i],"is actually",round(animal_age),"in",species[i],"years"))
}
```

```
## [1] "The 3 year old dog is actually 21 in dog years"
## [1] "The 8 year old elephant is actually 7 in elephant years"
## [1] "The 4 year old goat is actually 19 in goat years"
## [1] "The 6 year old dog is actually 42 in dog years"
## [1] "The 12 year old dog is actually 84 in dog years"
## [1] "The 18 year old elephant is actually 16 in elephant years"
```

```r
# Task 1
pm2_5 <- 1220

if (pm2_5 < 100) {
  risk <- "Low to moderate risk"
} else if (pm2_5 >=100 & pm2_5<150) {
    risk <- "Unhealthy for sensitive people"
} else if (pm2_5>= 150) {
    risk <- "Health risk present"
} 
print(risk)
```

```
## [1] "Health risk present"
```


# TASK 2


```r
# Task 2

species <- "blue monkey whale"

species
```

```
## [1] "blue monkey whale"
```

```r
if (stringr::str_detect(species,'whale') == TRUE) {
  print("WHALE IS FOUND")
} 
```

```
## [1] "WHALE IS FOUND"
```

# TASK 3

```r
# Task 3


max_airtemp_c <- 2.1

if (max_airtemp_c > 27) {
  print("Temperature TOo high")
} else print("Temperature OK")
```

```
## [1] "Temperature OK"
```

# TASK 4

```r
# Task 4

base_burrito <- 6.50

main_ingredent <- "steak"

if (main_ingredent=="veggie") {
  cost <- base_burrito
} else if (main_ingredent=="chicken"){
  cost <- base_burrito+3
} else if (main_ingredent=="steak"){
  cost <- base_burrito+3.25
  }
print(cost)
```

```
## [1] 9.75
```

# TASK 5

```r
# Task 5

# counts of different fish types in a fish tank

fish_species <- c("goldfish", "tetras", "guppies", "mollies")
fish_count <- c(8,10,12,23)

for (i in seq(fish_count)) {
  print(paste(100*round(fish_count[i]/sum(fish_count),2),"% of total fish in the tank are",fish_species[i]))
}
```

```
## [1] "15 % of total fish in the tank are goldfish"
## [1] "19 % of total fish in the tank are tetras"
## [1] "23 % of total fish in the tank are guppies"
## [1] "43 % of total fish in the tank are mollies"
```
# TASK 6

```r
# Task 6

for (i in seq(month.name)){
  print(paste(month.name[i],"is month",i))
}
```

```
## [1] "January is month 1"
## [1] "February is month 2"
## [1] "March is month 3"
## [1] "April is month 4"
## [1] "May is month 5"
## [1] "June is month 6"
## [1] "July is month 7"
## [1] "August is month 8"
## [1] "September is month 9"
## [1] "October is month 10"
## [1] "November is month 11"
## [1] "December is month 12"
```
