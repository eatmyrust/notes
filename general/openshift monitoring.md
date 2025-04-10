Monitoring in [[openshift]] comes preinstalled using [[prometheus]] and [[alertmanager]] managed by the openshift-monitoring operator. [[grafana]] was removed in favor of metrics dashboards directly in the openshift console.

Additional scrape configs for prometheus can be configured through the `cluster-monitoring-config` in the `openshift-monitoring` namespace.