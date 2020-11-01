## First enable ingress in minikube
`minikube addons enable ingress`

## Create a service and pods, using Deployment is a good option
I have used Deployment_nginx.yaml, same as Day3_Deployment_02.yml

## Expose the port of the pods using service
`kubectl expose deployment app-deployment --port 80`

## Create ingress
`kubectl create -f Ingress.yml`

## Create a new deployment and expose port
`kubectl create -f Deployment_apache`
<br>
`kubectl expose deployment app-deployment-apache --port 80`

## Create ingress for Domain Based Routing
`kubectl create -f Ingress_Domain_Based_Routing.yml`
<br><br>
If you had previously running ingress, just overwrite using<br>
`kubectl apply -f Ingress_Domain_Based_Routing.yml`

## Create ingress for Path Based Routing
`kubectl create -f Ingress_Path_Based_Route.yml`
or
`kubectl apply -f Ingress_Path_Based_Route.yml`
<br>
Since, we donot have configured routing for apache, it gives 404 error. But we can see that the error is produced by apache. If we navigate to other routes, nginx returns 404 error, since nginx is used in ingress.




