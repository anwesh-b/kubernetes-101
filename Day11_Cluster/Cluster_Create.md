# VM Installation
- Install VMs with more than 2GB ram for master node and 1200MB for worker nodes. Else, the nodes might not be supported by Kubernetes.
- Swap memory is not supported and we need to disable it later. It is best create VM without swap.
# Install Docker
Since latest docker might not be supported by Kubernetes, refer to Kubernetes documentation.<br>
https://kubernetes.io/docs/setup/production-environment/container-runtimes/
# Install Kubeadm, kubelet and kubectl 
Kubeadm is a tool build a Kubernetes cluster. It performs all the task needed for a minimum viable cluster.<br>
Kubelet is low level component of Kubernetes. It manages all stuffs for running containers. It is responsible for what is running in a node.<br>
Kubectl is a CLI tool to run commands for Kubernetes cluster.
<br>
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
# Create cluster using Kubeadm
After installing, kubeadm, kubelet and kubectl on all the nodes, run the following steps on master node to create Kubernetes Cluster. In last, use `kubeadm join` in worker node to join the cluster.
<br>
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/
# Create Deployment
Now create deployment using `Deployment.yml`<br>
Use `kubectl create -f Deployment.yml` on master node
<br><br>
After creating, list the pods in wide mode to view the node in which the pod is running.
<br>`kubectl get pods -o wide`