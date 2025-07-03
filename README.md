# emptyDir is used at the Pod level:
# hostPath is used to access the node's file system directly

# emptyDir definition:
•emptyDir will hold the volume until pod is available, if the pod deleted, then emptyDir volume will be deleted.
•	we have a pod and inside that pod, we are using two containers. if our requirement is to share a volume between those two containers (inside the single pod) then we will use the emptyDir volume type.
•	we have to define a volume which will be located inside the pod. and those two containers will share the volume.

# Advantages -
•	If one container gets deleted then the new container will automatically access the existing volume.

# Disadvantages -
•	We have to remember that the volume where is located in pod, if pod deleted then that volume would also be deleted.
•	we cannot share the volume between two pods

# host path definition:
host path is a type of ephemeral volume where pod can access the underlaying host files and directories. this is dangerous, but only one case, we can use the hostpath to access the server logs and pushing them into elastic search.
•	From emptyDir volume, we have seen the major disadvantages, two pods won’t share volume. To overcome that problem, we can use the hostPath volume where we can map the volume of a container with a host machine (Kubernetes node).
•	In this case if pods get deleted also then we can access the volume from the host machine (Kubernetes node). And also, we can share the volume with two or multiple pods.

# Advantages -
We can share this between multiple pods.
If pods get deleted then still, we can access the data from host machine.

# Disadvantages -
In case of hostPath, it is located on a single node but after destroying the pod, the new pod can be created on a different node. in that case, the new pod cannot access its previous hostPath location.


