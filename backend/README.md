# Coffee Shop Backend

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Environment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organized. Instructions for setting up a virtual environment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) and [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) are libraries to handle the lightweight sqlite database. Since we want you to focus on auth, we handle the heavy lift for you in `./src/database/models.py`. We recommend skimming this code first so you know how to interface with the Drink model.

- [jose](https://python-jose.readthedocs.io/en/latest/) JavaScript Object Signing and Encryption for JWTs. Useful for encoding, decoding, and verifying JWTS.

## Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

Each time you open a new terminal session, run:

```bash
export FLASK_APP=api.py;
```

To run the server, execute:

```bash
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.

## Tasks

### Setup Auth0

1. Create a new Auth0 Account
2. Select a unique tenant domain
3. Create a new, single page web application
4. Create a new API
   - in API Settings:
     - Enable RBAC
     - Enable Add Permissions in the Access Token
5. Create new API permissions:
   - `get:drinks`
   - `get:drinks-detail`
   - `post:drinks`
   - `patch:drinks`
   - `delete:drinks`
6. Create new roles for:
   - Barista
     - can `get:drinks-detail`
     - can `get:drinks`
   - Manager
     - can perform all actions
7. Test your endpoints with [Postman](https://getpostman.com).
   - Register 2 users - assign the Barista role to one and Manager role to the other.
   - Sign into each account and make note of the JWT.
   - Import the postman collection `./starter_code/backend/udacity-fsnd-udaspicelatte.postman_collection.json`
   - Right-clicking the collection folder for barista and manager, navigate to the authorization tab, and including the JWT in the token field (you should have noted these JWTs).
   - Run the collection and correct any errors.
   - Export the collection overwriting the one we've included so that we have your proper JWTs during review!

### Implement The Server

There are `@TODO` comments throughout the `./backend/src`. We recommend tackling the files in order and from top to bottom:

1. `./src/auth/auth.py`
2. `./src/api.py`


### Barista Token: `eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6Ik1jZ184aDVYbWNBeV9lTGZ5V2hEUyJ9.eyJpc3MiOiJodHRwczovL3NtYXJ0ZW1waXJlMDA3LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJhdXRoMHw2MmJjNTQ3MzhhZmU3YjA3YzY5ZDM3NmMiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjUwMDAiLCJpYXQiOjE2NTY1MTM0MzcsImV4cCI6MTY1NjU5OTgzNywiYXpwIjoiV242NHNReVN6eVVRZXlBdDVXUmNHalBVbmxSTlVaNnMiLCJzY29wZSI6IiIsInBlcm1pc3Npb25zIjpbImdldDpkcmlua3MtZGV0YWlsIl19.W4FJCne6zrEEC5BtrnT-Oj0BuCn1D1WzxVKdCkxzgpNt4Q6kbDScmC1gdx-UDLnTdoYA9P11L49h5TmApq735vIWg5luVDs4uD2u91Mg3mqAnDj2A8S_kegkifALA3RZXv24zdh2gBfIS2sWkc8V9sZ3oBotDz4LWj1cmIxYl80tkZ6shgkh73LVugzZH9HZZu2Rgw8X5eDIZQd5D-rrP1qpdaFmeOZzx6PiZqCElkyxO4UnwvH_cCmEy5g-U49TgxSd59wChDbY7Y3rEhAgiko6VOPvl12tloErhO-llB56eTlzc6seeYrpEulU6MfhvqLHwFHY_u_-3NhorcVocw`


### Manager Token: `eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6Ik1jZ184aDVYbWNBeV9lTGZ5V2hEUyJ9.eyJpc3MiOiJodHRwczovL3NtYXJ0ZW1waXJlMDA3LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJnb29nbGUtb2F1dGgyfDEwMzc1MTc5MTI0Mzg1ODYyMTQ5MCIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NTAwMCIsImlhdCI6MTY1NjUxNDI5OSwiZXhwIjoxNjU2NjAwNjk5LCJhenAiOiJXbjY0c1F5U3p5VVFleUF0NVdSY0dqUFVubFJOVVo2cyIsInNjb3BlIjoiIiwicGVybWlzc2lvbnMiOlsiZGVsZXRlOmRyaW5rcyIsImdldDpkcmlua3MtZGV0YWlsIiwicGF0Y2g6ZHJpbmtzIiwicG9zdDpkcmlua3MiXX0.eAMhyJ5AdooUF8muO91zVcgqTMVosOp5I_umuGp4sEakb2LFm0MzL6Za37qXyUsAgWyNU41H6kQznf8zrUgEH2ndK5dHH6xYlnPBebzhgfJzo7cWTZtruCOCl0LJVkPSRzCw4A_lSvJ2y-xYo2C2BdGDgbBqbkop-Wxf8mnVjkqSR0ddreJAIYwFceaO91SEbBDlNp2p96k3GkhCGWipQlk0QIcndLA2n-7mWf_G_luZW_ny-OJpA03pLeLC6ZTbFcUC8pHcuxdH_8TmFo1fC6vYjEsXhsRTUvNpGB3I7iAZwmnynaaIZjL4o054Nw9JQExvV_P4uo4bG1p3_7P3CA`
