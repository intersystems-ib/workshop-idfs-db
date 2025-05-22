# workshop-idfs-db
THe main goal of this project is to deploy different databases to demo IDFS solution. You'll find a MySQL, an Oracle and a IRIS database (the only JDBC connectors available for IDFS).

You can find more in-depth information in https://learning.intersystems.com.


# What do you need to install? 
* [Git](https://git-scm.com/downloads) 
* [Docker](https://www.docker.com/products/docker-desktop) (if you are using Windows, make sure you set your Docker installation to use "Linux containers").
* [Docker Compose](https://docs.docker.com/compose/install/)
* [Visual Studio Code](https://code.visualstudio.com/download) + [InterSystems ObjectScript VSCode Extension](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript)

# Setup
Build the image we will use during the workshop:

```console
$ git clone https://github.com/intersystems-ib/workshop-idfs-db
$ cd workshop-py-performance
$ docker-compose build
```

# Configuration

This project should be deployed in a AWS instance to make it accesible to IDFS. This project has a Jupyter Notebook configured to populate the databases.


## Test Production 
* Run the containers that we will use in the workshop:
```
docker-compose build

docker-compose up -d
```
Automatically an IRIS instance, a MySQL and an Oracle databases will be deployed, a Jupyter Notebook is deployed under (http://localhost:8888) too.

You can check PostgreSQL and MySQL databases from Adminer 

## MySQL Adminer

* Open [Adminer](http://localhost:8081) using the following parameters:
  * Server: `mysql`
  * Username: `testuser`
  * Password: `testpassword`
  * Database: `test`

## IRIS database

* Open the [Management Portal](http://localhost:52774/csp/sys/UtilHome.csp).
* Login using the default `superuser`/ `SYS` account.
* Open System Explorer --> SQL
* Select NAMESPACE USER and Schema `Test`

# Testing with Jupyter Notebook

This project is devolped in Python using Jupyter Notebook, you can access to it from [here](http://localhost:8888) and open PerformanceTests.ipnyb file.
![alt text](/images/jupyter.png)

You can test the project step by step or execute it at one time, feel free.