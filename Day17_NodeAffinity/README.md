# Create Pod using Node Affinity
Create pods using `SSD.yml`. We can see pending status of the Pod. 
Get description of the pod and we can see:
> 0/1 nodes are available: 1 node(s) didn't match node selector.

Lets delete the pod and change `operator: In` to `operator: NotIn` and create the pod. Now, the pod is created successfully.<br>
To assign label to node, use ` kubectl label nodes <node-name> <label-key>=<label-value>`