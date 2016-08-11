#Scalene Case-2

###Use case: Move Applications to Cloud
Tomcat+MariaDB+HAProxy version of "Scalene Expense Manager" application available for deploying in Helion Openstack environment.

Requires 8 VMs: MariaDB Cluster (3 VMs) + DB Proxy (1 VM) + Application Cluster (3 VMs) + App Proxy (1 VM) 

Could be deployed in public cloud (connected to Internet) or private cloud (no Internet connection, requires pre-installed MasterVM to install all dependencies)

##Sub-projects

###Scalene Case-2
Branch name: ***master***

###Private cloud

Execute following steps from /case-2-private-cloud folder on MasterVM

1. Download and execute HOS api configuration script to use `nova`  
    ```
    source [HOS config script].sh
    ```
    
2. Configure cluster in the cluster-configuration.sh  

3. Run `source create-cluster.sh`
  
###Private cloud for pre-created cluster

Execute following steps from /case-2-private-cloud folder on MasterVM

1. Set up hosts configuration in `/etc/ansible/hosts`     

           [case2_haProxyDb]  
           10.0.0.80  
           
           [case2_dbMaster]  
           10.0.0.78  
           
           [case2_dbSlave]  
           10.0.0.79  
           10.0.0.8  
           
           [case2_app]  
           10.0.0.81  
           10.0.0.82  
           10.0.0.83  
           
           [case2_haProxyApp]  
           10.0.0.84    

2. Run `source deploy_to_pre_created.sh`
3. Set ssh key name after prompt.
4. Optional. Set path to the folder with compiled expenses.war file.
   By default it's `/home/out/case-2`
 
###Scalene MasterVM
Branch name: ***scalene-masterVM***
  
Master VM downloads all dependencies for cases 0-2, compiles application and sets up all the necessary environment variables. 

1. `sudo -s`
2. Upload ssh key. Save it's path, like:
    ```
    export CASE1_KEY_PATH=home/ubuntu/[ssh_key_name].pem
    chmod 400 $CASE1_KEY_PATH 
    ```
    
3. Run setup script `source ./setup-repository.sh`

***NOTE:***
Target instances should base on the same image as local repository for the packages compatibility.