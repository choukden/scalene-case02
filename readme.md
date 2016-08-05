##Case-2

###Public cloud
/case-2

###Private cloud
/case-2-private-cloud

1. Download and execute api configuration script  
    `source Hewlett-Packard0517-openrc.sh`  

2. Configure cluster in the cluster-configuration.sh  

3. `source create-cluster.sh`
  
###Private cloud for pre-created cluster
/case-2-private-cloud  

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

2. `source deploy_to_pre_created.sh`
3. Set ssh key name after prompt.
4. Optional. Set path to the folder with compiled expenses.war file.  
   By default it's `/home/out/case-2`
 