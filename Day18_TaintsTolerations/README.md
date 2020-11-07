# Add taint to node
It will be better using cluster with multiple node rather than a single node.<br>
Get the name of node using `kubectl get nodes`<br>
Note the node name and run `kubectl taint nodes <node_name> <key>=<value>:<Taint_Effect>`<br>
I will use `kubectl taint nodes minikube key1=value1:NoSchedule`
# Create deployment without toleration
Create a Deployment using `Deployment.yml`. After creation, we can see the pods in `Pending` state. Lets see the description of the pod. We see
>0/1 nodes are available: 1 node(s) had taint {key1: value1}, that the pod didn't tolerate.

The reason for this is we do not have any toleration for the pod.
# Create deployment with toleration 
Create Deployment with `Toleration.yml` And when we see the pods, we can see the pods running.
<br><br>
Other operators are "Exists", which checks if key is present or not.<br>
Effect are "PreferNoSchedule" and "NoExecute".<br>
"tolerationSeconds" specifies how long the pod remains in the node after taint is added<br>
More details <a href="https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/">here</a>