Actividad Grupal - Dyplr
================
GRUPO 19
14/1/2022

# Ejercicios

### Instalamos el paquete “tidyverse” y “nycflights13”

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.5     v dplyr   1.0.7
    ## v tidyr   1.1.4     v stringr 1.4.0
    ## v readr   2.1.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(nycflights13)
glimpse(flights)
```

    ## Rows: 336,776
    ## Columns: 19
    ## $ year           <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2~
    ## $ month          <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1~
    ## $ day            <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1~
    ## $ dep_time       <int> 517, 533, 542, 544, 554, 554, 555, 557, 557, 558, 558, ~
    ## $ sched_dep_time <int> 515, 529, 540, 545, 600, 558, 600, 600, 600, 600, 600, ~
    ## $ dep_delay      <dbl> 2, 4, 2, -1, -6, -4, -5, -3, -3, -2, -2, -2, -2, -2, -1~
    ## $ arr_time       <int> 830, 850, 923, 1004, 812, 740, 913, 709, 838, 753, 849,~
    ## $ sched_arr_time <int> 819, 830, 850, 1022, 837, 728, 854, 723, 846, 745, 851,~
    ## $ arr_delay      <dbl> 11, 20, 33, -18, -25, 12, 19, -14, -8, 8, -2, -3, 7, -1~
    ## $ carrier        <chr> "UA", "UA", "AA", "B6", "DL", "UA", "B6", "EV", "B6", "~
    ## $ flight         <int> 1545, 1714, 1141, 725, 461, 1696, 507, 5708, 79, 301, 4~
    ## $ tailnum        <chr> "N14228", "N24211", "N619AA", "N804JB", "N668DN", "N394~
    ## $ origin         <chr> "EWR", "LGA", "JFK", "JFK", "LGA", "EWR", "EWR", "LGA",~
    ## $ dest           <chr> "IAH", "IAH", "MIA", "BQN", "ATL", "ORD", "FLL", "IAD",~
    ## $ air_time       <dbl> 227, 227, 160, 183, 116, 150, 158, 53, 140, 138, 149, 1~
    ## $ distance       <dbl> 1400, 1416, 1089, 1576, 762, 719, 1065, 229, 944, 733, ~
    ## $ hour           <dbl> 5, 5, 5, 5, 6, 5, 6, 6, 6, 6, 6, 6, 6, 6, 6, 5, 6, 6, 6~
    ## $ minute         <dbl> 15, 29, 40, 45, 0, 58, 0, 0, 0, 0, 0, 0, 0, 0, 0, 59, 0~
    ## $ time_hour      <dttm> 2013-01-01 05:00:00, 2013-01-01 05:00:00, 2013-01-01 0~

## Ejercicios Parte 9.1 - Filter

### 1. Encuentra todos los vuelos que

### Tuvieron un retraso de llegada de dos o más horas

``` r
filter(flights, arr_delay >= 120)
```

    ## # A tibble: 10,200 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      811            630       101     1047            830
    ##  2  2013     1     1      848           1835       853     1001           1950
    ##  3  2013     1     1      957            733       144     1056            853
    ##  4  2013     1     1     1114            900       134     1447           1222
    ##  5  2013     1     1     1505           1310       115     1638           1431
    ##  6  2013     1     1     1525           1340       105     1831           1626
    ##  7  2013     1     1     1549           1445        64     1912           1656
    ##  8  2013     1     1     1558           1359       119     1718           1515
    ##  9  2013     1     1     1732           1630        62     2028           1825
    ## 10  2013     1     1     1803           1620       103     2008           1750
    ## # ... with 10,190 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### Volaron a Houston (IAH o HOU)

``` r
dest_gal <- c("IAH", "HOU")
filter(flights,(dest %in% dest_gal))
```

    ## # A tibble: 9,313 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      623            627        -4      933            932
    ##  4  2013     1     1      728            732        -4     1041           1038
    ##  5  2013     1     1      739            739         0     1104           1038
    ##  6  2013     1     1      908            908         0     1228           1219
    ##  7  2013     1     1     1028           1026         2     1350           1339
    ##  8  2013     1     1     1044           1045        -1     1352           1351
    ##  9  2013     1     1     1114            900       134     1447           1222
    ## 10  2013     1     1     1205           1200         5     1503           1505
    ## # ... with 9,303 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### Fueron operados por United, American o Delta

``` r
airlines
```

    ## # A tibble: 16 x 2
    ##    carrier name                       
    ##    <chr>   <chr>                      
    ##  1 9E      Endeavor Air Inc.          
    ##  2 AA      American Airlines Inc.     
    ##  3 AS      Alaska Airlines Inc.       
    ##  4 B6      JetBlue Airways            
    ##  5 DL      Delta Air Lines Inc.       
    ##  6 EV      ExpressJet Airlines Inc.   
    ##  7 F9      Frontier Airlines Inc.     
    ##  8 FL      AirTran Airways Corporation
    ##  9 HA      Hawaiian Airlines Inc.     
    ## 10 MQ      Envoy Air                  
    ## 11 OO      SkyWest Airlines Inc.      
    ## 12 UA      United Air Lines Inc.      
    ## 13 US      US Airways Inc.            
    ## 14 VX      Virgin America             
    ## 15 WN      Southwest Airlines Co.     
    ## 16 YV      Mesa Airlines Inc.

``` r
dest_galD <- c("UA", "AA","DL")
filter(flights, (carrier %in% dest_galD))
```

    ## # A tibble: 139,504 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      554            600        -6      812            837
    ##  5  2013     1     1      554            558        -4      740            728
    ##  6  2013     1     1      558            600        -2      753            745
    ##  7  2013     1     1      558            600        -2      924            917
    ##  8  2013     1     1      558            600        -2      923            937
    ##  9  2013     1     1      559            600        -1      941            910
    ## 10  2013     1     1      559            600        -1      854            902
    ## # ... with 139,494 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### Partieron en invierno del hemisferio sur (julio, agosto y septiembre)

``` r
dest_galD <- c(7,8,9)
filter(flights, (month %in% dest_galD))
```

    ## # A tibble: 86,326 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7     1        1           2029       212      236           2359
    ##  2  2013     7     1        2           2359         3      344            344
    ##  3  2013     7     1       29           2245       104      151              1
    ##  4  2013     7     1       43           2130       193      322             14
    ##  5  2013     7     1       44           2150       174      300            100
    ##  6  2013     7     1       46           2051       235      304           2358
    ##  7  2013     7     1       48           2001       287      308           2305
    ##  8  2013     7     1       58           2155       183      335             43
    ##  9  2013     7     1      100           2146       194      327             30
    ## 10  2013     7     1      100           2245       135      337            135
    ## # ... with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### Llegaron más de dos horas tarde, pero no salieron tarde

``` r
filter(flights,  arr_delay > 120 & dep_delay <= 0)
```

    ## # A tibble: 29 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1    27     1419           1420        -1     1754           1550
    ##  2  2013    10     7     1350           1350         0     1736           1526
    ##  3  2013    10     7     1357           1359        -2     1858           1654
    ##  4  2013    10    16      657            700        -3     1258           1056
    ##  5  2013    11     1      658            700        -2     1329           1015
    ##  6  2013     3    18     1844           1847        -3       39           2219
    ##  7  2013     4    17     1635           1640        -5     2049           1845
    ##  8  2013     4    18      558            600        -2     1149            850
    ##  9  2013     4    18      655            700        -5     1213            950
    ## 10  2013     5    22     1827           1830        -3     2217           2010
    ## # ... with 19 more rows, and 11 more variables: arr_delay <dbl>, carrier <chr>,
    ## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>,
    ## #   distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### Se retrasaron por lo menos una hora, pero repusieron más de 30 minutos en vuelo

``` r
df<- select(flights,ends_with("delay"))
df<- mutate(df, tiemporecupaerado= flights$dep_delay-flights$arr_delay)
filter(df,dep_delay>=60 & arr_delay < 30)
```

    ## # A tibble: 206 x 3
    ##    dep_delay arr_delay tiemporecupaerado
    ##        <dbl>     <dbl>             <dbl>
    ##  1        65        28                37
    ##  2        65         1                64
    ##  3        60        24                36
    ##  4        79        28                51
    ##  5        73        23                50
    ##  6        60        26                34
    ##  7        66        22                44
    ##  8        68        17                51
    ##  9        61        21                40
    ## 10        61        28                33
    ## # ... with 196 more rows

### Partieron entre la medianoche y las 6 a.m. (incluyente)

``` r
filter(flights,  dep_time >= 0 & dep_time <= 600)
```

    ## # A tibble: 9,344 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ... with 9,334 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 2. Otra función de dplyr que es útil para usar filtros es between(). ¿Qué hace? ¿Puedes usarla para simplificar el código necesario para responder a los desafíos anteriores?

``` r
filter(flights, between(month, 7, 9))
```

    ## # A tibble: 86,326 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7     1        1           2029       212      236           2359
    ##  2  2013     7     1        2           2359         3      344            344
    ##  3  2013     7     1       29           2245       104      151              1
    ##  4  2013     7     1       43           2130       193      322             14
    ##  5  2013     7     1       44           2150       174      300            100
    ##  6  2013     7     1       46           2051       235      304           2358
    ##  7  2013     7     1       48           2001       287      308           2305
    ##  8  2013     7     1       58           2155       183      335             43
    ##  9  2013     7     1      100           2146       194      327             30
    ## 10  2013     7     1      100           2245       135      337            135
    ## # ... with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 3. ¿Cuántos vuelos tienen datos faltantes en horario_salida? ¿Qué otras variables tienen valores faltantes? ¿Qué representan estas filas?

``` r
filter(flights, is.na(dep_time))
```

    ## # A tibble: 8,255 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1       NA           1630        NA       NA           1815
    ##  2  2013     1     1       NA           1935        NA       NA           2240
    ##  3  2013     1     1       NA           1500        NA       NA           1825
    ##  4  2013     1     1       NA            600        NA       NA            901
    ##  5  2013     1     2       NA           1540        NA       NA           1747
    ##  6  2013     1     2       NA           1620        NA       NA           1746
    ##  7  2013     1     2       NA           1355        NA       NA           1459
    ##  8  2013     1     2       NA           1420        NA       NA           1644
    ##  9  2013     1     2       NA           1321        NA       NA           1536
    ## 10  2013     1     2       NA           1545        NA       NA           1910
    ## # ... with 8,245 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
filter(flights, is.na(dep_delay))
```

    ## # A tibble: 8,255 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1       NA           1630        NA       NA           1815
    ##  2  2013     1     1       NA           1935        NA       NA           2240
    ##  3  2013     1     1       NA           1500        NA       NA           1825
    ##  4  2013     1     1       NA            600        NA       NA            901
    ##  5  2013     1     2       NA           1540        NA       NA           1747
    ##  6  2013     1     2       NA           1620        NA       NA           1746
    ##  7  2013     1     2       NA           1355        NA       NA           1459
    ##  8  2013     1     2       NA           1420        NA       NA           1644
    ##  9  2013     1     2       NA           1321        NA       NA           1536
    ## 10  2013     1     2       NA           1545        NA       NA           1910
    ## # ... with 8,245 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
