# Setup EC2

## Install stuff

```bash
#!/bin/bash
sudo su -
# install jdk
sudo amazon-linux-extras install java-openjdk11 -y

# change directory to opt
cd /opt

# install tomcat
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.83/bin/apache-tomcat-9.0.83.tar.gz

# extract compressed tomcat file
tar -xvzf apache-tomcat-9.0.83.tar.gz

# rename it for rememberable name
mv apache-tomcat-9.0.83 tomcat

ln -s /opt/tomcat/bin/startup.sh /usr/local/bin/tomcatup
```

## Modify role

- Add

```xml
<role rolename="admin-gui"/>

<role rolename="manager-gui"/>

<role rolename="manager-script"/>

<role rolename="manager-jmx"/>

<role rolename="manager-status"/>

<user username="admin" password="s3cret" roles="admin-gui,manager-gui, manager-script, manager-jmx, manager-status"/>
```

to
`tomcat/conf/tomcat-users.xml`

- Remove `<Value>` on `tomcat/webapps/manager/META-INF/context.xml`

- Run tomcat: `tomcatup`
