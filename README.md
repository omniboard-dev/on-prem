# Omniboard On-Premise Distribution

# Getting Started

1. adjust values in the secret files in this folder
   * `api-admin-password` - password of initial Omniboard admin user
   * `db-user` - database user to connect backend to the DB
   * `db-user-password` - database password to connect backend to the DB
   * `db-root-password` - database root password for DB administration

2. adjust values in the `docker-compose.yml` file
   * `OB_ORG_ADMIN_EMAIL` - email of the initial Omniboard admin user
   * `OB_ORG_NAME` - name of your organization that will be generated in the backend
   * `ports` - (Optional) ports to expose frontend, backend and DB can be customized, by default frontend can be accessed on port `:80` which is `http://localhost` (and whatever the public url on which the system is accessible)

3. log into Docker using the `docker login` command with username `omniboard` and password `<your-omniboard-access-key>`

4. run `docker-compose up` to start the containers

5. access the running frontend (by default at [http://localhost](http://localhost)) and log in as an admin user with credentials provided previously:
   * email: `OB_ORG_ADMIN_EMAIL`
   * password: `api-admin-password`

6. finish initial setup

7. navigate to one of your project folders and run `npx @omniboard/analyzer --ak <your-api-key-from-initial-setup> --api http://localhost:8080` to get first results (`--api http://localhost:8080` assuming its on the same machine, else on a public URL where the Omniboard backend is running)

## Data persistence when pulling new image versions
...

## DB Administration

Database can be accessed using the provided `Adminer` image which will by default run at [http://localhost:8090](http://localhost:8090)
