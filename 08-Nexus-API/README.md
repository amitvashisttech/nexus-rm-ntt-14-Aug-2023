
# Explore Nexus API

## Step 1: Login with Admin User

## Step 2: Go to Settings Tab -> System -> API -> You Will API Groups -> Click any of them & test. 

## Step 3: Check avalivable Repos
```
 curl -u admin:redhat -X GET http://192.168.68.130:8081/service/rest/v1/repositories
```

### Step 4: Check avalivable Repos Settings 
```
curl -u admin:redhat -X GET http://192.168.68.130:8081/service/rest/v1/repositorySettings
```

### Step 5: Create a new nexus repo 
```
 curl -u admin:redhat -X 'POST'   'http://192.168.68.130:8081/service/rest/v1/repositories/maven/hosted'   -H 'accept: application/json'   -H 'Content-Type: application/json'   -H 'NX-ANTI-CSRF-TOKEN: 0.733172098784374'   -H 'X-Nexus-UI: true'   -d @hosted-repo.json
```

### Step 6: Check LDAP Settings
```
curl -u admin:redhat -X GET http://192.168.68.130:8081/service/rest/v1/security/ldap
```