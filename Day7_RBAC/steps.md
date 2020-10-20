### Generate key
openssl genrsa -out user1.key 2048

### Generate CSR (Certificate Signing Request)
openssl req -new -key user1.key -out user1.csr -subj "/CN=user1/O=testlab"

### Generate certificate
openssl x509 -req \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-in user1.csr \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-CA ~/.minikube/ca.crt \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-CAkey ~/.minikube/ca.key \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-CAcreateserial \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-out user1.crt \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-days 100
        
### Set credentials for Client user
kubectl config set-credentials user1 --client-certificate=user1.crt --client-key=user1.key

### Create a context pointing to user created before
kubectl config set-context user1-context --cluster=minikube --namespace=default --user=user1
###### To see the user and context created
`kubectl config view` 
###### To see current context
`kubectl config current-context`

## Role and Role binding
Create role
kubectl apply -f role.yml
Create role binding
kubectl apply -f role-binding.yml
To check them
`kubectl get roles`
`kubectl get rolebindings`

###### Change the current context to user1-context
`kubectl config use-context user1-context`
###### To see current context
`kubectl config current-context`
Now try viewing and creating pods. We can see everything about the pods but we cannot create one.

###### 
