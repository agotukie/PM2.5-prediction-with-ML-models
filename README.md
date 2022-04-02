# PM25 prediction in Warsaw

Model created for fun to test possibility of creating machine learning model based on available data for Warsaw.  


## Weather data 2015-2019
Data retrieved from API https://darksky.net/dev/docs#time-machine-request  

## Pollution data for PM2.5 2015-2019
Data from archive http://powietrze.gios.gov.pl/pjp/archives  

## Available data
Data in initial model:  
* PM2.5 data from 3 stations ('pm25_nie', 'pm25_kon', 'pm25_wok'), 
* set of meteorological data ('winter_break', 'apparentTemperature', 'cloudCover', 'dewPoint', 'humidity', 'precipAccumulation', 'precipIntensity', 'precipProbability', 'precipType', 'pressure', 'temperature', 'uvIndex', 'visibility', 'windBearing', 'windGust', 'windSpeed')
* set of sezonal data ('date', 'year', 'month', 'day','hour', 'day_of_week', 'no_of_week')

Correlation matrix  
![obraz](https://user-images.githubusercontent.com/10920417/161385575-851430b9-5f8c-48b3-bae8-4107611a1e5f.png)


Some variables are highly correlated  
VIF - variance inflation factor  

|variable               |VIF       |
|-----------------------|----------|
|temperature            |219.106036|
|apparentTemperature    |125.666083|
|dewPoint               | 87.160973|
|humidity               | 32.393281|
|month                  | 22.729463|
|no_of_week             | 22.499852|
|pm25_wok               |  8.274731|
|pm25_nie               |  7.938301|
|windGust               |  5.335601|
|windSpeed              |  5.257859|
|visibility             |  2.776910|
|year                   |  2.394984|
|precipProbability      |  2.184273|
|precipIntensity        |  1.993141|
|uvIndex                |  1.613159|
|pm25_kon               |  1.602117|
|cloudCover             |  1.306285|
|pressure               |  1.269099|
|hour                   |  1.155689|
|winter_break           |  1.142295|
|day                    |  1.100532|
|windBearing            |  1.094673|
|precipAccumulation     |  1.059246|
|day_of_week            |  1.005792|


## Initial model results
Model was run on pm25_wok data - comparison of XGBoost and LightGBM  

XGBoost Regression model   
RMSE: 0.3856  
R2: 69.0%  

LightGBM   
RMSE: 0.3267  
R2: 77.7%  


## Optimalization with Hyperopt
Optimalization of XGBoost model  
 
pm25_nie data  
RMSE: 0.2820  
R2: 79.9%  

pm25_wok data  
RMSE: 0.2887  
R2: 82.6%  




