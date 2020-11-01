## Create a deployment
Create a deployment using `Initial_Deployment.yml` file.<br>
`kubectl create -f Initial_Deployment.yml`
## Create deployment using RollingUpdate strategy
Create deployment using RollingUpdate strategy `Deployment_Recreate.yml` file<be>
`kubectl create -f Deployment_RollingUpdate.yml`<br><br>
Update the image from nginx:1.19.3 to nginx and apply the changes.
`kubectl apply -f Deployment_RollingUpdate.yml`<br><br>
View the description of the Deployment using `kubectl describe deployment <deployment_name>`<br>
We can see the changes occured when the image was updated.
## Create deployment using Recreate strategy
Create deployment using Recreate strategy `Deployment_Recreate.yml` file<be>
`kubectl create -f Deployment_Recreate.yml`<br><br>
Update the image from nginx:1.19.3 to nginx and apply the changes.
`kubectl apply -f Deployment_Recreate.yml`<br><br>
View the description of the Deployment using `kubectl describe deployment <deployment_name>`<br>
We can see the changes occured when the image was updated. And we can see how it differs from Rolling Update strategy.