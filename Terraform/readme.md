## Welcome to the Taraform 

    --The main idea is that to write the intrastructure  as code (IaC)

    - AWS has cloudFormation  Template as the tool for Iac 
    - Azure has Resource Manager Template as the tool for Iac

    Now why Taraform ? 
        
        universal tool for Iac 
        we dont have to require to learn different Iac tool for different cloud provider
        we can use the same tool for all cloud provider

-Now we have to maintain a main.tf file  to configure the tarraform that is know writing the code for the aws not for azure as the 
tarraform is a universal  tool not for specific one

# Provider 
    the first thing is the provider then the region

    1. multiregion setup of the terraform
    2. hybrid version of the terraform

    
#           Multiregion setup of the terraform

                -- we have to add alias after the region setup in the provider section 
                -- add the alias name in the provider in the resource file . 
    
#           Hybrid version of the terraform

                --we can provide configure of different provider section of the file and then use it 

# Variables

    Two types of variables
        - Input variables
        - Output variables

## Module  

     - module is a way to reuse the same code in the terraform
     so we have microservices architecture as the bug is very difficult to maintain in the single file 

     we create module (directory) and make the complete terraform init and then we just call the module in the main.tf file

# Terraform State

    - state are the heart of the terraform  and store the record of infrastructure 
    - state file are created these file to store the instance and everything that we created in the terraform
    So, the benefit of the state file is that when we have to modify something in that case terraform dont create 
     another  file instead of it just update the already created one 
     
    - Second one terraform cache the information of init in that file (created and create)...
     
    - In case of destroy command it just destroy the inf it created from the statefile and then it delete the state file

    - Drawbacks of the state file
       - Statefile contain the sensitive information so it should be encrypted
       - It can be misconfigured as in the team it will stored in the version control system so wveryone can change it remotely then it can cause the problem

#   Remote Backend 
    
    - it means store the state file in s3 bucket 

    It will solve the two prblm 
        1. Sensitive information - we can restrict the access by the iam role
        2. Version control - whenever someone apply terraform apply the file is directly changes ..
    
    