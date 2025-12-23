Authentication vs Authorization 

Authentication means with the  bank  example like it checks first you are identity that you are employee of the bank 
Authorization means with the bank example like it checks first you are identity that you are employee of the bank and you have the right to access the resource

# Authentication means the identity of the user is verified and the user is authorized to access the resource

So if the aws account have only the authentication and not the authorization then the user can access the resource without any restriction so the aws have it's own authentication mechanism called IOM

# IOM - Identity and Access Management (Authentication and Authorization)

when we create an  account in aws so it wants which service we want to acces so it will  give only that things to write and read and not the other things but we have the permission to read in other things

    1. users    - users simple
    2. groups   - we create group like developers,db,ops like that when the user signup we ask for group
                  and attach the policy according to that we dont need to create policy again and again
    3. roles    - see like if the aws is used like providing the db to the web whenever the user connect to 
                  web the aws want user for which aws req the user but not permanent user so we create roles that create temporary user.
    4. policies - what the user can do
    

# EC2 - Elastic Cloud Compute 

    asking the aws for the compute instance (cpu and memory) and the storage (disk) and the network
   # THAT IS VIRTUAL SERVER
    what it do it give the request to hypervisor and hypervisor provide the vm by alloacting a physical server that it has across the world
   # elastic means to inc or dec(Scaling) the resource while using it 
    public cloud is good bcz of maintainence and cost pay ans as go
    
   # Different type of instance
        1.general
        2.compute optimized
        3.memory
        4.storage
        5.accelerated  
    dependent upon the application

# VPC - Virtual Private Cloud

    vpc is like the network we have create a subnet like we did in the network  we have assign some ip range to that network  then different instance are created in that network let say host1 ,host2 and host2 
    if some one wants to access the host1  first they need to be verified at the internal gateway then reach the public subnet that is attachd to load balnacer and that elastic load balancer act as router that gives path to reach the host1 called (target group) and after that you reach the host1 then also  security group  isthere to protect the instance for what we have to pass

    VPC have the NAT (Network Address Translation)  that is the ip address of the instance is translated to the public ip address

    In VPC we create two subnet zone one for public and one for private 
    in public we add the load balancer and NAT and in private we add the instance
    The private server have the auto scaling 

#   Security Group anss NACL (the last point of security )
 
     Security group is the firewall that is attached to the instance and it is used to protect the instance from the attacks
     NCL is the firewall  that is attached to the subnet and it is used to protect the subnet from the attacks

     In  the AWS security is the shared responsibility.

    there are two things 
         1.inbound
         2.outbound
         
         Inbound means traffic comming to the instance
         Outbound means traffic going  from the instance
    for sg:

         by default the aws allows all the outbound ports except the port 25.
         but it deny  all the inbound ports 


    for nacl(network access control list):
        
        network  traffic what typw fo traffic we want to allow or deny and nacl layer is additional layer
        add rules for each and every instance by the nacl 


    1.Internet  Gateway 
    2.NACl
    3.Security Group
        
# ROUTER53

    router53 is used to give the domain name service 
    When a user sends a request to AWS, the request enters the VPC through the Internet Gateway. It then goes to Route 53, which handles the DNS resolution and translates the domain name into the IP address of the Load Balancer. The request is then routed to the Load Balancer (usually in a public subnet).  
    router53 also  check the health check by sending the req in certain time



# AWS S3 - Simple Storage Service

     S3 is a storage service that is used to store the data in the cloud
     the secret is success is the 11 9' number 

     -- Scalable , Availibilty , Secure and Cost Effective and Performance 
     S3 allows us to store the any data what we want to store 
     
     we can access the content using the https protocol

     The amazon provides 11 9 means 99.99999999999% relaibility it is because of the multiple replication of the data 
     1 billion in 100 year the data is deleted

     Advantages of S3
            1. Availability
            2. Scalability -- almost unlimited storage in bucket only restriction is that one object should not be more than 5tb
            3. Security    -- aws provides many policies like encryption , access control , data retention
            4. Cost-effectiveness -- 
            5. Performance
            6. it it version control we can keep the history of the data and retrieve the previous version of the dats 
               if it is disable then the file is replaced otherwise the new file is added to the existing file with the same name
                
# AWS CLI 

    AWS CLI is a command-line interface (CLI) tool that allows you to interact with AWS services from the command line. It provides a unified interface to manage AWS resources, such as EC2 instances, S3 buckets, and RDS databases.

    AWS prvides api  for the cli for the automate the process of the aws services 

        1. AWS CLI
        2. CDK
        3. Terraform
        4. CloudFormation

    AWS_CLI 
        it is python based utility that is used to interact with the aws services
        it act as middle-man and it changes the command to the aws-ap   

