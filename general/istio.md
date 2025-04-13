Istio is a service mesh that implements networking capabilities for increased security, performance, and monitoring. It provides mutual TLS, load balancing, fine grained control over traffic behavior, a policy layer for access controls, rate limits, and quotas, and automatic metrics.

Istio runs on kubernetes and can be utilized for applications within the same cluster it is deployed to, extend the mesh to other clusters, or connect to VMs outside of kubernetes.

A proxy is utilized to intercept all network traffic entering or exiting a service. The proxy can either run in sidecar mode, where every pod gets a sidecar, or in ambient mode, where the proxy is deployed per node or per namespace.