Monitoring in [[openshift]] comes preinstalled using [[prometheus]] and [[alertmanager]] managed by the openshift-monitoring operator. [[grafana]] was removed in favor of metrics dashboards directly in the openshift console.

# Grafana Custom Install
To configure a custom installation of grafana to view openshift's metrics, you must do the following:

1. Bind the grafana service account to the `cluster-monitoring-view` cluster role
2. Create a service account token to allow grafana to authenticate to prometheus `oc create token grafana-serviceaccount --duration=8760h -n <grafana-ns>`
3. Create a datasource for grafana to access prometheus
```yaml
datasources:
- access: proxy
  editable: true
  isDefault: true
  jsonData:
	httpHeaderName1: 'Authorization'
	timeInterval: 5s
	tlsSkipVerify: true
  name: Prometheus
  secureJsonData:
	httpHeaderValue1: 'Bearer ${BEARER_TOKEN}'
  type: prometheus
  url: 'https://thanos-querier.openshift-monitoring.svc.cluster.local:9091'
```
# Openshift Alertmanager Configuration
To configure the default platform alerts edit the `alertmanager-main` secret in the `openshift-monitoring` namespace. There is also limited configuration available through the openshift console at `Administration -> Cluster Settings -> Configuration -> Alertmanager`.

Different Alertmanager receivers can be configured for default platform alerts and user defined alerts. Utilize the `openshift_io_alert_source="platform"` label to match on default platform alerts, and `openshift_io_alert_source!="platform"` label to match user defined alerts.