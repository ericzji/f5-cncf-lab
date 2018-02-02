.. _my-cluster-setup:

Prometheus installation
====================

Overview
--------

Installing Prometheus
-------------

Lets start with deploy the configuration for Prometheus using a config map using :
::
    kubectl create -f prometheus-config-map.yaml

Next we deploy Prometheus itself using a Kubernetes yaml file. Create a file named prometheus-deployment.yaml and paste in the following content
::
	kubectl create -f prometheus-deployment.yaml

We can now check the deployment status using
::
    kubectl get deployment

.. image:: ../images/prometheus-get-deployment.png
	:align: center

When the deployment is complete and the Prometheus pod is running we can visit the Prometheus UI using port-forwarding. First get the pod name using kubectl get pods. Then using:
::
    kubectl port-forward prometheus_pod_name 9090:9090

we can visit http://127.0.0.1:9090 and we should see the Prometheus user interface. This should look like this


Installing Grafana
-------------

Setting up Grafana
-------------
The last part is to setup Grafana. The default install we used for installing Grafana using Helm does not include a public IP adress for Grafana. So we have to use a kubectl port forward to connect to Grafana.
::
    kubectl port-forward my-grafana-pod-name 3000:3000

By visiting http://127.0.0.1:3000 we can now configure Grafana. Log in to Grafana using admin and the password we retrieved earlier. Inside Grafana add a datasource using the Prometheus service URL.

After the datasource has been added it is finally time to add a dashboard. Goto import dashboards inside and import a dashboard using ID 1621. Grafana dashboards can be shared on Grafana dashboards. Using this dashboard ID in the import and choosing our Prometheus datasource we created earlier we should now see our first Grafana dashboard.

Happy dashboarding!
