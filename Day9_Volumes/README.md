## SSH into minikube
Since our host is minikube, create a directory in minikube.
Get the directory path
`/home/docker/volume`

## Create a pod 
Create a pod using the path


kubectl expose pod volume-pod --type=NodePort --port=80

minikube service volume-pod to open in browser

We can see welcome to kubernetes

Delete the pod and create a new pod using the same hostpath in volume

minikube service volume-test-pod and see the browser

We can see the same output we got previously