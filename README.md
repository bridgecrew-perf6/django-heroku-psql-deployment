# How to structure your django app for deployment to Heroku

1. Set up your settings.py file as show and store your enviroment variables in the .env file

2. Login to heroku,create the app and git add the remote repository e.g
    ```heroku git:remote -a <heroku-repo>``

3. Add the enviroment variables as shown !(Screenshot)[img/heroku-env-variables.png]: 
    | Variable_Name       | Value            |
    | ------------------- | -----------------|
    | SECRET_KEY          | abr*@#-2-example |
    | DEBUG               | True             |
    | ALLOWED_HOSTS       | 127.0.0.1        |
    | DB_NAME             | DB_NAME          |
    | DB_HOSTS            | DB_HOSTS         |
    | DB_PASSWORD         | DB_PASSWORD      |
    | DISABLECOLLECTSTATC | 1

4. Git add , commit and push to heroku master and wait for it to install

5. Create a Postgres databast on heroku:

    ```heroku addons:create heroku-postgresql:hobby-dev``

6. Run migrations:
    ```heroku run python manage.py makemigrations```
    ```heroku run python manage.py migrate```
7. Migrate localdb to Heroku
    ```heroku pg:push <local-db> HEROKU_POSTGRESQL_NAVY_URL 
    --app <heroku-app-name>
