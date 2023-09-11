# Vaultwarden on Render
This is a sample repo to run the latest version of [Vaultwarden](https://github.com/dani-garcia/vaultwarden) on Render. You need to add any free database backend (like PlanetScale) using the environment variables provided by the Vaultwarden Wiki. Below you can find some of the required and recommended ones:
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
- [Fly.io](https://fly.io/)
- [ElephantSQL](https://www.elephantsql.com/)

## Deployment

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/mostafa-abdelbrr/vaultwarden-render)