filter(flights, is.na(arr_time))
```

    ## # A tibble: 8,713 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     2016           1930        46       NA           2220
    ##  2  2013     1     1       NA           1630        NA       NA           1815
    ##  3  2013     1     1       NA           1935        NA       NA           2240
    ##  4  2013     1     1       NA           1500        NA       NA           1825
    ##  5  2013     1     1       NA            600        NA       NA            901
    ##  6  2013     1     2     2041           2045        -4       NA           2359
    ##  7  2013     1     2     2145           2129        16       NA             33
    ##  8  2013     1     2       NA           1540        NA       NA           1747
    ##  9  2013     1     2       NA           1620        NA       NA           1746
    ## 10  2013     1     2       NA           1355        NA       NA           1459
    ## # ... with 8,703 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
filter(flights, is.na(arr_delay))
```

    ## # A tibble: 9,430 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     1525           1530        -5     1934           1805
    ##  2  2013     1     1     1528           1459        29     2002           1647
    ##  3  2013     1     1     1740           1745        -5     2158           2020
    ##  4  2013     1     1     1807           1738        29     2251           2103
    ##  5  2013     1     1     1939           1840        59       29           2151
    ##  6  2013     1     1     1952           1930        22     2358           2207
    ##  7  2013     1     1     2016           1930        46       NA           2220
    ##  8  2013     1     1       NA           1630        NA       NA           1815
    ##  9  2013     1     1       NA           1935        NA       NA           2240
    ## 10  2013     1     1       NA           1500        NA       NA           1825
    ## # ... with 9,420 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
