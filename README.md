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

### How to add packages?

You can add packages directly in RStudio, but this packages will not be available if you stop the container. If you want to add packages permanently you need to add this packages during the build of R image. It sounds complicated but it's simple! You just need to add a command on Dockerfile (present in this repository) after the FROM statement. Example:

```
FROM rocker/rstudio:3.4.4

RUN R -e "install.packages('here', repos='http://cran.rstudio.com/')"

expose 8787
```

This will install the package [here](https://github.com/r-lib/here)! Great package by the way.

Now you need to rebuild the image. To do this execute the follow command:
Obs: stop the container (with ctrl + c or doing `docker-compose down`)

```
docker-compose up --build
```

You can run just the build doing `docker-compose build`. To execute the service again you need to do `docker-compose up`.

If you have any problems please open a [issue](https://github.com/gileadekelvin/r-docker/issues)!