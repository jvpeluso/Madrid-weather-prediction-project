![](https://i.imgur.com/GtUi6nH.png)

## 1. Introduction

### The dataset and target value
    
The data is retrieved from the **_[AEMET](https://opendata.aemet.es/centrodedescargas/inicio)_** site, **_AEMET_** (Agencia Estatal de Metereología) is the Spanish official weather agency, which offers some of the data they gather for public use [(OpenData)](https://opendata.aemet.es/centrodedescargas/inicio). 

In this case, we access the data via their API, filtering the request to get the *daily temperature records* of the period 1990 - 2019 from the *MADRID AEROPUERTO* station. The information is retrieved in JSON format, which was loaded into a Pandas dataframe and filtered to have finally the fields we're interested in, **minimum** and **maximum** temperature, with the **dates** as *index*.

### Problem description

As we all know, [climate change](https://www.un.org/en/sections/issues-depth/climate-change/) is a huge problem we all have been suffering since the last decade. The temperature are constantly raising, which creates abnormals changes that affect the ecosystem. Consequently, these changes impact the stations; longer and warmer periods and shorter but inconsistent cold periods. 

To name a few of the consequences of this change, we can see how some species are on the verge of extinction, others, are forced to migrate elsewhere, breaking the balance of the local fauna. Plants experience a change in their life cycle, causing crops to fail, or in the worst case, to be completely lost due to an extremely cold late winter, or an extraordinarily hot early summer. Not to mention the increase in weather phenomena that we've experienced over the last century.  
