# Getting Started with Helm Charts (Logging using Loki Stack)

This document explains how to get started with log aggregation for Scalar products on Kubernetes using Grafana Loki (with Promtail).

We assume that you have already read the [getting-started with monitoring](./getting-started-monitoring.md) for Scalar products and installed kube-prometheus-stack.

## What we create

We will deploy the following components on a Kubernetes cluster as follows.

```
+--------------------------------------------------------------------------------------------------+
| +------------------------------------+                                                           |
| |             loki-stack             |                                                           |
| |                                    |                                       +-----------------+ |
| | +--------------+  +--------------+ | <-----------------(Log)-------------- | Scalar Products | |
| | |     Loki     |  |   Promtail   | |                                       |                 | |
| | +--------------+  +--------------+ |                                       |  +-----------+  | |
| +------------------------------------+                                       |  | ScalarDB  |  | |
|                                                                              |  +-----------+  | |
| +------------------------------------------------------+                     |                 | |
| |                kube-prometheus-stack                 |                     |  +-----------+  | |
| |                                                      |                     |  | ScalarDL  |  | |
| | +--------------+  +--------------+  +--------------+ | -----(Monitor)----> |  +-----------+  | |
| | |  Prometheus  |  | Alertmanager |  |   Grafana    | |                     +-----------------+ |
| | +-------+------+  +------+-------+  +------+-------+ |                                         |
| |         |                |                 |         |                                         |
| |         +----------------+-----------------+         |                                         |
| |                          |                           |                                         |
| +--------------------------+---------------------------+                                         |
|                            |                                                                     |
|                            |         Kubernetes                                                  |
+----------------------------+---------------------------------------------------------------------+
                             | <- expose to localhost (127.0.0.1) or use load balancer etc to access
                             |
              (Access Dashboard through HTTP)
                             |
                        +----+----+
                        | Browser |
                        +---------+
```

## Step 1. Prepare a custom values file

1. Get the sample file [scalar-loki-stack-custom-values.yaml](./conf/scalar-loki-stack-custom-values.yaml) for the `loki-stack` helm chart.

## Step 2. Deploy `loki-stack`

1. Add the `grafana` helm repository.
   ```console
   helm repo add grafana https://grafana.github.io/helm-charts
   ```

1. Deploy the `loki-stack` helm chart.
   ```console
   helm install scalar-logging-loki grafana/loki-stack -n monitoring -f scalar-loki-stack-custom-values.yaml
   ```

## Step 3. Access the Grafana dashboard

1. Add Loki as a data source
   - Go to Grafana http://localhost:3000 (If you use minikube)
      - If you use a Kubernetes cluster other than minikube, you need to access the LoadBalancer service according to the manner of each Kubernetes cluster.
   - Move to `Configuration` and choose `Data Sources`
   - Click `Add data source`
   - Select `Loki`
   - Input `http://scalar-logging-loki:3100` to URL
   - Click `Save and test`
   - Go to `Explore` to find the added Loki

## Step 4. Delete the `loki-stack` helm chart

1. Uninstall `loki-stack`.
   ```console
   helm uninstall scalar-logging-loki -n monitoring
   ```
