# KickStart
Create kubernetes object<br>
`kubectl create -f <file_name>`

## Pods
#### Get list of pods
`kubectl get pods`
#### For wide output
`kubectl get pods -o wide`
#### Get detailed description of pod
`kubectl get pod <pod_name>`
#### Delete a pod
`kubectl delete pod <pod_name>`

## Replica Controller
#### Get list of Replication Controllers
`kubectl get replicationcontroller`<br>
You can use rs instead of replicationcontroller
#### Get detailed description of Replication Controller
`kubectl describe replicationcontroller <replication_controller_name>`
#### Delete a Replication Controller
`kubectl delete replicationcontroller <replication_controller_name>`

## Replica Set
#### Get list of Replica Set
`kubectl get replicaset`<br>
You can also use rs instead of replicaset
#### Get detailed description of Replica Set
`kubectl describe replicaset <replica_set_name>`
#### Delete a Replica Set
`kubectl delete replicaset`

# Scaling
#### Changing from file
`kubectl replace -f <file_name>`
#### Scaling without file change
`kubectl scale --replicas=<no_of_new_replicas> -f <file_name>`<br>
Eg. `kubectl scale --replicas=5 -f <file_name>`
#### Scaling using resource name
`kubectl scale --replicas=<no_of_new_replicas> <resource_type> <resource_name>`<br>
Eg. `kubectl scale --replicas=5 replicaset <resource_name>`
