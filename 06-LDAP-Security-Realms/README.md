Step 1. Install the LDAP Packages for Relam Auth.   
```
apt -y install slapd ldap-utils
```

Step 2. Check your DN ( cn=admin,dc=example,dc=com)
```
 slapcat
```

## Step 3: Craete the base.ldif for inital OU in LDAP. 
```
 cat base.ldif
```
```
dn: ou=people,dc=example,dc=com
objectClass: organizationalUnit
ou: people


dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups
```

## Step 4. Add Base.ldif Record in Ldap :
```
ldapadd -x -D cn=admin,dc=example,dc=com -W -f base.ldif 
```


## Step 5. Install Apache WebServer & PHP: 
```
apt -y install apache2 php php-cgi libapache2-mod-php php-mbstring php-common php-pear
```
```
a2enconf php7.4-cgi
systemctl reload apache2 
```

## Step 6. Install LDAP Account Manager:
```
apt -y install ldap-account-manager
systemctl restart apache2 
```

## Step 7. Configure LDAP Account Manager:

URL : http://MachineIPAddress/lam

LAM - Ldap Accout Manager 

## Default UserName : Manager & Password : lam 

Change the password : redhat@123

--> Go to Genral Setting -> Server Profile -> Use Old Password -> Server Setting : 
 -> Tree Suffix : dc=example,dc=com 
 
 
Security settings
--> List of Valid User:  cn=admin,dc=example,dc=com
  
--> Go to Accout Type [TAB]
  -> Active account types - Users  - LDAP Suffix ->  [ou=People,dc=example,dc=com]
  -> Active account types - Groups - LDAP Suffix ->  [ou=group,dc=example,dc=com]

-> Save



## Now Login Back with Admin Cred -> Create Group -> Click on Group TAB -> 
New Group Name : developer

## Now create user & add them in developer group: User TAB -> New User 

-> Name          : 
-> LastName      : test1
-> Type          : Unix 
-> UserID        : 10000
-> Primary Group : Developer

## Now Click on set password -> Configure your user password -> Save. 


# Let's configure Nexus for LDAP Realm Authentication 
## --> Go to Nexus -> Setting -> LDAP -> Create Connection 
   -> Name : LDAP LOCAL Connection
   -> ldap ://master.example.com: 389
   -> BaseDN : dc=example,dc=com
   -> Auth Methord: Simple Authentication
   -> User DN : cn=admin,dc=example,dc=com
   -> Verify Connection
   
##   -> Next TAB -> User & Group -> Posix Static Group -> Keep All the Settings as Default -> Verify user mapping: 
   
## -> Now try to login with newly created Ldap user to -> Nexus.   

