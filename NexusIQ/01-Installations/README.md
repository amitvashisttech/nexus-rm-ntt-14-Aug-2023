# Nexus IQ Installation 

### Pre-request: 
-> RAM : 8 GB 
-> CPU : 4 CPU

### Step 0: Update the VM Configuration, in case using vagrant the please update the vagratfile for the same. 
```
-> Open the cmder
-> cd devops-lab/vagrant-setup/devops
-> ls 
```
```
-> vim Vagrantfile
```
```
Update the following: 
v.memory = 8096
v.cpu    = 4 
```
```
vagrant up master
```

### Step 1. Install Java JDK & Maven 
```
apt-get update; apt-get install openjdk-8-jdk maven -y 
```

### 2. Download URL ( https://help.sonatype.com/iqserver/product-information/download-and-compatibility ) 

### 3. Click the Link for Download according to your operating system. The packed/zipped file is downloaded to your computer.
```
wget https://download.sonatype.com/clm/server/latest.tar.gz 
```

### 4. Create a directory where you want to install IQ.
```
mkdir -p /opt/nexus-iq-server
mv /root/latest.tar.gz /opt/nexus-iq-server
```

### 5. Extract the achive 
```
cd /opt/nexus-iq-server
tar -zxvf latest.tar.gz
```

### 6. Run the NexusIQ
```
sh demo.sh 
```

### 7. Wait for IQ Server to listen or bind on [0.0.0.0:8070] message on your screen. 

### 8. Log in to the IQ Server 
```
-> In chrome open the url : http://172.31.0.100:8070
-> Enter Defualt username (admin) & password (admin123)
```

### 9. Install the License. 
