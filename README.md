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

### 20230114 Initial deployment on home Alpine server 

Today I was able to deploy the page on Alpine Linux server with python waitress, that was kind of fun! At first, I installed proxmox on my old Lenovo U330 and found out that the old laptop does not have virtualization. I then installed Alpine linux and was able to ssh into it. I set a static ip on the system to 192.167.87.11, in order to ssh to the machine use `ssh dmitriy@192.168.87.11`. I have also set up a DNS for the above address to **alpine.local**. When moving code over to the server, I moved the entire repository instead of moving the wheel object, and because of that, I was not able to correctly create a SECRET_KEY.

Running the app using waitress made the project terminate when I closer the ssh terminal, unless i ran the process in the background with `waitress-serve --call 'flaskr:create_app'&`. Thank you Stan, for showing me how to run precesses in the background. By default the waitress will run the application on port 8080 so that in order to access the site, use `alpine.local:8080` on any computer on the network.

I look forward to keep working on this project.

### 20230118 Playing with my new toys

I took a few days to work sqlite and am still working on it. I need to learn sql queries because I wanted to limit users to only a single up/down vote per post and my understanding of sqlite was limiting my work. I look forward to using my understanding of sqlite in other projects. I believe that the query language is the same with other databases.

While wasting time, I also installed a docker and docker-composer on the Alpine machine. I look forward to playing with docker as well. I did not like running docker on my main machine when I was originaly learning docker a few years ago.

For *funsies* I have also installed a wordpress docker. The container can be reached at `alpine.local` or the static ip from above. I used this [tutorial](https://cloudinfrastructureservices.co.uk/install-wordpress-with-docker-compose/).

TODO: think about running my own gitlab server, possibly on the NAS.
