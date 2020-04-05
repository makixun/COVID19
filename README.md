# COVID19

[cran]: https://www.r-pkg.org/badges/version/zeallot"
![alt text][cran]


## Scripts for describing, analysing and predicting the pandemic COVID19

### Description of files

The code available is composed of **three code files and one dataset**:

- **aux_functions.R**: code with auxiliary functions which should not change it. 

- **countries_by_continents.R**: code for classify each country in its continent. Note that Russia has been included in Europe and Turkey in Asia. The dataset with the classifiction is contained in countries_by_continents.R

- **main_comparing_countries_ECDCdata.R**: code for extracting, filtering and plotting the data. **IMPORTANT**: this code is the only piece of code that the non-expertised user should execute and open.


### Installation (please, check before question to be asked below):

#### Option 1: R studio (recommended):

**Download all files** of [repository](https://github.com/JavierAlvarezLiebana/COVID19/tree/master) in the same folder of your computer and **just open the** [main file](https://github.com/JavierAlvarezLiebana/COVID19/blob/master/main_comparing_countries_ECDCdata)

![Head of code. Source on save must be ticked](https://github.com/JavierAlvarezLiebana/COVID19/blob/master/head_code_source_on_save.jpg)

Note that at the beginning of the [main file](https://github.com/JavierAlvarezLiebana/COVID19/blob/master/main_comparing_countries_ECDCdata.R), all **variables will be removed** and all packages required will be attached. You can execute the whole code just pressing the **save button** in the R studio, making sure that the **option source on save is previously ticked**.

#### Option 2: classical R terminal:

You can also execute in the classical terminal of R by writting (note that `your_path_of_files` should b the path of your computer where you have saved the files)
 
```R
source('your_path_of_files/main_comparing_countries_ECDCdata.R')
```


### Questions to be asked before executing:

Please, **before executing, read the questions asked** at the beginning of the [main file](https://github.com/JavierAlvarezLiebana/COVID19/blob/master/main_comparing_countries_ECDCdata.R): 

- **countries**: introduce the **code of the countries** that you want to plot (maximum 11 at the same time). Check the available codes in [countries by continents dataset](https://github.com/JavierAlvarezLiebana/COVID19/blob/master/countries_by_cont.RData)

```R
countries <- c("ESP", "ITA", "FRA", "DEU", "PRT", "GBR", "USA",
               "CAN", "MEX", "CHN", "NLD")
```

- **log**: do you want data in the **original scale** `FALSE` or in the **log scale** `TRUE`?

```R
log <- FALSE # If log <- TRUE, cases and deaths are plotted in log_10 scale
```

- **from_date**: since **when** do you want to analysed? For example, since `from_date <- "2019-12-31" `

```R
from_date <- "2019-12-31" # Please, modify with a date in format "YYYY-mm-dd"
to_date <- format(Sys.time(), "%Y-%m-%d") # DO NOT CHANGE
dates <- as.Date(c(from_date, to_date)) # DO NOT CHANGE
```

- **save_local**: do you want to **save in your computer** the datasets `TRUE`or not `FALSE`?

```R
save_local <- TRUE
```

- **n_hab** do you want to show all data in a **relative way, in terms of each** `n_hab` **people**? For example, `n_hab <- 10000` would be for each **10.000 people**. Otherwise, please fix `n_hab <- FALSE`.

```R
n_hab <- 1e6 # If n_hab <- FALSE, deaths or cases are plotted as usual
```

- **aligned_cases**:  do you want to **align the data** `TRUE`, starting all graphics at **Day 0 of pandemic** defining as the first day in which **cumulative cases are greater than population * perc_pop**, where `perc_pop` denotes a percentage of the population, or not `FALSE`?

```R
aligned_cases <- TRUE
perc_pop <- 0.000005 # 0.0005 % of population of each country
```

- **aligned_deaths**:  do you want to **align the data** `TRUE`, starting all graphics at **Day 0 of pandemic** defining as the first day in which **cumulative deaths are greater than population * perc_pop**, where `perc_pop` denotes a percentage of the population, or not `FALSE`?

```R
aligned_deaths <- FALSE
perc_pop <- 0.000001 # 0.0001 % of population of each country
```

#### Flags for plotting:

Which graphics do you want to be plotted?

- **plot_cases**: do you want a graphic plotting the **daily cases** `TRUE` or not `FALSE`?
- **plot_deaths**: do you want a graphic plotting the **daily deaths** `TRUE` or not `FALSE`?
- **plot_cum_cases**: do you want a graphic plotting the **cum cases** `TRUE` or not `FALSE`?
- **plot_cum_deaths**: do you want a graphic plotting the **cum deaths** `TRUE` or not `FALSE`?
- **plot_morth_rate**: do you want a graphic plotting the **daily mortality rate** (cum deaths / cum cases) `TRUE` or not `FALSE`?
- **plot_v_cases**: do you want a graphic plotting the **% growth (velocity) of cases** `TRUE` or not `FALSE`?
- **plot_v_deaths**: do you want a graphic plotting the **% growth (velocity) of deaths** `TRUE` or not `FALSE`?
- **plot_a_cases**: do you want a graphic plotting the **% growth of velocity (acceleration) of cases** `TRUE` or not `FALSE`?
- **plot_a_deaths**: do you want a graphic plotting the **% growth of velocity (acceleration) of deaths** `TRUE` or not `FALSE`?
- **plot_dev_by_continents**: do you want a graphic plotting the **cases and deaths (and their cumulatives) in comparison with their continets** (by habitants) `TRUE` or not `FALSE`?

```R
# PLOT_CASES, PLOT_DEATHS, PLOT_CUM_CASES, PLOT_CUM_DEATHS, PLOT_MORT_RATE
plot_cases <- TRUE # A graphic about the daily cases? TRUE/FALSE
plot_deaths <- TRUE # A graphic about the daily deaths? TRUE/FALSE
plot_cum_cases <- TRUE # A graphic about the cum. cases? TRUE/FALSE
plot_cum_deaths <- TRUE # A graphic about the cum. deaths? TRUE/FALSE
plot_mort_rate <- TRUE # A graphic about the mortality rate (cum deaths / cum cases)? TRUE/FALSE

# PLOT_V_CASES, PLOT_V_DEATHS, PLOT_A_CASES, PLOT_A_DEATHS
plot_v_cases <- TRUE # A graphic about the % growth (velocity) of cases? TRUE/FALSE
plot_v_deaths <- TRUE # A graphic about the % growth (velocity) of deaths? TRUE/FALSE
plot_a_cases <- TRUE # A graphic about the % growth of velocity of cases (acceleration)? TRUE/FALSE
plot_a_deaths <- TRUE # A graphic about the % growth of velocity of deaths (acceleration)? TRUE/FALSE
plot_dev_by_continents <- TRUE # A graphic about the data related to their continents
```

### Examples of using the datasets (after executing the code):


### Examples of using the graphics (after executing the code):

If you write in the console

- ECDC_data$raw_data: raw data (all countries, all dates).

- ECDC_ESP$covid_data: covid19 data of Spain, from the ECDC database, between the selected dates, updated just in time of the execution.

- ECDC_data$all_countries: all countries (their codes) included in the database.

- ECDC_data$filter_countries: asked country codes

- ECDC_data$filter_data[[i]]: filtered data (by countris and dates) of the i-th country asked (included in ECDC_data$filter_countries).

- ECDC_ESP$country and ECDC_ITA$country # Country codes (in this case "ESP" and "ITA", resp.)

- ECDC_ESP$population: population in January 2019 from the World Bank database

- graphics_countries$fig_cum_deaths: plots cumulative deaths

- graphics_countries$fig_vel_cases: plots the % daily growth of cases 

- graphics_countries$ + tab key: a menu will appear with the different graphics available.




