### This repository contains WSO2 ESB 4.9.0 Worker/manager separated clustering deployment pattern with Docker compose ###

![alt tag](https://docs.wso2.com/download/attachments/47525837/ClusterESB.png)

#### How to run
 
 ``` docker login dockerhub.private.wso2.com ```
 
 ```docker-compose up```

This will deploy the following,

* Mysql server (container) with esbdb
* SVN server (container) and create svn repo
* ESB-Manager runs on a container
* ESB-Worker runs on a container and clustred with ESB-Manager node
* Nginx Load Balancer container and add ESB enpoints

#### How to test

Add the following entries to the /etc/hosts
```
127.0.0.1 mgt.esb.wso2.org
127.0.0.1 esb.wso2.org
```
If you are using docker machine, please use the docker machine IP instead of the local machine IP.

#### How to access the environment

ESB Management console

```
https://mgt.esb.wso2.org/carbon
```

