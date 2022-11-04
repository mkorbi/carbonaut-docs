+++
description = "Setup of database for development purpose."
title = "Database Setup"
weight = 10
+++

{{< tip "warning">}}
The database might change in future
{{< /tip >}}

# Database

We will run Carbonaut on Mimir as time series database, as we have to deal with many series of different data streams. Mimir requires an S3 compatible storage and is able to run on any cloud provider as well as on local environments.


## Run Mimir locally on kind/miniKube/microK8s

To get the things started localy you need a K8s like [kind](https://kind.sigs.k8s.io/). Create the kind cluster with the dev [config](https://github.com/carbonaut-cloud/carbonaut/tree/main/deployment/dev) `kind create cluster --config ./deployment/dev/kind-conf.yaml`. Ensure that you have the dependencies available via 'helm dependency build ./deployment'.

Next, get Mimir & Grafana started. 
```
kubectl create namespace carbonaut
helm upgrade carbonaut ./deployment --namespace carbonaut -i
```

To access Grafana (http://localhost:3000/) get the password and port-forward the dashbaord
```
kubectl port-forward service/carbonaut-grafana 3000:80 -n carbonaut
kubectl get secret -n carbonaut carbonaut-grafana -o jsonpath="{.data.admin-password}" | base64 --decode
```

Username: admin ;)
