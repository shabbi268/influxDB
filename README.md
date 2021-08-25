InfluxDB/Telegraf Monitoring System Logs
========================================

Table of contents
=================

<!--ts-->
  - [About](#about)
  - [Getting Started](#getting-started)
    - [Influx DB Setup](#influx-db-setup)
    - [Telegraf Setup](#telegraf-setup)
<!--te-->

## About
=================

This docker-compose.yml file is used to pull the latest InfluxDB Image from the DockerHub and build the image with the configurations provided in the `environment` section.

Use the Login credential in the `environment` section to login to the InfluxDB Web UI once we spin and bring up the InfluxDB Image.

## Getting Started
==================

### Influx DB Setup:
====================

- Clone this Repo and navigate to that repo from your favorite terminal.
- To start this project in your local environment, make sure you have Docker Desktop running and you can check whether Docker is running or not by running this command:
        `docker -version` 
    Which should display the version of the Docker thats running.

- Execute the below command in your terminal 
        `docker-compose up`
        This command will run the InfluxDB container in port number `8086`

- If the above command throws any error you can manually download InfluxDB image with below command:
        `docker pull influxdb`
    

- To check if the InfluxDB is up or not - navigate to `localhost:8086` and you should be able to see the Web UI Sign In page.

- Use the credentials from the `docker-compose.yml` file to login and view the DB Console.

### Telegraf Setup:
====================
- Telegraf is a tool used to send logs/data/metrics from you localSystem/server to InfluxDB/AnyOtherDB

- If you are Mac User execute below commands to install telegraf:
    `brew update && brew install telegraf`
    This will install telegraf in your local system

- Now we set some configurations for the telegraf package:
    - For this You have to navigate to Data tab in the InfluxDB Web UI and go to telegraf section and click on create configuration which will ask for what type of system you want to watch the metrics for
    - Select `System` and it will generate two commands which you can copy and execute them in you local terminal.
    - The commands would look something like this:
    `export INFLUX_TOKEN=<YOUR TOKEN>`
    `telegraf --config http://localhost:8086/api/v2/telegrafs/<SOME-TOKEN>`

- Once ypu execute both of those commands the telegraf starts sending your System Metrics to the InfluxDB and you can start viewing the metrics from the Explore Tab on side menu of Web UI.
