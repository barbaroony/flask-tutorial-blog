# Notes

This project us the official Flask tutorial on 2023/01/13 taken from [https://flask.palletsprojects.com/en/2.2.x/tutorial]. After finishing the tutorial I kept working on the recommended "Keep Development" ideas.

## Updates

### 1.0.2 Future Development

- [x] Like / unlike a post.
- [ ] use images for up/down vote
- [ ] add testing for focus view feature
- [ ] allow users to only use vote once

### 1.0.1

- A detail view to show a single post. Click a post’s title to go to its page
- Created a feature branch
- Figured out how to debug from vs code so I can place breaks into the code

## setting up Virtual Environment

Instructions [https://flask.palletsprojects.com/en/2.2.x/installation/]

- To create a new environment: `python3 -m venv venv`or for windows `python -m venv venv`
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

When deploying the site on remote use `python -c 'import secrets; print(secrets.token_hex())'` and save as `SECRET_KEY = string` inside the created file `venv/var/flaskr-instance/config.py`. Other config info can be stored there as well.

## Blog entries

### Initial deployment on home Alpine server 20230114

Today I was able to deploy an alpine server with python waitress, that was kind of fun! I installed proxmox on my old Lenovo U330 and found out that the old laptop does not have virtualization. I then installed Alpine linux and was able to ssh into it. When moving code over to the server, I moved the entire repository instead of moving the wheel object, and because of that, I was not able to correctly create a SECRET_KEY.

Running the app using waitress made the project terminate when I closer the ssh terminal, unless i ran the process in the background with `waitress-serve --call 'flaskr:create_app'&`. Thank you Stan, for showing me how to run precesses in the background.

I look forward to keep working on this project.
