# Docker is a container platform 
  - it is platform to make , run and manage the container

# Kubernetes is a container orchestration platform
  - the container are ephemeral means the life of the container are very short

  1. Single User 
     - the problem is that lets say we have 100 container and we want to run the container in the same time and one container is crashed bcz of resource are used by other container so the linux have to  kill the container acc to its policy so it create 
     prblm bcz of **Single User**  ( Single host - the container are impacting one another)

  2. Killed container
     - if the container is killed bcz of some reason then in the docker the container will not auto restart (suto healing) 
     so we have kubernetes for tha **Auto Healing**

  3. Auto Scaling
     - we required the load balanceer to balance the load the docker dont have that thing so we have to use kubernetes

  4. Simple 
     - it doesn't have the enterprise support  like load-balancerr , internet-gateway , firewalls ,load-balancer etc 


# Kubernetes 

  - In general k8s is a cluster - grp of nodes and master node 

  - In the cluster if anyone cause prblm then the k8s move that pod to other node and then it will be fixed

  - k8s have the concept of **ReplicaSet** so when configure the yaml file and say whenever the load is inc replica the current node to distribute the load .

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

   - So the pod is like container or grp  of container that have the same configuration as in the docker in the yaml  file not on the cli 

   - We can have many container in the pod and have benefit like shared volume , shared network , shared storage etc
   
   - Pod is just a wrapper around the container and it is responsible for the life cycle of the container

# Kubectl 
   
   - Kubectl is the command line tool for kubernetes

   - It is used for managing the cluster and the container

   - It is used for creating the pod , deployment , service , configmap etc

   - **VM -> single node k8s cluster**  (minikube) 

# DEMO

   - just add pod.yml to configure all the things like container , volume , network etc
   
   - kubectl create -f pod.yml

   - kubectl get pod 
      
      - kubectl get pod -o wide
     
   just go the cluster of minikube as minikube ssh then try to connect with the ip  

   - Auto - healing and Auto - scaling 
     
# Debug 

  - kubectl logs pod_name it is used for getting the logs of the pod

  - kubectl describe pod pod_name it is used for getting the information about the pod    

# Deployment
     
  - we create pod that dont have the capablilty of auto  healing and auto-scaling
   
  - we have to use deployment for that it is just a wrapper around the pod

  - when we create the deployment it will first create the replica-set that is the controller for insuring the desired state is always on the actual state then it will create the pods as per the replica-set 

  - it is just abstraction for the pod,replica-set.

  - it is auto healing with replica-set even if i kill the pod bcz of some reason it will create the new pod and it will be runnin  

# K8s Service

  - the prblm is that with the deployment we can have the auto-healing but the new pod can be created with the **new ip address** that this is the issue ..
  
  - to solve this we have the **load balancer** but in the k8s we have the service whoch act as the load balancer 

  - we can access the application using the name or ip of svc 

  - the prblm is that now the service have to mannually configure the ip if the new pod arise with the new ip to solve this service is mapping the pod with the labels and selector not with the ip so the new pod is created with the same **label and selector** so it will be mapped with the service

  - service is also  exposing the application outside the k8s cluster 
          1. clusterIP  - inside the cluster.
          2. nodePort -   inside the organization ( can access that are in the node)  it is working on ip of the minikube          
          3. loadBalancer - exposing the world.


  1. load service.
  2. service discovery.
  3. exposing the service to the world.

  - for conversion from nodeport to  load-balancer we simple change the nodeport to loadbalancer and by kubectl edit svc and responsiliblity is taken by the cloud control mgr .

# K8s  Ingress

  1. we have the service that is providing a lot of functionality like load-balancer and other things but there are other  things 
    but a lot of things are missing like 100 , waf ,tls which are not available in the lagacy k8s 

  2. for load-balancer , we have to provide different public ip for different service so the companies have to pay for that to cloud provider

  - to solve these problem k8s has the ingress 

  - so we have the ingress resource on k8s and this will allow to connect to the ingress controller that will created by the different load-balancer like nginx or traefik etc to implement their load - balancer on the cluster of k8s
     
  - so we hv to create the 
     1. ingress - it just the **configuration** of what the load-balancer hv to do  
     2. ingress controller - it is the **actual engine** or logic behind the ingress to enforce it .

     Ingress never talk  to  the nodeport but it is only use for domain name routing 


# K8s Secret and  ConfigMap

   -  for the info like db_port , db_name or other things that we hv to keep secret we have to use the secret we use env in the application but in the k8s we hv to use configmap to store the info as **mount or env** to the container for access that information (the info is stored in **etc** as obj)

   - secret also solve the same problem as the configmap but the secret is **encrypted** and then stored in the etcd
    he configmap is not.

   - it deals with the **sensitive info**  

   if we are using the env the data is not **dyanmaically changeable** so we hv to use volume mount(cm)


# K8s  RBAC (Role Based Access Control)

  - RBAC is the authorization for the k8s
  - In the team we hv to have the different role like admin , user , developer and hving deifferent permission for them .
  - we hv to give the permission to the user to do the operation like create pod , create deployment etc .

  we hv three things in rbac 
    1. Service Account / User
    2. Role / ClusterRole
    3. RoleBinding / ClusterRoleBinding
  
  **User**

      Kubernetes handles **authorization using RBAC**, but user **creation and authentication** are handled by an external Identity Provider. 
        - Kubernetes = AuthZ (RBAC)
        - External IdP = AuthN (User creation, login, identity proof)
  
  **Service Account**

    - Service account can be created using yaml file
    - K8s created when k8s start to interact with the api-server so it is the identity of the pods to interact with the pods  and the api-server..

  **Role and RoleBinding**

    - Role is the set of permissions that can be granted to a user or a group of users .
    - Through RoleBinding , role is attaching to the different swtich account and user .

       Role  ->  RoleBinding -> Switch Account

    - If the role is creating with specific namespace then it is called role
    - if the role is creating within the specific cluster then it is called clusterrole


# K8s Monitoring 

  - Prometheus is an open-source monitoring and alerting system used to collect, store, query, and alert on metrics, especially in cloud-native and Kubernetes environments.
  - Grafana is an open-source visualization tool for time series data.

  **Prometheus**
     - **Prometheus server** is used to interact with k8s api-server and get the metrics which are exposed by the k8s api-server
     - The metrics are stored in the **TSDB**(Time Series Database)
     - **Alert Mgr** is used to get the alerts from the TSDB and send the alert to the email or slack
     - **Prometheus server** is used to get the metrics from the TSDB and store the metrics in the **TSDB**
     - **PromQL** it is used to query the metrics from the TSDB
    
  **Grafana**
     - Grafana is used to visualize the metrics from the TSDb   

# K8s Custom Resource
  - Custom Resource Definition (CRD) is a way to extend the Kubernetes API with Custom Resources.

  - extend the api of the k8s with the custom resource
  
  - There are three rsources in the k8s to handle the custom resource
     1. Custom Resource Definition (CRD)
     2. Custom Resource (CR)
     3. Custom Controller

  **Custom Resource Definition (CRD)**
    - defining a type of api  to the k8s and to validate the yaml  
    - it is yaml file that hv all the custom resource that is supported by the new resource otherwise k8s shows the error
      in the yaml whoever try to use new customm resource 
    -  In the native k8s the yaml  file is validating using the **resource defination** while in the custom resource it is validating using the CRD
   
   **Custom Resource (CR)**
     - it is the actual resource that is created by the user
     - it is yaml file that hv the actual resource that is created by the user
     - the CRD is validating the yaml file and then it is creating the actual resource
 
   **Custom Controller**
      - it is the controller that is responsible for the actual resource
      