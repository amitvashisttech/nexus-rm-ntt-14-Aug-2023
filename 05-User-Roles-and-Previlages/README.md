## Testing User, Roles & privileges

## Create Custom privileges

### 1. Login to Nexus UI with admin user. 

### 2. Go to Settings Tab -> Select -> privileges -> Create Previlage -> Type -> Repository View [Custom-Repo-Viewer-Prev ] 

Name  :  Custom-Repo-Viewer-Prev 
Desc  :  Custom-Repo-Viewer-Prev 
Format:  maven2 
Repo  :  maven-proxy-test
Action:  browse,read

### 3. Go to Settings Tab -> Select -> privileges -> Create Previlage -> Type -> Repository View [Custom-Repo-Edit-Prev ]

Name  :  Custom-Repo-Edit-Prev 
Desc  :  Custom-Repo-Edit-Prev 
Format:  maven2 
Repo  :  maven-proxy-test
Action:  browse,read,edit

### 4. Go to Settings Tab -> Select -> privileges -> Create Previlage -> Type -> Repository Admin [Custom-Repo-Admin ]

Name  :  Custom-Repo-Admin  
Desc  :  Custom-Repo-Admin 
Format:  maven2 
Repo  :  (All Repositories)
Action:  *


## Now we need to create respective roles & assign privileges to them. 

### 1. Go to Settings Tab -> Select -> Roles -> Create Roles -> Type -> Nexus role -> [Custom-Repo-Viewer-Role]

Role ID    : Custom-Repo-Viewer-Role
Role Name  : Custom-Repo-Viewer-Role
Role Desc  : Custom-Repo-Viewer-Role
Privileges : Custom-Repo-Viewer-Prev 

### 2. Go to Settings Tab -> Select -> Roles -> Create Roles -> Type -> Nexus role -> [Custom-Repo-Edit-Role]

Role ID    : Custom-Repo-Edit-Role
Role Name  : Custom-Repo-Edit-Role
Role Desc  : Custom-Repo-Edit-Role
Privileges : Custom-Repo-Edit-Prev 

### 3. Go to Settings Tab -> Select -> Roles -> Create Roles -> Type -> Nexus role -> [Custom-Repo-Admin-Role]

Role ID    : Custom-Repo-Admin-Role
Role Name  : Custom-Repo-Admin-Role
Role Desc  : Custom-Repo-Admin-Role
Privileges : Custom-Repo-Admin-Prev 


## Now we need to create respective Users & assign respective Roles to them. 

### 1. Go to Settings Tab -> Select -> User -> Create local User -> Nexus role -> [Custom-Repo-Viewer-User]

ID         : viewer
First Name : Custom
Last  Name : Viewer
Email  ID  : viewer@localhost
Password   : redhat
Status     : Active
Roles      : Custom-Repo-Viewer-Role

### 2. Go to Settings Tab -> Select -> User -> Create local User -> Nexus role -> [Custom-Repo-Edit-User]

ID         : editor
First Name : Custom
Last  Name : editor
Email  ID  : editor@localhost
Password   : redhat
Status     : Active
Roles      : Custom-Repo-Edit-Role

### 3. Go to Settings Tab -> Select -> User -> Create local User -> Nexus role -> [Custom-Repo-Admin-User]

ID         : repoadmin
First Name : Custom
Last  Name : repoadmin
Email  ID  : repoadmin@localhost
Password   : redhat
Status     : Active
Roles      : Custom-Repo-Admin-Role


## Login with each user & verify their privilages & roles. 