filter(flights, is.na(tailnum))
```

    ## # A tibble: 2,512 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     2       NA           1545        NA       NA           1910
    ##  2  2013     1     2       NA           1601        NA       NA           1735
    ##  3  2013     1     3       NA            857        NA       NA           1209
    ##  4  2013     1     3       NA            645        NA       NA            952
    ##  5  2013     1     4       NA            845        NA       NA           1015
    ##  6  2013     1     4       NA           1830        NA       NA           2044
    ##  7  2013     1     5       NA            840        NA       NA           1001
    ##  8  2013     1     7       NA            820        NA       NA            958
    ##  9  2013     1     8       NA           1645        NA       NA           1838
    ## 10  2013     1     9       NA            755        NA       NA           1012
    ## # ... with 2,502 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
filter(flights, is.na(air_time))
```

    ## # A tibble: 9,430 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     1525           1530        -5     1934           1805
    ##  2  2013     1     1     1528           1459        29     2002           1647
    ##  3  2013     1     1     1740           1745        -5     2158           2020
    ##  4  2013     1     1     1807           1738        29     2251           2103
    ##  5  2013     1     1     1939           1840        59       29           2151
    ##  6  2013     1     1     1952           1930        22     2358           2207
    ##  7  2013     1     1     2016           1930        46       NA           2220
    ##  8  2013     1     1       NA           1630        NA       NA           1815
    ##  9  2013     1     1       NA           1935        NA       NA           2240
    ## 10  2013     1     1       NA           1500        NA       NA           1825
    ## # ... with 9,420 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 4. ¿Por qué NA^0 no es faltante? ¿Por qué NA \| TRUE no es faltante? ¿Por qué FALSE & NA no es faltante? ¿Puedes descubrir la regla general? (¡NA \* 0 es un contraejemplo complicado!)

``` r
x <- c(NA) 
# La función `is.na()` determina si falta un valor y devuelve un valor lógico `TRUE` en los casos en que es NA (Not Available).
x^0
```

    ## [1] 1

