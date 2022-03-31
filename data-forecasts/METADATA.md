# Metadata file structure

Each model is required to have metadata in 
[yaml format](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html), 
e.g. [see this metadata file](https://github.com/reichlab/covid19-forecast-hub/blob/master/data-processed/JHU_IDD-CovidSP/metadata-JHU_IDD-CovidSP.txt).
Note that the example file has a slightly different structure and included variables.

This file describes each of the variables (keys) that should be included in the submitted yaml document.
Please order the variables in this order.


## Required variables

### team_name
The name of your team that is less than 50 characters.

### model_name
The name of your model that is less than 50 characters.

### model_abbr
An abbreviated name for your model that is less than 30 alphanumeric characters. The model abbreviation must be in 
the format of `[team_abbr]-[model_abbr]`. where each of the `[team_abbr]` and `[model_abbr]` are text strings that 
are each less than 15 alphanumeric characters that do not include a hyphen or whitespace  Note that this is a 
uniquely identifying field in our system, so please choose this name carefully, as it may not be changed once 
defined. An example of a valid `model_abbr` is `UMass-MechBayes` or `UCLA-SuEIR`. 

### team_lead
The name, affiliation, and email address for the individual acting as the team lead. The email needs to be valid
for communication with the team.

The syntax of this field should be

    name (affiliation) <user@address>

### model_contributors
A list of all other individuals involved in the forecasting effort, affiliations, and email address.
All email addresses provided will be added to an email distribution list for model contributors.

The syntax of this field should be 

    name1 (affiliation1) <user@address>, name2 (affiliation2) <user2@address2>

### license

One of [licenses](https://github.com/reichlab/covid19-forecast-hub/blob/master/code/validation/accepted-licenses.csv).

We encourage teams to submit as a "cc-by-4.0" to allow the broadest possible uses. 
If the value is "LICENSE.txt", then a LICENSE.txt file must exist within the folder and provide a license.

### methods

A brief description of your forecasting methodology that is less than 200 characters.

### data_inputs

A description of the data sources used in the model and the temporal relationship of these variables to the forecast.

An example description of a set of variables could be 

> Spring (Jan-Mar, matching time to forecast) mean temperature and total precipitation were obtained on the
> county scale from PRISM.



## Optional

### institutional_affil

University or company names, if relevant. 

### team_funding 

Like an acknowledgement in a manuscript, you can acknowledge funding here.

### repo_url

(previously `model_repo`)

A github (or similar) repository url. 

### citation

A url (doi link preferred) to an extended description of your model,
e.g. blog post, website, preprint, or peer-reviewed manuscript. 

### methods_long

An extended description of the methods used in the model. 
If the model is modified, this field can be used to provide the date of the 
modification and a description of the change.
