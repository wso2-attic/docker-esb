### This repository contains WSO2 ESB 5.0.0 Worker/manager separated clustering deployment pattern with Docker compose ###

![alt tag](https://github.com/wso2-support/deployment-patterns/blob/master/wso2esb/5.0.0/design/esb-5.0-pattern-1.png)

#### How to run
 
 ``` docker login docker.wso2.com ```
 
 ```docker-compose pull```
 
 ```docker-compose build```
 
 ```docker-compose up```

This will deploy the following,

* Mysql server (container) with esbdb
* SVN server (container) and create svn repo
* ESB-Manager runs on a container
* ESB-Workers runs on containers and clustred with ESB-Manager node
* ESB Analytics runs on a container
* Nginx Load Balancer container and add ESB enpoints

#### How to test

Add the following entries to the /etc/hosts
```
127.0.0.1 mgt.esb.wso2.org
127.0.0.1 esb.wso2.org
127.0.0.1 mgt.esb-analytics.wso2.org
```
If you are using docker machine, please use the docker machine IP instead of the local machine IP.

#### How to access the environment

ESB Management console

```
https://mgt.esb.wso2.org/carbon
```

ESB Analytics Management console

```
https://mgt.esb-analytics.wso2.org:9444/carbon
```