``` r
# Dado que el NA podría tomar cualquier valor, es práctico pensar que cualquier número (aunque sea muy grande) a la potencia cero es igual a 1.
x | TRUE
```

    ## [1] TRUE

``` r
# Es igual a TRUE pues el NA se entiende como un valor lógico (`TRUE` or `FALSE`) y por lógica proposicional `TRUE` | `TRUE`  y  `FALSE` | `TRUE` es siempre igual a `TRUE`.
x & FALSE
```

    ## [1] FALSE

``` r
# Es igual a `TRUE` pues el NA se entiende como un valor lógico (`TRUE` or `FALSE`) y por lógica proposicional `TRUE`&`FALSE` y `FALSE`&`FALSE` es siempre `FALSE`.
```

## Ejercicios Parte 9.2 - Arrange

### 1.¿Cómo podrías usar arrange() para ordenar todos los valores faltantes al comienzo? (Sugerencia: usa is.na()).

``` r
na<-arrange(flights,desc(is.na(air_time)))
na
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     1525           1530        -5     1934           1805
    ##  2  2013     1     1     1528           1459        29     2002           1647
    ##  3  2013     1     1     1740           1745        -5     2158           2020
    ##  4  2013     1     1     1807           1738        29     2251           2103
    ##  5  2013     1     1     1939           1840        59       29           2151
    ##  6  2013     1     1     1952           1930        22     2358           2207
    ##  7  2013     1     1     2016           1930        46       NA           2220
    ##  8  2013     1     1       NA           1630        NA       NA           1815
    ##  9  2013     1     1       NA           1935        NA       NA           2240
    ## 10  2013     1     1       NA           1500        NA       NA           1825
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 2.Ordena vuelos para encontrar los vuelos más retrasados. Encuentra los vuelos que salieron más temprano.

``` r
tarde<-arrange(flights, dep_delay)
tarde
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013    12     7     2040           2123       -43       40           2352
    ##  2  2013     2     3     2022           2055       -33     2240           2338
    ##  3  2013    11    10     1408           1440       -32     1549           1559
    ##  4  2013     1    11     1900           1930       -30     2233           2243
    ##  5  2013     1    29     1703           1730       -27     1947           1957
    ##  6  2013     8     9      729            755       -26     1002            955
    ##  7  2013    10    23     1907           1932       -25     2143           2143
    ##  8  2013     3    30     2030           2055       -25     2213           2250
    ##  9  2013     3     2     1431           1455       -24     1601           1631
    ## 10  2013     5     5      934            958       -24     1225           1309
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
temprano<-arrange(flights,  -dep_delay)
temprano
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     6    27      959           1900       899     1236           2226
    ##  9  2013     7    22     2257            759       898      121           1026
    ## 10  2013    12     5      756           1700       896     1058           2020
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 3.Ordena vuelos para encontrar los vuelos más rápidos (que viajaron a mayor velocidad).

``` r
velocidad<-arrange(flights,-(distance/air_time))
velocidad
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     5    25     1709           1700         9     1923           1937
    ##  2  2013     7     2     1558           1513        45     1745           1719
    ##  3  2013     5    13     2040           2025        15     2225           2226
    ##  4  2013     3    23     1914           1910         4     2045           2043
    ##  5  2013     1    12     1559           1600        -1     1849           1917
    ##  6  2013    11    17      650            655        -5     1059           1150
    ##  7  2013     2    21     2355           2358        -3      412            438
    ##  8  2013    11    17      759            800        -1     1212           1255
    ##  9  2013    11    16     2003           1925        38       17             36
    ## 10  2013    11    16     2349           2359       -10      402            440
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 4.¿Cuáles vuelos viajaron más lejos? ¿Cuál viajó más cerca?

``` r
lejos<-arrange(flights, -(distance))
lejos
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      857            900        -3     1516           1530
    ##  2  2013     1     2      909            900         9     1525           1530
    ##  3  2013     1     3      914            900        14     1504           1530
    ##  4  2013     1     4      900            900         0     1516           1530
    ##  5  2013     1     5      858            900        -2     1519           1530
    ##  6  2013     1     6     1019            900        79     1558           1530
    ##  7  2013     1     7     1042            900       102     1620           1530
    ##  8  2013     1     8      901            900         1     1504           1530
    ##  9  2013     1     9      641            900      1301     1242           1530
    ## 10  2013     1    10      859            900        -1     1449           1530
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
cerca<-arrange(flights, (distance))
cerca
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7    27       NA            106        NA       NA            245
    ##  2  2013     1     3     2127           2129        -2     2222           2224
    ##  3  2013     1     4     1240           1200        40     1333           1306
    ##  4  2013     1     4     1829           1615       134     1937           1721
    ##  5  2013     1     4     2128           2129        -1     2218           2224
    ##  6  2013     1     5     1155           1200        -5     1241           1306
    ##  7  2013     1     6     2125           2129        -4     2224           2224
    ##  8  2013     1     7     2124           2129        -5     2212           2224
    ##  9  2013     1     8     2127           2130        -3     2304           2225
    ## 10  2013     1     9     2126           2129        -3     2217           2224
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

