# Cluster Logs Demo with OpenTelemetry & ClickHouse®

A demo to collect all cluster logs with the OpenTelemetry Collector and send them to a ClickHouse instance. 

## Quickstart

This repository depends on an existing Kubernetes cluster with the [Altinity Operator](https://github.com/Altinity/clickhouse-operator) installed in the `kube-system` namespace.

Clone this repository and in the directory run (modifying the namespace as you see fit):

```
helm install cluster-logs-demo . --namespace=demo --create-namespace
```

## Connect

#### Grafana

Connect to Grafana:

```
kubectl port-forward -n monitoring services/monitoring-grafana 3000:80
```

You can then load Grafana in your browser at `http://localhost:3000` — there is no username or password.

## Architecture

### Components

- Altinity Operator (not included) - for creating and managing a ClickHouse Cluster
- ClickHouse - for storing log data
- OpenTelemetry Collector - deployed as a daemonset to collect node logs and metrics
    - OpenTelemetry Exoprter for ClickHouse - to forward logs data to ClickHouse
- Grafana - for visualizing logs
    - ClickHouse Plugin for Grafana - to connect ClickHouse as a Grafana datasource.

# Legal

Altinity®, Altinity.Cloud®, and Altinity Stable® are registered trademarks of Altinity, Inc. ClickHouse® is a registered trademark of ClickHouse, Inc.; Altinity is not affiliated with or associated with ClickHouse, Inc.
