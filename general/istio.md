Istio is a service mesh that implements networking capabilities for increased security, performance, and monitoring. It provides mutual TLS, load balancing, fine grained control over traffic behavior, a policy layer for access controls, rate limits, and quotas, and automatic metrics.

Istio runs on kubernetes and can be utilized for applications within the same cluster it is deployed to, extend the mesh to other clusters, or connect to VMs outside of kubernetes.

A proxy is utilized to intercept all network traffic entering or exiting a service. The proxy can either run in sidecar mode, where every pod gets a sidecar, or in ambient mode, where the proxy is deployed per node or per namespace. Sidecar mode provides all istio features but it much more resource intensive, while ambient mode provides most features and requires less resources, but works best at layer 4.

Istio offers the ability to operate at [layer 4 and layer 7](https://istio.io/latest/docs/overview/dataplane-modes/#layer-4-vs-layer-7-features) of the networking stack. Layer 7 functionality requires substantially higher processing than the processing of network packets at layer 4 does. Utilizing layer 7 functionality is only necessary if fine grained control at the application level is need, such as needing to set a rule that service A can only reach service B at endpoint `/foo`.

