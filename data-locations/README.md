Locations
============================

This folder contains a comma-separated file `locations.csv` that contains location-specific data for all US counties included in the forecasting challenge.

Columns:

- `fips` is the five digit FIPS code, which includes the two-digit state code and the three-digit 
county code. Please note that when writing FIPS codes, they are written as a character string to preserve any 
leading zeroes.
- `county` is the county name.
- `state` is the state name.
- `location` is `state-county` as a character string and is the variable that should be included in forecast submissions. 
For example, “California-San Diego” or “Texas-Harris”. Forecast submissions will be 
checked to ensure that location names match those found in this csv file.
- `population` is the county population size from the 2010 US Census.

