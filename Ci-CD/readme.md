what is cicd
     -cicd is the continuos integration and continuos deployment
     -it is the process of automating the build, test, and deployment of software applications
     
     -it means the application is goes to the user with the testing ,build and  deploy it is process to automate all that
    
     Unit testing
     Static code analysis
     Code Quality
     Automation 
     Reports
     Deployment

     Unit testing - the testing of the unit of the code
                  - it is the testing of the smallest unit of the code
    
     Static code analysis - the analysis of the code without running it tp verify the code

     Code Quality - the security of the code to test the code security
     
     Automation - functional testing

     Reports - the report of the test

     Deployment - the deployment of the code where the user can access the code
     
     Jenkins is do it we say to him whenever the prgm commit something just check and i have to perform some steps to it
     jenkins act as middle man or pipeline and is used to automate all the steps which are we talk above
     jenkins pipeline are used to do all  the testing automate and allow us to specify the testing 

     Jenkins Deployment have 3 steps
         1. Development
         2. Staging
         3. Production

    At the deployment stage , the code is first deploted to the development environment where env is small and clean
    Then the code is deployed to the staging environment where env is somehow big and replica of live env  and  then the code is ready to be deployed to the production environment 
    In the dev deployment the test is automated and in the stage the test are manual
    the prod phase is just last live environment.

    Jenkins is the legacy tool it is still  used but it is not scale up  for that it is no  prefered tool  

    Jenkins architecture
        1. Master -- we do the only scheduling in this node 
        2. Worker -- we do the work in this node 

        We choose master-worker architecture bcz of the lib conflicting in the master node and heavy load in the master node as there are many jobs and many teams running in the master node 
        The problem is that if we lets say we have 5 workers and 1 master then the workers remaian idle if the request not come from the master node so we have better approach than the master-worker architecture

        Instead of  master-worker architecture we have docker architecture in that we have one master node having docker and we can make different node as container as we need instantly.


# AWS-Cloud Watch

    it is service that watch the activity of aws    
     1. monitoring
     2. alerting
     3. reporting 
     4. logging
     5. real-life matrix - it tells how much api my instance receive cpu utilization of my instance
     6. alarms - it gives the alarms on cpu utilization of my instance  
     7. custom metrics - the cw by default monitor the cpu utilization but not eh memory utilization that  can be done using the custom metrics.
     8. cost optimization - cloud watch is used for cloud optimization (lambda)
    