# Parte 9.3 dplyr - select

### 1.Haz una lluvia de ideas sobre tantas maneras como sea posible para seleccionar dep_time, dep_delay, arr_time, and arr_delay de flights.

``` r
flights%>%
  select(dep_time,dep_delay,arr_time,arr_delay)
```

    ## # A tibble: 336,776 x 4
    ##    dep_time dep_delay arr_time arr_delay
    ##       <int>     <dbl>    <int>     <dbl>
    ##  1      517         2      830        11
    ##  2      533         4      850        20
    ##  3      542         2      923        33
    ##  4      544        -1     1004       -18
    ##  5      554        -6      812       -25
    ##  6      554        -4      740        12
    ##  7      555        -5      913        19
    ##  8      557        -3      709       -14
    ##  9      557        -3      838        -8
    ## 10      558        -2      753         8
    ## # ... with 336,766 more rows

### 2.¿Qué sucede si incluyes el nombre de una ariable varias veces en una llamada a select()?

``` r
flights%>%
  select(dep_time,dep_time) #La acción solo se toma una vez
```

    ## # A tibble: 336,776 x 1
    ##    dep_time
    ##       <int>
    ##  1      517
    ##  2      533
    ##  3      542
    ##  4      544
    ##  5      554
    ##  6      554
    ##  7      555
    ##  8      557
    ##  9      557
    ## 10      558
    ## # ... with 336,766 more rows

### 3.¿Qué hace la función any_of()? ¡¿Por qué podría ser útil en conjunto con este vector?

``` r
flights%>%select(-any_of("year")) #Se usa para remover variables de un data frame
```

    ## # A tibble: 336,776 x 18
    ##    month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1     1     1      517            515         2      830            819
    ##  2     1     1      533            529         4      850            830
    ##  3     1     1      542            540         2      923            850
    ##  4     1     1      544            545        -1     1004           1022
    ##  5     1     1      554            600        -6      812            837
    ##  6     1     1      554            558        -4      740            728
    ##  7     1     1      555            600        -5      913            854
    ##  8     1     1      557            600        -3      709            723
    ##  9     1     1      557            600        -3      838            846
    ## 10     1     1      558            600        -2      753            745
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
flights%>%select(-any_of("year")) %>%select(-any_of("month")) #Puede ser llamado más de una vez
```

    ## # A tibble: 336,776 x 17
    ##      day dep_time sched_dep_time dep_delay arr_time sched_arr_time arr_delay
    ##    <int>    <int>          <int>     <dbl>    <int>          <int>     <dbl>
    ##  1     1      517            515         2      830            819        11
    ##  2     1      533            529         4      850            830        20
    ##  3     1      542            540         2      923            850        33
    ##  4     1      544            545        -1     1004           1022       -18
    ##  5     1      554            600        -6      812            837       -25
    ##  6     1      554            558        -4      740            728        12
    ##  7     1      555            600        -5      913            854        19
    ##  8     1      557            600        -3      709            723       -14
    ##  9     1      557            600        -3      838            846        -8
    ## 10     1      558            600        -2      753            745         8
    ## # ... with 336,766 more rows, and 10 more variables: carrier <chr>,
    ## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>,
    ## #   distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

# Parte 9.4 dplyr - mutate

### 1.Las variables horario_salida y salida_programada tienen un formato conveniente para leer, pero es difícil realizar cualquier cálculo con ellas porque no son realmente números continuos. Transfórmalas hacia un formato más conveniente como número de minutos desde la medianoche.

``` r
transmute(flights,dep_time,hour=dep_time%/%100,minut=dep_time%%100,nhours=hour*60+minute) #sch_salida
```

    ## # A tibble: 336,776 x 4
    ##    dep_time  hour minut nhours
    ##       <int> <dbl> <dbl>  <dbl>
    ##  1      517     5    17    315
    ##  2      533     5    33    329
    ##  3      542     5    42    340
    ##  4      544     5    44    345
    ##  5      554     5    54    300
    ##  6      554     5    54    358
    ##  7      555     5    55    300
    ##  8      557     5    57    300
    ##  9      557     5    57    300
    ## 10      558     5    58    300
    ## # ... with 336,766 more rows

``` r
transmute(flights,dep_time,hour = sched_dep_time %/% 100,minut = sched_dep_time %% 100,nhour = hour * 60 + minute) #salida_programada
```

    ## # A tibble: 336,776 x 4
    ##    dep_time  hour minut nhour
    ##       <int> <dbl> <dbl> <dbl>
    ##  1      517     5    15   315
    ##  2      533     5    29   329
    ##  3      542     5    40   340
    ##  4      544     5    45   345
    ##  5      554     6     0   360
    ##  6      554     5    58   358
    ##  7      555     6     0   360
    ##  8      557     6     0   360
    ##  9      557     6     0   360
    ## 10      558     6     0   360
    ## # ... with 336,766 more rows

### 2.Compara tiempo_vuelo con horario_llegada - horario_salida. ¿Qué esperas ver? ¿Qué ves? ¿Qué necesitas hacer para arreglarlo?

``` r
 #Espero ver que hora de salida más tiempo de vuelo es igual a horario de llegada
 #No se cumple lo anterior
