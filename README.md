# Vaultwarden on Render
This is a sample repo to run the latest version of [Vaultwarden](https://github.com/dani-garcia/vaultwarden) on Render. You need to add any free database backend (like PlanetScale) using the environment variables provided by the Vaultwarden Wiki. Please check their wiki/documentation for more environment variables and how to use them. Below you can find some of the required (bare minimum to run this hosting configuration) and recommended ones:
|Environment Variable|Required?|Explanation|
|---|-|---|
|ADMIN_TOKEN|No|For admin access to admin dashboard, use [this wiki page](https://github.com/dani-garcia/vaultwarden/wiki/Enabling-admin-page) for instructions on how to generate a secure token. This repo will auto generate a value which you can change later by going to your Render dashboard then go to your service then go to `Environment` tab end edit its value. If you want to completely disable it then remove the environment variable entirely|
|DATABASE_URL|Yes|For database access to store info|
|SIGNUPS_ALLOWED|No|Allows users to sign up, set it to `false` after you make your own account on your hosted instance if you don't want anyone else to be able to sign up, allowed values are `true` or `false`|
|WEB_VAULT_ENABLED|No|Allows access to the web interface without needing the desktop and mobile clients or browser extensions. Values are `true` or `false`|

# Connection String
You can get it from whatever host you use.
### PlanetScale
For PlanetScale it provides multiple formats, you need to find the one that looks like this:  
```
<database_type>://<username>:<password>@<host>/<database_name>
```  
Manually append this to the end:
```
?sslaccept=strict&ssl_ca=/etc/ssl/certs/ca-certificates.crt
```
End result format:
```
<database_type>://<username>:<password>@<host>/<database_name>?sslaccept=strict&ssl_ca=/etc/ssl/certs/ca-certificates.crt
```
### Other free database providers:
- [Supabase](https://supabase.com/)  
- [Fly.io](https://fly.io/)
- [ElephantSQL](https://www.elephantsql.com/)
For more as well as usage limits and databse types, check [this gist](https://gist.github.com/bmaupin/0ce79806467804fdbbf8761970511b8c). Please note that it must be a database backend supported by Vaultwarden itself like MySQL and Postgres! If you find any more comprehensive list of free database backends, please hit me up in issues.

## Deployment

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/mostafa-abdelbrr/vaultwarden-render)

## Upgrading
This uses Vaultwarden's latest Docker image, so just manually deploy latest commit on Render. If you get DB connection errors, shut it down completely from the settings and then restart after a few minutes or set the DB connections environment variable to a number less than or equal to half the max limit provided by the DB hosting service to avoid this problem.
