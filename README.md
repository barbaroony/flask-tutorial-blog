# Notes

This project us the official Flask tutorial on 2023/01/13 taken from [[https://flask.palletsprojects.com/en/2.2.x/tutorial]

## setting up Virtual Environment

Instructions [https://flask.palletsprojects.com/en/2.2.x/installation/]

- To create a new environment: `python2 -m venv venv`or for windows `python -m venv venv`
- To activate the environment: `. venv/bin/activate` or for windows `venv\Scripts\activate`
- In order to create a requirements.txt file `pip freeze > requirements.txt`

## Running application

- Starting in debug mode: `flask --app flaskr --debug run`

## Testing the application

use `pytest`

## Deploying the application

to make a distribution file use `$ python setup.py bdist_wheel` which will create the file in.
When deploying the applicaiton on the new machine use `pip install DIST_APP_NAME`. After the installation
to initialize the db, use `flask --app flaskr init-db`