# AWS CFT
  
    AWS CloudFormation is a powerful and flexible tool for creating and managing AWS infrastructure and resources. It allows you to define your AWS resources as code, making it easier to provision and manage your infrastructure.
    It is based on Infracture as Code (IaC) and declerative (what you see is what you do)
     AWS CLI is when some quick and short action
     AWS CFT is when you want to create a complex infrastructure    

     continue .....


# AWS CICD 

    AWS CODE COMMIT is a service that allows you to commit code to a Git repository and automatically deploy it to an Amazon EC2 instance or a container in Amazon Elastic Container Service (Amazon ECS) or an Amazon Elastic Kubernetes Service (Amazon EKS) cluster. it is version control system

    Managed Git
    Scalability 
    Reliability
    
    It has less feature
    aws restricted 

    AWS code pipeline   when the aws code commit is triggered the aws code pipeline (similar to jenkins) and the build step is processing with different stages like unit test , static code analysis  .. 
    Now aws code pipleline takes the responsibility of the continus integration and delivery (CI/CD) and it is the one that is responsible for the deployment of the code to the production environment


# AWS CODE COMMIT

   AWS Code Commit is a service that allows you to commit code to a Git repository and automatically deploy it to an Amazon EC2 instance or a container in Amazon Elastic Container Service (Amazon ECS) or an Amazon Elastic Kubernetes Service (Amazon EKS) cluster.

   It is version control system 
   it is managed git
   it is scalable  
   it is reliable  

# AWS CODE PIPELINE

   AWS code pipeline   when the aws code commit is triggered the aws code pipeline (similar to jenkins) and the build step is processing with different stages like unit test , static code analysis  ..

   Now aws code pipleline takes the responsibility of the continus integration and delivery (CI/CD) and it is the one that is responsible for the deployment of the code to the production environment
   
   # aws code pipeline is invoking the ci  and cd  but the jenkins integrate the ci and invoke the cd 
     it is using the aws code build the ci part is done where we have different stages like unit test , static code analysis  ..


   then the aws code deploy takes the cd part where it deploy it using kubernetes or ecs

   we have to take the aws-code-pipeline bcz of managing issue bcz of jenkins we have to manage the node and all the other part so we can use the aws-code-commit and pipeline 

   other part is that during the docker build the node is automatically removed after the build or other thing is done
   jenkins is open source and it is not restricted to anything  we can integrate many tools to it .


# ECR - elastic container registry

    ECR is a managed Docker registry service that makes it easy to store, manage, and deploy Docker container images.

    -- Dockerhub is free to use and we can use the public repository and private repository 

    -- ECR supports only the private repository , iam are directly integrated with the ECR so with ecr we dont need  to create the user and all these , directly the image are accessed ...

# ECS - Elastic Container Service

    the prblm with the docker is that 
        1. auto - healing -> it means that if the container is deleted then the container is not self healed again
        2. auto - scaling

    - COE - cluster orchestration environment

    - Kubernetes is there to solve the problem of auto-healing and auto-scaling

    - aws is comming with their  own container orchestration service and it is only restricted to aws and its service it is disadv bcz of hybrid cloud

    - the main prblm is that k8s is open source and have many feature but that is not go with the ecs like CRD , istio 

    - ECS we dont have to maintain anything and it provide Forget ECS that means it is complete serverless model  so we dont need to manage anything so it is easy to use

    - K8s is complex to use 

    - ECS is easy to use


# SECRET MANAGEMENT

    - System Manager
      - it has parameter store and ssm to store the secrets .   
      - it is easy to store as iam have access to the system manager .

    - Secret Manager
      - it provide more security then system manager
      - it has rotate  that means we can expire the secret in a particular time .
      - it is expensive to use
    - Hashicorp Vault
      - hashicorp vault is a centralized service that we can implement with different cloud based service like aws and azure
      - it is dedicated to the secret management

# Load Balancer 

    - Load Balancer is the service that is used to manage the incoming request and distribute the request to the Servers 

    - the basic load balancer is round robin technique

    - we have different types of load balancer like nginx , traffic , apache etc 

    - Depending upon the different layer of the osi model we have different load balancer
        1. ALB for application layer
            in this we have different target server like
                1. for amazon.com we have main server 
                2. for amazon.com/login  request to the target server that is handling the login 

            all these things are done by the application load balancer we called it alb
            In this , http header is used to route the request to the target server    by load balancer 

            -- it is costly and slow 

        2. NLB for Transport layer
           in this we the decesion is made at the l4 level  by the load balancer
           ex:- gaming server,streaming server so it decides the frame has to be sent to the server or not
        
          -- it is fast  and have low latency
        
        3. GWLB - Gateway Load Balance ( for network layer )
            it is more used in the case of firewalls 