flights%>%
  select(dep_time,air_time)%>%
  mutate(arr_time=dep_time+air_time)
```

    ## # A tibble: 336,776 x 3
    ##    dep_time air_time arr_time
    ##       <int>    <dbl>    <dbl>
    ##  1      517      227      744
    ##  2      533      227      760
    ##  3      542      160      702
    ##  4      544      183      727
    ##  5      554      116      670
    ##  6      554      150      704
    ##  7      555      158      713
    ##  8      557       53      610
    ##  9      557      140      697
    ## 10      558      138      696
    ## # ... with 336,766 more rows

### 3.Compara horario_salida, salida_programada, y atraso_salida. ¿Cómo esperarías que esos tres números estén relacionados?

``` r
transmute(flights,DEP_delay=(dep_time - sched_dep_time),dep_delay) #horario de salida menos atraso de salida es igual a la salida_programada
```

    ## # A tibble: 336,776 x 2
    ##    DEP_delay dep_delay
    ##        <int>     <dbl>
    ##  1         2         2
    ##  2         4         4
    ##  3         2         2
    ##  4        -1        -1
    ##  5       -46        -6
    ##  6        -4        -4
    ##  7       -45        -5
    ##  8       -43        -3
    ##  9       -43        -3
    ## 10       -42        -2
    ## # ... with 336,766 more rows

### 4.Encuentra los 10 vuelos más retrasados utilizando una función de ordenamiento. ¿Cómo quieres manejar los empates? Lee atentamente la documentación de min_rank().

``` r
Vuelos2<-arrange(flights, desc(dep_delay))
Vuelos2[1:10,]
```

    ## # A tibble: 10 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     6    27      959           1900       899     1236           2226
    ##  9  2013     7    22     2257            759       898      121           1026
    ## 10  2013    12     5      756           1700       896     1058           2020
    ## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
#El comando mink_rank asigna rangos en orden valorando las repeticiones de elementos de un
```

### 5.¿Qué devuelve 1:3 + 1:10? ¿Por qué?

``` r
1:3+1:10         #Devolvera error  ya que no existe la misma cantidad de elementos 
```

    ## Warning in 1:3 + 1:10: longitud de objeto mayor no es múltiplo de la longitud de
    ## uno menor

    ##  [1]  2  4  6  5  7  9  8 10 12 11

### 6.¿Qué funciones trigonométricas proporciona R?

``` r
#seno
sin(1)
```

    ## [1] 0.841471

``` r
#coseno
cos(0)
```

    ## [1] 1

``` r
#tangente
tan(0)
```

    ## [1] 0

``` r
#arcoseno
asin(3/5)
```

    ## [1] 0.6435011

``` r
#arcocoseno 
acos(4/5)
```

    ## [1] 0.6435011

``` r
#arcotangente
atan(1)
```

    ## [1] 0.7853982

## Ejercicios Parte 9.5 - Dplyr - group by & summarize

### 1. Haz una lluvia de ideas de al menos 5 formas diferentes de evaluar las características de un retraso típico de un grupo de vuelos. Considera los siguientes escenarios:

### Un vuelo llega 15 minutos antes 50% del tiempo, y 15 minutos tarde 50% del tiempo

