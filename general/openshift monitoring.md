Monitoring in [[openshift]] comes preinstalled using [[prometheus]] and [[alertmanager]] managed by the openshift-monitoring operator. [[grafana]] was removed in favor of metrics dashboards directly in the openshift console.

To configure a custom installation of grafana to view openshift's metrics, you must do the following:

1. Bind the grafana service account to the `cluster-monitoring-view` cluster role
2. 