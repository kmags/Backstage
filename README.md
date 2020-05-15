# Backstage Tech Challenge

## Background
* The Director of Finance has requested “a report on correlations between the weather and our sales”. We can assume the hypothesis is that weather has an effect on sales. He
* did not provide many details, but let’s assume he does not currently have easy access to this data and therefore needs an analysis of the current state, as well as access to * this data as a report going forward.  Our final output will be 1) a summary of key findings after exploratory analysis of the data and 2) a link to a report with             * instructions on how to access, refresh, etc. 

### PROPOSED PLAN 

## Objective
* 1) Examine the correlation between weather and uw basket weaving sales
* 2) Provide report for finance to access and explore this data going forward

## Areas for exploratory analysis / cuts of data to be included in a report: 
* 1) Location → Variation of weather impact by continent/country/state, etc
* 2) Seasonality →  Does correlation of weather to sales change with the seasons?
    	- Mapping required to assign ‘seasons’ to countries 
    	- Month over month view will show if Christmas/holiday season sales has weather correlation
* 3) Additional sales metrics → Weather’s impact on: 
    	- Avg order value, Avg daily orders, Avg daily $ per customer, Avg daily units per customer
* 4) Customer Segmentation → Variation of weather impact on different types of customers:
	 	- New vs. repeat buyers, High/medium/low lifetime value segments, Customer cohort analysis 


###DATA PROCESS

##Create data sources: 
* 1) Chinook Data
* 2) Weather Data 


## Chinook Data
* For efficiency purposes, I downloaded a sample Chinook data source from GitHub (https://github.com/lerocha/chinook-database/tree/master/ChinookDatabase/DataSources) 
* Then, I'm imported the dataset to a local relational data store (SQLLiteStudio) via the tool's GUI (again, for efficiency's sake).
** I'm on a Mac, so I chose to use SQLLiteStudio v3.2.1 as my SQL environment and data store. 
** For enterprise data software, I've familiar with Tableau, SnowFlake, Looker, MS Sql, MySQL, Postgres, etc. They all have their pro's and con's, but version-control and re-usablility are characteristics of each that are important.
* As a second version, I'd like to automate the process of both exporting and importing data.
** In lieu of more formalized parterships with the data sources, I'd probably write a script to do both the exporting/importing, probably using python (given its ubiquity).

## Weather Data
* Again for efficient purposes, I downloaded a Weather data source from www.ncdc.noaa.gov.
* I then imported the Weather Data in a similar fashion as I did for the Chinook data source.
* For this sample, data only includes USA data 

## Joining The Data
* To examine how weather impacts sales data, we had to clean up the data to be able to join on location & datetime. 
* Location
** Our weather data has highly detailed location info (lat, long) based on weather stations in all 50 states. Our sales data has customer address information. 
** The long term solution would be to use a python script to generate a latitude & * longitude for a given address. One option is to use python packages geopandas and geopy to generate latitude and longitude combination and calculate distance between two points this way. 
** A simpler but less accurate approach would be to use pgeocode to calculate the distance between postal codes
* Datetime
** The weather data is recorded at the day, hour level. The invoice date in the sales table is recorded at the day level, without timestamp granularity. 
** Therefore, our only option is to compare sales to 
** Therefore, for this data
