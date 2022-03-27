# monitoring

Monitoring tools for Scalar products.
Current chart version is `0.1.0`

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://prometheus-community.github.io/helm-charts | kube-prometheus-stack | 34.2.* |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| kube-prometheus-stack.alertmanager.alertmanagerConfigNamespaceSelector | string | `nil` | Only check own namespace |
| kube-prometheus-stack.alertmanager.enabled | bool | `true` | alertmanager is enabled |
| kube-prometheus-stack.coreDns.enabled | bool | `false` | Scraping CoreDNS is disabled |
| kube-prometheus-stack.defaultRules.create | bool | `false` | Default PrometheusRules are not enabled |
| kube-prometheus-stack.grafana.defaultDashboardsEnabled | bool | `false` | Default Grafana dashboards are not enabled |
| kube-prometheus-stack.grafana.enabled | bool | `true` | grafana is enabled |
| kube-prometheus-stack.grafana.sidecar.dashboards.enabled | bool | `true` |  |
| kube-prometheus-stack.grafana.sidecar.dashboards.label | string | `"grafana_dashboard"` |  |
| kube-prometheus-stack.grafana.sidecar.dashboards.labelValue | string | `"1"` |  |
| kube-prometheus-stack.grafana.sidecar.resources | object | `{}` | Resource limits & requests |
| kube-prometheus-stack.kubeApiServer.enabled | bool | `false` | Scraping kube-apiserver is disabled |
| kube-prometheus-stack.kubeControllerManager.enabled | bool | `false` | Scraping kube-controller-manager is disabled |
| kube-prometheus-stack.kubeEtcd.enabled | bool | `false` | Scraping etcd is disabled |
| kube-prometheus-stack.kubeProxy.enabled | bool | `false` | Scraping kube-proxy is disabled |
| kube-prometheus-stack.kubeScheduler.enabled | bool | `false` | Scraping kube-scheduler is disabled |
| kube-prometheus-stack.kubeStateMetrics.enabled | bool | `false` | kube-state-metrics is disabled |
| kube-prometheus-stack.kubelet.enabled | bool | `false` | Scraping kubelet is disabled |
| kube-prometheus-stack.namespaceOverride | string | `""` |  |
| kube-prometheus-stack.nodeExporter.enabled | bool | `false` | node-exporter is disabled |
| kube-prometheus-stack.prometheus.enabled | bool | `true` | Prometheus is enabled |
| kube-prometheus-stack.prometheus.prometheusSpec.podMonitorNamespaceSelector | object | `{}` | Only check own namespace |
| kube-prometheus-stack.prometheus.prometheusSpec.podMonitorSelectorNilUsesHelmValues | bool | `false` | All PodMonitors are enabled |
| kube-prometheus-stack.prometheus.prometheusSpec.probeNamespaceSelector | object | `{}` | Only check own namespace |
| kube-prometheus-stack.prometheus.prometheusSpec.probeSelectorNilUsesHelmValues | bool | `false` | All Probes are enabled |
| kube-prometheus-stack.prometheus.prometheusSpec.resources | object | `{}` |  |
| kube-prometheus-stack.prometheus.prometheusSpec.ruleNamespaceSelector | object | `{}` | Only check own namespace |
| kube-prometheus-stack.prometheus.prometheusSpec.ruleSelectorNilUsesHelmValues | bool | `false` | All PrometheusRules are enabled |
| kube-prometheus-stack.prometheus.prometheusSpec.serviceMonitorNamespaceSelector | object | `{}` | Only check own namespace |
| kube-prometheus-stack.prometheus.prometheusSpec.serviceMonitorSelectorNilUsesHelmValues | bool | `false` | All ServiceMonitors are enabled |
| kube-prometheus-stack.prometheus.prometheusSpec.storageSpec | object | `{}` |  |
| kube-prometheus-stack.prometheusOperator.admissionWebhooks.patch.resources | object | `{}` | Resource limits & requests |
| kube-prometheus-stack.prometheusOperator.enabled | bool | `true` | Prometheus Operator is enabled |
| kube-prometheus-stack.prometheusOperator.kubeletService.enabled | bool | `false` | kubelet service for scraping kubelets is disabled |
| kube-prometheus-stack.prometheusOperator.namespaces.releaseNamespace | bool | `true` | Only check own namespace |
| kube-prometheus-stack.prometheusOperator.resources | object | `{}` |  |
| kubePrometheusStack.enabled | bool | `true` |  |
