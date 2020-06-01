# JenkinsDockerwithPrometheus
## In this i have illustrated how to setup Prometheus & Grafana in Kubernetes in container and integrating them ***

**Assumptions:Used vimal13/prometheus and vimal13/grafana images to lauch prometheus and grafana.Kubernetes is installed.Accessing through CLI.***

STEPS:

1- start minikube.exe service & check if there are any pods or other resources running.If running clean it.Make sure your environment is clean.
![](SDP1/1.PNG)

2- Launch a deployment with vimal13/prometheus image.
![](SDP1/2.PNG)

Check its status is its succesfully running or not
![](SDP1/3.PNG)

3-Now expose this deployment using patting.Using the Port number we can access Prometheus succesfully on browser using IP
![](SDP1/4.PNG)
![](SDP1/5.PNG)

4-Launch a deployment with vimal13/grafana image.
![](SDP1/6.PNG)

Check its stautus if its successfully running
![](SDP1/7.PNG)

5- -Now expose this deployment using patting.Using the Port number we can access Grafana succesfully on browser using IP
![](SDP1/8.PNG)
![](SDP1/9.PNG)

6-Create a data source in Grafana and give Prometheus URL.
![](SDP1/10.PNG)

***Now here we will make Prometheus monitor three nodes:
```
node 0:It will monitor itself by default
node 1:It will monitor node which has RHEL8 and has node_exporter program running
node 2:It will monitor node which has RHEL8 and has node_exporter program running
node 3:It will monitor docker
```
For this we will follow following steps:***

7-Run the node_exporter program in node 1.
![](SDP1/11.PNG)

8-Run the node_exporter program in node 2.
![](SDP1/12.PNG)
![](SDP1/13.PNG)

9-Here node 2 has daemon.json file setup,so that Prometheus can monitor docker.Now go to cmd in Windows and get into prometheus pod and add jobs to prometheus.yml file .These jobs contain IPs of the nodes which Prometheus has to monitor
![](SDP1/14.PNG)
![](SDP1/15.PNG)

10-Now run the following kill -HUP command using the Prometheus ProcessID so that Prometheus runs without downtime
![](SDP1/16.PNG)

Now on Prometheus WEBUI we can see our nodes
![](SDP1/17.PNG)

Use the UP command to see the nodes monitored by Prometheus
![](SDP1/18.PNG)

![](SDP1/19.PNG)

11-Now we can also do visualisation using Grafana by creating Graph
![](SDP1/20.PNG)
![](SDP1/21.PNG)






