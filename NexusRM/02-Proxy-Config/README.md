## Create a Maven Proxy Repository

### 1. Next up, we’ll create a new Maven proxy in the Nexus Repository Manager UI.

### 2. Open the Nexus Repository user interface.

### 3. Click Administration  in the top navigation menu.

### 4. Select Repositories.

### 5. Click Create repository.

### 6.  Choose the maven2 (proxy) recipe from the list.

### 7. Add the following text in the required fields:

### 8. Name: maven-proxy-test

### 9. Remote storage URL: https://repo1.maven.org/maven2

### 10. Click Create repository to complete the form.



## Now we need to create a maven project. 

### 1. Create a Dir : mkdir -p /root/maven-test

### 2. cd /root/maven-test

### 3. cp -rf /root/nexus-rm-ntt-14-Aug-2023/02-Proxy-Config/pom.xml 

### 4. mkdir ~/.m2

### 5. cp -rf /root/nexus-rm-ntt-14-Aug-2023/02-Proxy-Config/settings.xml ~/.m2/

### 6. mvn clean package 

### 7. Go to Nexus URL -> Browes proxy repo for data caching.  