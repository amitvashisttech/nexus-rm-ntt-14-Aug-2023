### Login to Jenkins 

### Install Nexus Plugin 
-> Go to Manage Jenkins -> Manage Plugins -> Select ( Avaliable Plugins ) -> Search (Nexus Platform) -> Install.  



### Config Nexus with Jenkins
-> Go to Manage Jenkins -> System -> Sonatype Nexus 

-> Select : Nexus-3.x Server
-> Display Name : NEXUS-3-LATEST
-> Server ID    : releases 
-> Server URL   : http://192.168.68.130:8081/
-> Add Cred     : Nexus-Admin-Cred. ( username & password )


### Create a FireStyle Job 
-> Go to Admin Page  -> + New Item -> FreeStyleNexusJob -> Freestyle Project

-> SCM : Git 
-> Repo URL : https://github.com/amitvashisttech/nexus-rm-ntt-14-Aug-2023.git
-> Repo Branch: */main

-> Build Steps: 
   --> Execute Shell:
    -> cd 03-SnapShots-and-Release-Repo
    -> mvn clean ; mvn package

    --> Add Build Step -> Nexus Repo Manager Publisher 
       -> Nexus Instance : NEXUS-3-LATEST
       -> Nexus Repository : releases
       -> Tag              : empty

    ---------> Maven Package
            -> Group : com.example
            -> Artifact : nexus-proxy
            -> Version  : 1.0
            -> Packaging : jar

    --------------> Artifacts
                 -> File Path: 03-SnapShots-and-Release-Repo/target/nexus-proxy-1.0-SNAPSHOT.jar

    --> Save. 


-> Build Now.     