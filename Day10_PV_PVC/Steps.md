### Create a directory
`/home/docker/persistentVolume`
### Create persistent volume
`kubectl create -f Persistent_Volume.yml`
### Get persistent volume
`kubectl get pv`
### Create persistent volume claim
`kubectl create -f Persistent_Volume_Claim.yml`
### Get Persistent Volume Claim
`kubectl get pvc`
### Create Pod using PVC
`kubectl create -f Pod.yml`
### Create file in the Pod
`kubectl exec pod-test ls /mydata`
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

`kubectl exec pod-test touch /mydata/hello` 
`kubectl exec pod-test ls /mydata`
> hello
### Delete Pod, Persistent Volume and Persistent Volume Claim
`kubectl delete pod pod-test`
`kubectl delete pv per-vol`
`kubectl delete pvc pv-c`

### Create Persistent Volume, Persistent Volume Claim and Pod again
`kubectl create -f Persistent_Volume.yml`
`kubectl create -f Persistent_Volume_Claim.yml`
`kubectl create -f Pod.yml`

### Check the file 
`kubectl exec pod-test ls /mydata`
> hello

If we had multiple nodes and created new pod in another node, we could not see the hello file.