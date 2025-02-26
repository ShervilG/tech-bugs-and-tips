#kubernetes #basics 

## Terminologies
It is a Container Orchestration framework.
- Contains Nodes -> Pods (each pod has typically 1 running container)
- Pods have internal IP addresses which change as pod dies and restarts.
- Services (have fixed IP) can be used for Pod communication->
	- Internal -> visible among the pods only
	- External -> visible from outside IP address
	- It also load balances b/w the pods
- We communicate with Ingress and Ingress communicates with Services
- Secrets and ConfigMap -> used to store runtime credentials, env varaibles etc.
- Volumes -> Internal or External Persistent Storage
- Deployment -> Blueprint for scaling up or down replicas/pods
	- StatefulSet -> for Stateful Apps such as DBs
![[Pasted image 20230318131706.png]]
- These 3 must be installed and running in the machines (nodes).
	- KubeProxy -> Handles communication b/w the pods
![[Pasted image 20230318132924.png]]
- Master Nodes handle Pod Health and shiz and Pod Scheduling
- Minukube -> 1 Nodes K8 Cluster with Worker and Master Processes on the same Node
- Kubectl -> Command Line tool that Interacts with Cluster and forwards commands/requests to the API Server
- 