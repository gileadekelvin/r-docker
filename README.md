## RStudio and Docker

This repository allows you to execute R and RStudio via docker directly in your browser.

First, if you want to set the user and password default, you need to create a file named .env (`touch .env`). Then you need to add the follow lines:

```
USER_RSTUDIO=<user>
PASSWORD_RSTUDIO=<password>
```

You can choose not to do this and then use the user and password:
User: admin
password: secret

To start the whole process, please execute:

```
docker-compose up
```

You can access localhost:8787 on a browser and type the user and the password.

It Works!!! Awesome, right?

You can save files in folder called workspace. Everything that you save in workspace will be saved even if you stop the container. You can access this files outside container too. If you copy files to this folder (workspace) on your local machine they will be available on Rstudio too.

If you have any problems please open a issue!