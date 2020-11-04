# Enable metrics server 
`minikube addons enable metrics-server`<br>
To verify if metrics server is enabled,<br>
`minikube addons list` 
# Create a Horizontal Pod Autoscaler for CPU utilization
Create a Horizontal Pod Autoscaler using `HPA.yml`. 
# Create a Deployment and expose it
Create a Deployment using `HPA_Deploy.yml`<br>
Now create a service to expose the Deployment.
`kubectl expose deployment mem-autoscale-deployment --port 80`<br>
# Get IP and test load
Get the ip of the service `minikube service mem-autoscale-deployment --url`<br>
Copy the IP into `KPA_test.js`<br>
Run `k6 run KPA_test.js`<br>
The load is being generated, meanwhile in other terminal, `watch kubectl get all`.<br>
We can see pods being created. It scales down after the load decreases. <br><br>
For the autoscaling purpose, it uses the formula
> desiredReplicas = ceil [ currentReplicas * ( currentMetricValue / desiredMetricValue ) ]

<a href="https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/#algorithm-details">More details on Autoscaling</a>