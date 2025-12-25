# Docker is a container platform 
    - it is platform to make , run and manage the container

# Kubernetes is a container orchestration platform
     the container are ephemeral means the life of the container are very short

1. Single User 
     the problem is that lets say we have 100 container and we want to run the container in the same time and one container is crashed bcz of resource are used by other container so the linux have to  kill the container acc to its policy so it create 
     prblm bcz of **Single User**  ( Single host - the container are impacting one another)

2. Killed container
     if the container is killed bcz of some reason then in the docker the container will not auto restart (suto healing) 
     so we have kubernetes for tha **Auto Healing**

3. Auto Scaling
     we required the load balanceer to balance the load the docker dont have that thing so we have to use kubernetes

4. Simple 
     it doesn't have the enterprise support  like load-balancerr , internet-gateway , firewalls ,load-balancer etc 


# Kubernetes 
    In general k8s is a cluster - grp of nodes and master node 

    -In the cluster if anyone cause prblm then the k8s move that pod to other node and then it will be fixed

    -k8s have the concept of **ReplicaSet** so when configure the yaml file and say whenever the load is inc replica the current node to distribute the load .

    - K8s  have the controlm and fix the damage so whenever the container is going down k8s start(roll down) the container immedaitely or even before it actually going down  by api-server.

    - Ingres feature for advancement

# Kubernetes Architecture
    - Control Plane
    - Data Plane 

   **date  plane or worker plane**

   - In k8s, **kubeletes** are there creating the pod and for insuring that pod is always running and if it is down then use the auto-healing (using api-server).

   - In the docker we have **docker runtime** that is responsible for the running the container  that is called as **dockersim**
   But k8s supports  many interface as docker runtime such as dockersim ,cri-o 

   - **kube-proxy** that provides the networking to the pods for load distribution and things.
      
   **control plane**

   - The kube-apiserver exposes the Kubernetes API, which is used by all components and users to communicate with the cluster.
     It is request entry point 

     → authenticate
     → authorize (RBAC)
     → validate pod spec
     → store in etcd

   - Api=server takes all the information from user to create the pod on which node like that 
    
   - Schedular is used for pick the node for the pod it decide which node is best for it 

   - etcd storage is the backup key-pair store that store the entire k8s cluster information as objects.

   - Controller manager  , k8s provides many feature like auto-healing,auto-scaling so it has many controller (like replicaset)   for checking the information about this so k8s have controller mgr for managing the controller 

   - Cloud controller manager  , k8s is running on different cloud  ,  for different cloud the k8s setup an open source utility 
   called ccn that is used for writing logic for different cloud to run k8s 

# K8s Pod

   - Pod describes as  how to run a container 
   In the docker , we just run the docker by using cli as docker run -d -v -network  like that in the k8s we configure such things in the yaml  file 
   