### ESB clustred deployment ###

![alt tag](https://docs.wso2.com/download/attachments/47525837/ClusterESB.png)

Following instructions will help you to setup the deployment

 Execute 
 
 ``` docker login dockerhub.private.wso2.com ```
 
 ```docker-compose up```

This will setup 

* Mysql server (container) with esbdb
* SVN server (container) and create svn repo
* ESB-Manager runs on a container
* ESB-Worker runs on a container and clustred with ESB-Manager node
* Nginx Load Balancer container and add ESB enpoints

