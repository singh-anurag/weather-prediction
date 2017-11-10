# weather-prediction

## Requirement Statement:

The application is designed to predict the weather of various cities around Australia. 
Primarily the weather is observed over a period of time and later , using time series analysis, weather conditions are 
like temperature, humidity etc. are predicted. Time-series analysis is the core part of the project. This analysis is achieved using Auto-regressive integrated moving average (ARIMA), a statistical technique, to forecast weather parameters.

Data required for the prediction is sourced from BOM (Bureau of Meteorology, Australia).

Scope of the application can be altered/widened by changing the source of input data.

# Development

## Design and Build
The application is designed using following 
1. Scala
2. SBT (Scala Build Tool)
3. Java

Project uses SBT for building and converting the code into a jar

## Execution
Command line parms must be specifed in pairs in the format --name value. 
Internally application validates this format & converts to a Map(name -> vlaue)

Application expects, 4 mandatory command line parms viz. dataSource, year, month, outFile. Optional parameter dateRange allows to override the default date range of (201610 to 201711). This range can be adjusted according to the data availablity in Bureau of 
Meteorlogy.

As of now dataSource is Bureau of Meteorlogy, the data is downloaded from BOM website before forecasting else it expects the data to be in local files in current working dierctory.

## Dependencies

There are certain dependencies in the code with the help of which expected output os acheived.
All dependencies are listed below in an orderly manner 

1. sparkts (For ARIMA timeseries analysis.)
2. spark-code & spark-mllib (For prediction and forecast)
3. joda-time (Date - time utility)
4. json4s (Extracting Geo-cordinates from Google Rest API response json)
