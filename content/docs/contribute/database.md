+++
description = "Setup of database for development purpose."
title = "Database Setup"
weight = 10
+++

{{< tip "warning">}}
The database might change in future
{{< /tip >}}

# Database

Carbonaut requires a database, for now, we will run on PostgreSQL. It can be deployed anywhere and is available as managed service on many cloud providers and IaaS.

> Setup and execution can be problematic on M1 chip

## Run PostgreSQL as Docker

First, pull the docker image with PostgreSQL
```sh
sudo docker pull postgres:14
```

Before deploying, you'll need to set up a Docker volume or bind mount to persist your database. Otherwise, your data will be lost when the container restarts. The mount should be made to /var/lib/postgresql/data directory within the container.

The following command will create the volume in your local machine, which you can connect with PostgreSQL container as next step:
```sh
sudo docker volume create postgres-volume
# don't forget to set a password
sudo docker run -d --name=postgres14 -p 5432:5432 -v postgres-volume:/var/lib/postgresql/data -e POSTGRES_PASSWORD=[YOUR-SUPER-PASSWORD] postgres:14
```

Check the log files if everything is up and running 'sudo docker logs postgres14'. You should find as the latest entry a 'LOG:  database system is ready to accept connections.

The DB is ready for connection.


## Run PostgreSQL on Kubernetes/Minikube/Kind

Alternatively, to run just docker (or any other local container runtime) you can use a local or remote Kubernetes environment. For local development, we recommend [Minikube](https://minikube.sigs.k8s.io/docs/) or [kind](https://kind.sigs.k8s.io/). Please follow the corresponding instructions for the local setup of these Kubernetes distributions.

We deploy PostgreSQL via Helm:
```sh
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install postgres14 bitnami/postgresql
```
Read more about the installation in the PostgreSQL packaged by [Bitnami Chart Github repository](https://github.com/bitnami/charts/tree/master/bitnami/postgresql/#installing-the-chart).


## Run PostgreSQL locally
You can also run PostgreSQL locally. However, this is somewhat more complicated. Therefore we recommend the following instructions from [CodeCademy](https://www.codecademy.com/article/installing-and-using-postgresql-locally).
> Kudos to you, CodeCademy! 