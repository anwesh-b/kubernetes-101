# Create Deployment without ConfigMap and Secret
Create a deployment with eclipse-mosquitto image. <br>
`kubectl create -f Initial_Deployment.yml`<br>
Check the running pods with `kubectl get pods`and get the name of the pod.<br>
Get into the container using `kubectl exec --it <pod_name> -- /bin/sh`. Now you are into the container.<br>
`cd mosquitto` and check the files.<br>
`cd config` and read the `mosquitto.conf` file.<br>
There are all the default configuration and files.
# Create ConfigMap
Create ConfigMap from ConfigMap.yaml file<br>
`kubectl create -f ConfigMap.yml`
# Create Secret
Create Secret from Secret.yaml file<br>
`kubectl create -f Secret.yml`
# Create Deployment using without ConfigMap and Secret
Create deployment using ConfigMap and Secret<br>
`kubectl create -f Mosquitto.yml`
Now follow all the steps from first Deployment and check `mosquitto` folder and `mosquitto.conf` file.<br>
We can see the files from our config map and secrets
