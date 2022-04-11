Locations
============================

This folder contains a comma-separated file `locations.csv` that contains the five digit FIPS code, 
location name used for forecast submission and the location FIPS code, the state name, county name, and population (2010 US Census) for each valid forecast location.

Values in the `fips` column are five digit FIPS code, which includes the two-digit state code and the three-digit 
county code. Please note that when writing FIPS codes, they are written as a character string to preserve any 
leading zeroes.

Values in the `location` column consist of the “State” and “County” as written with a hyphen: “State-County”. For example, 
“California-San Diego” or “Texas-Harris”.