``` r
filter(flights, arr_delay > 15) %>%
group_by(year, month, day) %>%
summarise(min15_tarde = quantile(arr_delay, 0.5, na.rm = TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month'. You can override using the `.groups` argument.

    ## # A tibble: 365 x 4
    ## # Groups:   year, month [12]
    ##     year month   day min15_tarde
    ##    <int> <int> <int>       <dbl>
    ##  1  2013     1     1        33  
    ##  2  2013     1     2        37  
    ##  3  2013     1     3        32  
    ##  4  2013     1     4        36  
    ##  5  2013     1     5        30  
    ##  6  2013     1     6        32  
    ##  7  2013     1     7        41  
    ##  8  2013     1     8        30.5
    ##  9  2013     1     9        28  
    ## 10  2013     1    10        35  
    ## # ... with 355 more rows

``` r
View(filter(flights, arr_delay < 15) %>%
group_by(year, month, day) %>%
summarise(min15_antes = quantile(arr_delay, 0.5, na.rm = TRUE)))
```

    ## `summarise()` has grouped output by 'year', 'month'. You can override using the `.groups` argument.

### Un vuelo llega siempre 10 minutos tarde.

``` r
View(filter(flights, arr_delay == 10) %>%
group_by(year, month, day, flight))
```

### Un vuelo llega 30 minutos antes 50% del tiempo, y 30 minutos tarde 50% del tiempo.

``` r
filter(flights, arr_delay > 30) %>%
group_by(year, month, day) %>%
summarise(min30_tarde = quantile(arr_delay, 0.5, na.rm = TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month'. You can override using the `.groups` argument.

    ## # A tibble: 365 x 4
    ## # Groups:   year, month [12]
    ##     year month   day min30_tarde
    ##    <int> <int> <int>       <dbl>
    ##  1  2013     1     1        54  
    ##  2  2013     1     2        58  
    ##  3  2013     1     3        51  
    ##  4  2013     1     4        49  
    ##  5  2013     1     5        65  
    ##  6  2013     1     6        52  
    ##  7  2013     1     7        59  
    ##  8  2013     1     8        50  
    ##  9  2013     1     9        48.5
    ## 10  2013     1    10        48  
    ## # ... with 355 more rows

``` r
View(filter(flights, arr_delay < 30) %>%
group_by(year, month, day) %>%
summarise(min30_antes = quantile(arr_delay, 0.5, na.rm = TRUE)))
```

    ## `summarise()` has grouped output by 'year', 'month'. You can override using the `.groups` argument.

### Un vuelo llega a tiempo en el 99% de los casos. 1% de las veces llega 2 horas tarde. ¿Qué es más importante: retraso de la llegada o demora de salida?

### 2. Sugiere un nuevo enfoque que te dé el mismo output que no_cancelados %>% count(destino) y no_cancelado %>% count(codigo_cola, wt = distancia) (sin usar count())

``` r
no_cancelation <- filter(flights, !is.na(dep_delay), !is.na(arr_delay))
no_cancelation %>%
count(dest)
```

    ## # A tibble: 104 x 2
    ##    dest      n
    ##    <chr> <int>
    ##  1 ABQ     254
    ##  2 ACK     264
    ##  3 ALB     418
    ##  4 ANC       8
    ##  5 ATL   16837
    ##  6 AUS    2411
    ##  7 AVL     261
    ##  8 BDL     412
    ##  9 BGR     358
    ## 10 BHM     269
    ## # ... with 94 more rows

``` r
no_cancelation %>% 
group_by(dest) %>%
summarise(length(dest))
```

    ## # A tibble: 104 x 2
    ##    dest  `length(dest)`
    ##    <chr>          <int>
    ##  1 ABQ              254
    ##  2 ACK              264
    ##  3 ALB              418
    ##  4 ANC                8
    ##  5 ATL            16837
    ##  6 AUS             2411
    ##  7 AVL              261
    ##  8 BDL              412
    ##  9 BGR              358
    ## 10 BHM              269
    ## # ... with 94 more rows

### 3.Nuestra definición de vuelos cancelados (is.na(atraso_salida) \| is.na (atraso_llegada)) es un poco subóptima. ¿Por qué? ¿Cuál es la columna más importante?

``` r
# La columna mas importante es la primera, a diferencia de la segunda que no influye poque usameos la funcion "is.na(atraso_salida)"
```

### 4.Mira la cantidad de vuelos cancelados por día. ¿Hay un patrón? ¿La proporción de vuelos cancelados está relacionada con el retraso promedio?

### 5. ¿Qué compañía tiene los peores retrasos? Desafío: ¿puedes desenredar el efecto de malos aeropuertos vs. el efecto de malas aerolíneas? ¿Por qué o por qué no? (Sugerencia: piensa en vuelos %>% group_by(aerolinea, destino) %>% summarise(n()))

``` r
arrange(flights, arr_delay) %>%
group_by(arr_delay, carrier, dest) %>%
summarise()
```

    ## `summarise()` has grouped output by 'arr_delay', 'carrier'. You can override using the `.groups` argument.

    ## # A tibble: 39,730 x 3
    ## # Groups:   arr_delay, carrier [4,683]
    ##    arr_delay carrier dest 
    ##        <dbl> <chr>   <chr>
    ##  1       -86 VX      SFO  
    ##  2       -79 VX      SFO  
    ##  3       -75 AA      SEA  
    ##  4       -75 UA      LAX  
    ##  5       -74 AS      SEA  
    ##  6       -73 UA      SFO  
    ##  7       -71 B6      LAX  
    ##  8       -71 DL      PDX  
    ##  9       -71 UA      SFO  
    ## 10       -70 B6      LGB  
    ## # ... with 39,720 more rows

### 6.¿Qué hace el argumento sort a count(). ¿Cuándo podrías usarlo?

``` r
# la funcion count() nos permite saber cuantas observaciones hay en una variable especifica. Al agregar al argumento sort = TRUE devuelve una tabla descendiente con el numero de observaciones
```

## Ejercicios Parte 9.6

### Remítete a las listas de funciones útiles de mutación y filtrado. Describe cómo

### cambia cada operación cuando las combinas con la agrupación.

\*\*\* mutate().Permite crear una columna de datos a partir de un grupo
\*\*\* filter().Filtrar datos por filas de distintos grupos de datos

# ¿Qué avión (codigo_cola) tiene el peor registro de tiempo?

``` r
novolaron<-flights %>% filter(!is.na(dep_delay),!is.na(arr_delay))
novolaron
```

    ## # A tibble: 327,346 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ... with 327,336 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
b<-novolaron %>%count(tailnum,wt=air_time)
tiempos<-arrange(b,n)
tiempos
```

    ## # A tibble: 4,037 x 2
    ##    tailnum     n
    ##    <chr>   <dbl>
    ##  1 N505SW     43
    ##  2 N746SK     50
    ##  3 N824AS     53
    ##  4 N881AS     57
    ##  5 N766SK     60
    ##  6 N701SK     64
    ##  7 N760SK     64
    ##  8 N795SK     66
    ##  9 N726SK     67
    ## 10 N772SK     67
    ## # ... with 4,027 more rows

# ¿A qué hora del día deberías volar si quieres evitar lo más posible los retrasos?

``` r
vuelos<-select(flights,hour, minute, dep_delay, arr_delay)
nocancelados1<-vuelos %>% filter(!is.na(dep_delay),!is.na(arr_delay))
sinretraso<-nocancelados1%>%filter((arr_delay<0) & (dep_delay<0))%>%select(hour,minute,dep_delay,arr_delay)
tiempo1<-arrange(sinretraso,hour,minute)
tiempo1
```

    ## # A tibble: 144,346 x 4
    ##     hour minute dep_delay arr_delay
    ##    <dbl>  <dbl>     <dbl>     <dbl>
    ##  1     5      0        -4       -19
    ##  2     5      0        -2       -10
    ##  3     5      0        -6       -11
    ##  4     5      0        -6       -23
    ##  5     5      0        -3        -1
    ##  6     5      0       -10       -14
    ##  7     5      0        -7        -5
    ##  8     5      0        -7        -8
    ##  9     5      0        -7        -3
    ## 10     5      0        -7       -12
    ## # ... with 144,336 more rows

# Para cada destino, calcula los minutos totales de demora. Para cada vuelo, calcula la

# proporción de la demora total para su destino.

``` r
demora<- group_by(flights, dest)
summarise(demora, mindemora = sum(arr_delay, na.rm = TRUE))
```

    ## # A tibble: 105 x 2
    ##    dest  mindemora
    ##    <chr>     <dbl>
    ##  1 ABQ        1113
    ##  2 ACK        1281
    ##  3 ALB        6018
    ##  4 ANC         -20
    ##  5 ATL      190260
    ##  6 AUS       14514
    ##  7 AVL        2089
    ##  8 BDL        2904
    ##  9 BGR        2874
    ## 10 BHM        4540
    ## # ... with 95 more rows

``` r
proporcion<- group_by(flights, dest)
summarise(proporcion, mindemora = mean(arr_delay, na.rm = TRUE))
```

    ## # A tibble: 105 x 2
    ##    dest  mindemora
    ##    <chr>     <dbl>
    ##  1 ABQ        4.38
    ##  2 ACK        4.85
    ##  3 ALB       14.4 
    ##  4 ANC       -2.5 
    ##  5 ATL       11.3 
    ##  6 AUS        6.02
    ##  7 AVL        8.00
    ##  8 BDL        7.05
    ##  9 BGR        8.03
    ## 10 BHM       16.9 
    ## # ... with 95 more rows

***Los retrasos suelen estar temporalmente correlacionados: incluso una
vez que*** ***el problema que causó el retraso inicial se ha
resuelto,*** ***los vuelos posteriores se retrasan para permitir que
salgan los vuelos anteriores.*** ***lag(), explora cómo el retraso de un
vuelo está relacionado con el retraso del*** ***vuelo inmediatamente
anterior***

### Encuentra todos los destinos que son volados por al menos dos operadores.

### Usa esta información para clasificar a las aerolíneas.

``` r
vuelos1<-flights%>%select(carrier,dest)%>%count(dest,carrier)%>%group_by(dest)%>%filter(rank(desc(carrier))>2)
destinos<-unique(vuelos1$dest)
destinos
```

    ##  [1] "ATL" "AUS" "BNA" "BOS" "BTV" "BUF" "BWI" "CHS" "CLE" "CLT" "CMH" "CVG"
    ## [13] "DCA" "DEN" "DFW" "DTW" "FLL" "IAD" "IND" "JAX" "LAS" "LAX" "MCI" "MCO"
    ## [25] "MEM" "MIA" "MKE" "MSP" "MSY" "OMA" "ORD" "ORF" "PBI" "PDX" "PHL" "PHX"
    ## [37] "PIT" "PWM" "RDU" "ROC" "RSW" "SAN" "SAT" "SDF" "SEA" "SFO" "SJU" "SRQ"
    ## [49] "STL" "STT" "SYR" "TPA"

### Para cada avión, cuenta el número de vuelos antes del primer retraso de más de 1 hora.
