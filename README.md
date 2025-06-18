# Kubernetes
Using this repo to learn and experiment with kubernetes

## What is Kubernetes? How is it different from Docker?
- Docker is a container platform.
- Kubernetes is a container ochestration platform.
- Containers are ephemeral in nature (have a short life, die and revive anytime)

### Problems with docker?
- *Single Host*: There are multiple containers hosted on a single host. If any of these conatiners is consuming more resources from the host (e.g. higher CPU consumption), other conatiners on the host will suffer. They might crash or be unable to come up because the host does not have enough resources now. 
- *No Auto-Healing*: Application running inside the conatiner will not be accessible. It needs manual intervention to start the conatiner again for the application to be accessible. Hence the lack of auto-healing makes docker conatiners un-relaiable for production apps.
- *No Auto scalling*: A conatiner running on a host can only consume the resources of the host even in the case of maximum traffic. There would be no concept of auto scalling to handle with more traffic.
- *No load balancing*: Docker cannot configure a load balancer out of the box for you even if you manually scale multiple container of the applications.


- *No enterprise level support*: Not fit for running production apps. No firewall, no auto-scaling, no support for api-gateways, no load balancers etc.

## How kubernetes is solving all of these problems?
- *Single Host*: K8s is a cluster. It is installed in a master-node architecture. (That does not mean you cannot install it on one single node. Dev envs are hosted on single node.) One faulty conatiner impacting the entire host, is automatically moved to a diffrent host. 
- *Auto-sclaing & Load-Balancing*: K8s proovides replication controller, also called replica-set. K8s is configured using YAML. To manually deal with more load, you can simply increase the count of replica-set to handle in the increased load. K8s aslo supports HPA (**Horizontal Pod Autoscaller**) which can directly increase the count of your pods based on the set thresholds. e.g. If the CPU on a POD reaches 80%, add more pods to the cluster.
- *Auto-healing*: If a container goes down, K8s will automatically sclae up a new container. K8s has an API server. When this API servers recieves a signal that a conatiner is going down, a new container is automatically scalled up even before the faulty container can die.
- *Enterprise Level Support*: CNCF is a community that constanlty focuses on making this application better. Has ingress controllers. More on that later.


# K8s Architecture 
-  Has a master node and a worker node
-  *Worker Node (Data Plane)*:
    - *Kube Proxy*: Networking of K8s. Provides IP address to your pods. Handles load balancing for k8s.
    - *Kubelet*: Responsible for creation of a pod. It also makes sure  that the pod is always running. If not running, it informs the master node(control plane), and gets it started again.
    - *Container runtime*: Dockershim, crio, conatinerd. Supports all of these container runtimes.
- *Control Plane/Master Node*
    - *API Server*: Core component of K8s. API server exposes your K8s to the external world and takes all the request. API server decidedes where the pod must be brought up
    - *Scheduler*: Recieves the information from the API server and takes the action of actually bringing the pod up.
    - *etcd*- Is a key/value store, that store all the information of configuration of the K8s cluster. Without etcd you won't have any cluster related information. If in any scenario you want to restoer th K8s cluster, etcd has the information of how it was built in the first place.
    - *Controller Manager*: k8s has multiple controllers like Repplica Controller, etc. Controller Manager makes sure that these controllers are always running. 
    - *Cloud Controller Manager*: CCM. It is an open source utility which has the logic for various cloud providers that allows kubernetes clusters to run on them. Basically allows Kubernetes to understand the cloud platform to allow the cluster to be hosted on there.
 
  
