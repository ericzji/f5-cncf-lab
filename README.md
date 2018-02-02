F5 CNCF Labs
==================

This introductory lab covers the following topics:


Lab 1: Install a Kubernetes Cluster (1 Master and 2 nodes)
===================================================
Lab 2: How to install and use F5 Container connector
====================================================
This lab covers the following topics:

- Install the F5 Kubernetes BIG-IP Controller
    - BIG-IP setup
    - Container Connector deployment
- Deploy an application and leverage our CC
    - Define a deployment
    - Define a ConfigMap
    - Define a Service

Lab 3: Kubernetes cluster monitoring with Prometheus and Grafana
====================================================
If you are using minikube, please follow the following document:
docs/prometheus/prometheus-grafana-installation.rst

For my case, I use kubeadm to build my own Kubernetes Cluster (1 Master and 2 nodes). I encountered some issue with above steps.
Instead, I leveraged kube-prometheus to use a single command for installation.

```
    git clone https://github.com/coreos/prometheus-operator.git
```
Simply run:

```
export KUBECONFIG=<path> # defaults to "~/.kube/config"
cd contrib/kube-prometheus/
hack/cluster-monitoring/deploy
After all pods are ready, you can reach:
```
Prometheus UI on node port 30900
- Alertmanager UI on node port 30903
- Grafana on node port 30902
- To tear it all down again, run:

```
hack/cluster-monitoring/teardown
```
Lab 4: gRPC
====================================================
Lab 5: OpenTracing and Jaeger
====================================================
Lab 6: CoreDNS
====================================================
Lab 7: Fluentd and Distributed Logging
====================================================