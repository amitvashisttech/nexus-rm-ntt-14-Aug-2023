## Create an installation directory on your computer.  

### 1. Install Java JDK & Maven 
```
apt-get update; apt-get install openjdk-8-jdk maven -y 
```

### 2. Download URL ( https://help.sonatype.com/repomanager3/product-information/download/download-archives---repository-manager-3

### 3. Click the Link for Download according to your operating system. The packed/zipped file is downloaded to your computer.

### 4. You have now successfully created an installation directory and downloaded NXRM. Next, we will unpack the file and launch NXRM via the startup script.
```
tar -zxvf  nexus-*.tar.gz
```

### 5. Move the nexus data into /opt. 
```
mv nexus-3.51.1-03  /opt/nexus
```

### 6. Run the Nexus
```
nohup ./nexus run > /tmp/nexus.logs
```

### 7. Check logs for Nexus startup message. 
```
tail -f /tmp/nexus.logs 
```

### 8. Now go ahead & open nexus URL In your Fvt. brower: http://MachineIP:8081/ 
