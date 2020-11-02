# Create a namespace
As, Resource Quota is applied to a namespace, not entire cluster, lets create namespace.<br>
`kubectl create namespace quota`
# Create a Resource Quota
Create a Resource Quota from `Resource_Quota.yml` file in `quota` namespace.<br>
Get about the quota through
`kubectl describe quota resource-quota -n quota`
### Create pods
Lets create a deployment with nginx pod in `quota` namespace.<br>
`kubectl create deployment nginx --image=nginx -n quota`<br>
Scale the replicas to 2.
`kubectl scale deployment nginx replicas=2 -n quota`<br>
Get all the resources
`kubectl get all -n quota`<br>
We can see 2 pods running. Lets scale it to 3.<br>
`kubectl scale deployment nginx replicas=3 -n quota`<br>
Get all the resources
`kubectl get all -n quota`<br>
We can see that even though we scaled our deployment to 3 replicas, there is only 2 pod running.<br>
Get the name of replica set and see the description. `kubectl describe replicaset <replicaset_name> -n quota`<br>
We can see the error message, 
>Error creating: pods "nginx-6799fc88d8-v22km" is forbidden: exceeded quota: resource-quota
, requested: pods=1, used: pods=2, limited: pods=2
# Create memory limit
Create Resource Quota with file `Memory_Quota.yml`<br>
Create Deployment with `Memory_Deployment.yml` file. And our deployment is ready.<br>
`kubectl get all -n quota` to see all the resources running.<br>
To check the quota, `kubectl describe quota mem-quota -n quota` and we can see the memory used and limit.<br>
Lets scale our replicas to 6 and apply the changes.<br>
`kubectl apply -f Memory_Deployment.yml`<br>
Get the replicaset and see the description like before. And we can see the error.
>Error creating: pods "quota-deploy-86cd949489-r4qdg" is forbidden: exceeded quota: mem-quota, requested: limits.memory=100Mi, used: limits.memory=500Mi, limited: limits.memory=500Mi
# Create request limit
Create Resource Quota with file `Memory_Quota2.yml`<br>
Create a Pod with file `Memory_Pod.yml`. We have set its memory to `200Mi`.<br>
`kubectl create -f Memory_Pod.yml` gives an error.
> Error from server (Forbidden): error when creating "Memory_Pod.yml": pods "mem-pod" is forbidden: exceeded quota: mem-quota, requested: requests.memory=200Mi, used : requests.memory=0, limited: requests.memory=100Mi

This way we can define limit for a single request.<br>
Lets add `requests.memory: "50Mi"` in `Memory_Pod.yml` file, and this will change request of the pod to 50Mi. And the pod is created. We can see the pod using `kubectl get pods -n quota`.
# Create a Limit Range
Create a limit range using `LimitRange.yml` and create a pod using `Pod.yml` file.<br>
Execute `kubectl describe pod limit-range -n quota` and we can see
>  Limits:<br>
&nbsp;&nbsp;&nbsp;memory:&nbsp;&nbsp;&nbsp;200Mi<br>
Requests:<br>
&nbsp;&nbsp;&nbsp;memory:&nbsp;&nbsp;&nbsp;50Mi

The `LimitRange.yml` sets the default memory for the pods automatically. This can also be used to configure default CPU constraints, maximum and minimum memory, CPU constraints and Storage consumption. 


