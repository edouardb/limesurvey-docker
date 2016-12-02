# Docker Limesurvey

This repository lets you run Limesurvey in multiple Docker containers. Docker Compose is used for orchestration.

## Containers

This compose environment uses 2 containers:

- dblimesurvey: A postgres database that contains Limesurvey data.
- limesurvey: The Limesurvey app build from the sources.

## Requirements

You need to have [Docker Compose](https://docs.docker.com/compose/install/) installed.

## How to use it?

### Start the environment

In the project root directory run the following command:

`docker-compose up -d`

This command build and get the Docker images and run the containers.

### Log in to the containers

You can log in to any of the container by running the following command:

`docker exec -i -t <container-name> bash`

