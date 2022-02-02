# Omniboard On-Prem Distribution

# Getting Started

## Quick Start

1. clone the this (`omniboard-dev/on-prem`) repository using `git clone https://github.com/omniboard-dev/on-prem.git`
2. log into Docker using the `docker login` command with username `omniboard` and password `<omniboard-docker-hub-access-token>`
3. run `docker compose up` to start the containers
4. open the browser to `http://localhost` and login using default credentials
   - email: `admin@awesome.com`
   - password: `admin`
5. complete initial setup wizard and copy the generated analyzer command (including API key)
6. navigate to some local project repository and run command from your clipboard (add `--api http://localhost:8080` to the command to access your local Omniboard instance)

## Advanced Start Setup

1. adjust values in the secret files in this folder

   - `api-admin-password` - password of initial Omniboard admin user
   - `db-user` - database user to connect backend to the DB
   - `db-user-password` - database password to connect backend to the DB
   - `db-root-password` - database root password for DB administration

2. adjust values in the `docker-compose.yml` file

   - `OB_ORG_ADMIN_EMAIL` - email of the initial Omniboard admin user
   - `OB_ORG_NAME` - name of your organization that will be generated in the backend
   - `ports` - (Optional) ports to expose frontend, backend and DB can be customized, by default frontend can be accessed on port `:80` which is `http://localhost` (and whatever the public url on which the system is accessible)

3. log into Docker using the `docker login` command with username `omniboard` and password `<omniboard-docker-hub-access-token>`

4. run `docker compose up` to start the containers

5. access the running frontend (by default at [http://localhost](http://localhost)) and log in as an admin user with credentials provided previously:

   - email: `OB_ORG_ADMIN_EMAIL`
   - password: `api-admin-password`

6. finish initial setup

7. navigate to some local project repository and run command from your clipboard (add `--api http://localhost:8080` to the command to access your local Omniboard instance)

## Data persistence when pulling new image versions

By default, Omniboard will keep the data from the previous version of the image in the standalone Docker volume.
Stopping (or even removing) of the images will not affect the Omniboard data (stored in the standalone Docker volume).

The data volume can be removed using the `docker compose down -v` command, please be extremely careful as running this will result in loosing of all the data.

## DB Administration (optional)

Database can be accessed and managed using the provided `Adminer` image which will by default run at [http://localhost:8090](http://localhost:8090)
