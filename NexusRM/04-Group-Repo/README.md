## Create a Maven Group Repository

### 1. Next up, we’ll create a new Maven Group in the Nexus Repository Manager UI.

### 2. Open the Nexus Repository user interface.

### 3. Click Administration  in the top navigation menu.

### 4. Select Repositories.

### 5. Click Create repository.

### 6.  Choose the maven2 (group) recipe from the list.

### 7. Add the following text in the required fields:

### 8. Name: maven-all

### 9. In the member section add the following repos 
### - maven-release
### - maven-snapshots
### - maven-proxy-test

### 10. Click Create repository to complete the form.


# Now we need to update our settings.xml and point to newly created group repo: http://localhost:8081/repository/maven-all/

### 1. cd maven-test

### 2. mvn clean package 

### 3. Now you can go & check the group repo for snapshot data. 