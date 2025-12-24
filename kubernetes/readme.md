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

    - K8s  have the controlm and fix the damage so whenever the container is going down k8s start(roll down) the container immedaitely or even it by api-server.

    - Ingres feature for advancement

# Kubernetes Architecture
    - Control Plane
    - Data Plane 

    




