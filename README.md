![](https://i.imgur.com/GtUi6nH.png)

## 1. Introduction

### The dataset and target value
    
The data is retrieved from the **_[AEMET](https://opendata.aemet.es/centrodedescargas/inicio)_** site, **_AEMET_** (Agencia Estatal de Metereología) is the Spanish official weather agency, which offers some of the data they gather for public use [(OpenData)](https://opendata.aemet.es/centrodedescargas/inicio). 

In this case, we will try to forecast the **minimum** and **maximum** temperatures for a weather station in Madrid, Spain. 

### Problem description

As we all know, [climate change](https://www.un.org/en/sections/issues-depth/climate-change/) is a huge problem we all have been suffering from since the last decade. The temperature are constantly rising, which creates abnormals changes that affect the ecosystem. Consequently, these changes impact the stations; longer and warmer periods and shorter but inconsistent cold periods. 

To name a few of the consequences of this change, we can see how some species are on the verge of extinction, others, are forced to migrate elsewhere, breaking the balance of the local fauna. Plants experience a change in their life cycle, causing crops to fail, or in the worst case, to be completely lost due to an extremely cold late winter, or an extraordinarily hot early summer. Not to mention the increase in weather phenomena that we've experienced over the last century.  

Being the Madrid the city where I currently live since 2009, I can tell the summers are warmer than previous, but mainly, the winters aren't colder as they used to be. The objective is to **forecast** the max/min temperatures from the MADRID AEROPUERTO station, to see if the rising trend will hold for the coming years.

## 2. Data load, formatting and inspection.

We access the *AEMET* data via API, filtering the request to get the *daily temperature records* of the period 1990 - 2019 from the *MADRID AEROPUERTO* station. The information is retrieved in JSON format, which was loaded into a Pandas dataframe and filtered to have finally the fields we're interested in:

+ **_fecha_**: Date of the measure, index of the dataframe.
+ **_tmin_**: Minimum temperature registered that day.
+ **_tmax_**: Maximum temperature registered that day.

As is pointless work to forecast the daily temperature, the dataframe was resampled to monthly periodicity using *average* as aggregation method. Then, the data was split into 2 series (minimum and maximum) to be able to work separately. No NaN or empty values were found in the integrity checks.

## 3. Descriptive statistics

### General overview

The datasets statistics tell us, the STD of the maximum temperatures is higher than the minimum one, which indicates the temperature fluctuations are greater. 

When we see the higher and lower record of daily, monthly and yearly temperatures we note the following:

* Coldest temperatures happened all before 2001.
* Warmest month and year both happened in 2015, except the hottest day ever recorded, which happened in July 1995.
* The warmest minimum temperatures all happened in the 2010 decade.
* The coldest maximum temperatures for month and year happened before 2001,  except the coldest maximum temperature ever recorded, which happened in January 2010.

### Data visualization

The plots of the series, we see a *seasonal time series* in both graphs, with no clear trend, neither the actual data or the rolling mean, calculated on a window of 12 months.

But when we calculate the year rolling mean for the minimum and maximum data, with a window of 5 years, we see that both higher temperatures and the lowest maximum average temperature have a clear rising trend, which confirms the fact that temperatures are rising.

## 4. Exporatory data analysis

### Augmented Dickey-Fuller test

To begin with, we must verify if the time series are stationary, once we apply the Augmented Dickey-Fuller test in both, we can affirm with **_99% confidence_** that they are, as both scored a less than 0.01 p-value. The results of the test can be seen in the notebook.

