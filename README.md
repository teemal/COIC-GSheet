# Readme

## What
This codebase is a Heroku hosted Flask app that pulls census, given a correct POST passing in a census American Community Survey (acs) 5 year study, and updates a Google Sheets worksheet. On update  of this worksheet,a seperate Tableau dashboard is updated shoowing vizualitions of the current Sheets  values. 

## Who
Taylor Malory: taymal1987@gmail.com    
Matthew Barnes: mlbarnes04@gmail.com

## Getting Started
* Make sure you have python 3 (Heroku is currently running 3.8), Anaconda (>= 4.6) and Git.
* Clone and `cd` into the repo
* Create a new virtual enviroment with `conda create --name myenv && conda activate myenv`, substituting `myenv` with whatever enviroment name you choose.
* Install dependencies with `conda install --file requirements.txt`
* For local development - **You will need a client_secret.json**. This is found through [here](https://console.developers.google.com/), under the account associated with this project. Click on the project (located in the upper left near the Google APIs logo), click `Crednetials`, click `OAuth 2.0 Client IDs`,  download the JSON file and change the file name to just `client_secret.json`. Place JSON file in the root of the directory.
* For local development - In the directory you will find a  `.env.example` file. Run `mv .env.example .env`, then open `.env` in your prefered editor. The keys present in this file are correct but their values are not. Go to Heroku, select either the staging or production project, go find the enviroment variables and replace the values in the `.env` file with the associated values found on Heroku.
* For local development - In you console, run `FLASK_ENV=dev`.

* You are now ready to edit the files and push to Heroku/development, so long as you have access to the project.

## Example request
* An example POST looks like `https://coic-housing.herokuapp.com/update_gsheet?pword=XXXXX&year=2018`. Substituting `XXXXX` for the correct password. The year should be within 2013 - the year of the most current American Community Survey (ACS).


## Tips
* Ensure you have proper Heroku enviroment variables configured. These are denoted in the code with `os.environ['SOME_ENV_VAR']`, except for the pygsheets authorization which just needs the key name. 
* The enviroment variables should be good to go and not need changing or updating. If they do, for some reason, those can be updated in Heroku either through the CLI or site. The 'SERVICE_ACCOUNT' enviroment variable is a JSON file, generated through the projects Google Developers page (https://console.developers.google.com/), and thrown directly into Heroku as an eviroment variable. If, for some reason, the project needs a new one, generate it through the above link, add the **entire** file as an enviroment variable, and then share access to the email address within the JSON file from the projects sheets page.
* To view available conda virtual enviroments, run `conda  env list`
* To leave the current conda virtual enviroment, run `conda deactivate`

### Links: 
* Python: https://www.python.org/downloads/
* Pandas: https://pandas.pydata.org/
* pygsheets: https://pypi.org/project/gsheets/
* requests: https://requests.readthedocs.io/en/master/
