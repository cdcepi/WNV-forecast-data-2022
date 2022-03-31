Forecast submission instructions
============================

This page is intended to provide teams with all the information they
need to submit forecasts. We note that these instructions have been adapted from the [COVID-19 Forecast Hub](https://github.com/reichlab/covid19-forecast-hub).

All forecasts should be [submitted directly](#Making-a-submission) to
the [data-forecasts/](./) folder. Data in this directory should be added
to the repository through a pull request so that automatic data validation checks are run.

These instructions provide detail about the [data
format](#Data-formatting) as well as [validation](#Forecast-validation) that
you can do prior to this pull request. In addition, we describe
[metadata](https://github.com/cdcepi/WNV-forecast-data-2022/blob/master/data-forecasts/METADATA.md) that each model should provide.

See the [data-surveillance/](https://github.com/cdcepi/WNV-forecast-data-2022/tree/main/data-surveillance) folder for 
details on the reported WNV neuroinvasive case data. 

*Table of Contents*

-   [Data formatting for submission](#Data-formatting)
-   [Forecast file format](#Forecast-file-format)
-   [Making a submission](#Making-a-submission)
-   [Forecast data validation](#Forecast-validation)
-   [Policy on late submissions](#policy-on-late-or-updated-submissions)


Data formatting
---------------

The automatic checks in place for forecast files submitted to this repository validates both the filename and 
file contents to ensure the file can be used in the visualization and ensemble forecasting.

### Subdirectory

Each subdirectory within the [data-forecasts/](data-forecasts/)
directory has the format

    team-model

where

-   `team` is the teamname and
-   `model` is the name of your model.

Both team and model should be less than 15 characters and not include
hyphens. The `model` should be unique from any other model in the project.

Within each subdirectory, there should be a metadata file, a license
file (optional), and a set of forecasts.

### Metadata

The metadata file should have the following format

    metadata-team-model.txt

and here is [the structure of the metadata
file](https://github.com/cdcepi/WNV-forecast-data-2022/blob/master/data-forecasts/METADATA.md).

### License (optional)

By default, forecasts are released under a CC-BY 4.0 license. If you would like to release your forecasts under a different license, please specify a [standard
license](../accepted-licenses.csv) in the `license` field of your metadata file. Alternatively, if you wish to use a license that is not in the list of [standard
licenses](../accepted-licenses.csv), you may include a 

    LICENSE.txt

file in your model directory. 

### Forecasts

Each forecast file within the subdirectory should have the following
format

    YYYY-MM-DD-team-model.csv

where

-   `YYYY` is the 4 digit year,
-   `MM` is the 2 digit month,
-   `DD` is the 2 digit day,
-   `team` is the teamname, and
-   `model` is the name of your model.

The date YYYY-MM-DD is the [`forecast_date`](#forecast_date). For this project, the `forecast_date` should always 
be the date which the submission is due.

The `team` and `model` in this file must match the `team` and `model` in
the directory this file is in. Both `team` and `model` should be less
than 15 characters, alpha-numeric and underscores only, with no spaces
or hyphens.

Forecast file format
--------------------

The file must be a comma-separated value (csv) file with the following
columns (in any order):

-   `forecast_date`
-   `target`
-   `location`
-   `quantile`
-   `value`

No additional columns are allowed.

Each row in the file is either a point or quantile forecast for a location on a particular date for a particular 
target. See the [template](./wnv_forecasting_template.csv) for an example.


### `forecast_date`

Values in the `forecast_date` column must be a date in the format

    YYYY-MM-DD

This is the date on which the forecasts were due to be submitted.  `forecast_date` should correspond
and be redundant with the date in the filename, and is included here by
request from some analysts. 

### `target`

Values in the `target` column must be the following character (string):

-   “Annual WNV neuroinvasive disease cases"

The total number of West Nile virus (WNV) neuroinvasive disease cases (confirmed and probable following the 
[WNV neuroinvasive disease case definition](https://ndc.services.cdc.gov/case-definitions/arboviral-diseases-neuroinvasive-and-non-neuroinvasive-2015/)) 
reported to [ArboNET](https://wwwn.cdc.gov/arbonet/Maps/ADB_Diseases_Map/index.html) from each county in the 
contiguous United States in 2022.

### `location`

Values in the `location` column consist of the “State” and “County” as written with a hyphen: “State-County”. For example, 
“California-San Diego” or “Texas-Harris”. Do not include the word “County” and include spaces between words 
within the county or state name. The easiest way is to accomplish this is by matching the format in the [location file](../data-locations/locations.csv).

### `quantile`

Values in the `quantile` column are in the format

    0.###

This value indicates the quantile for the `value` in this row.

Teams must provide the following 23 quantiles:

    c(0.01, 0.025, seq(0.05, 0.95, by = 0.05), 0.975, 0.99)

    ##  [1] 0.010 0.025 0.050 0.100 0.150 0.200 0.250 0.300 0.350 0.400 0.450 0.500
    ## [13] 0.550 0.600 0.650 0.700 0.750 0.800 0.850 0.900 0.950 0.975 0.990


### `value`

Values in the `value` column are non-negative numbers indicating the
“quantile” prediction for this row. This is the inverse of the cumulative distribution function for
the `target`, `location`, and `quantile` associated with that row.


Making a submission
---------------

### Initial submission

To prepare for the initial submission, make a [subdirectory](#Data-formatting) for your team in 
the [data-forecasts/](./) folder. This is where you will place all your forecasts, metadata, and license (optional).

Files should be added to the repository through a [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) 
so that automatic data validation checks are run. More information on making a pull request can be found 
[here](https://www.freecodecamp.org/news/how-to-make-your-first-pull-request-on-github-3/).

The initial submission should include the forecast for April 30, metadata describing the model, and optional license file.


### Additional submissions

Forecast submissions for the optional May, June, and July deadlines as well as updated metadata are made through 
pull requests as well. All the files for each team should be placed in their subdirectory.



Forecast validation
-------------------

To ensure proper data formatting, pull requests for new data in
`data-forecasts/` will be automatically run.

### Pull request forecast validation

When a pull request is submitted, the data are validated through [Github Actions](https://docs.github.com/en/actions) 
which runs the tests present in [the validations repository](https://github.com/cdcepi/Flusight-forecast-validation). The intent
for these tests are to validate the requirements above. 
Please [let us know](https://github.com/cdcepi/WNV-forecast-data-2022/issues) if you are facing issues while running the tests.


Policy on late or updated submissions
------------------

In order to ensure that forecasting is done in real-time, all forecasts are required to be submitted to this 
repository by the listed (deadlines)[../README.md]. We do not accept late forecasts. 
