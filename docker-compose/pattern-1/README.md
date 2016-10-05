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
## How to run in Docker Swarm Cluster

### Setup Docker Swarm Cluster in Amazon AWS

https://beta.docker.com/docs/aws/

### Deploy on Swarm

Change docker-compose-swarm.yml image names according to your docker private registry or public registry.

eg. If you have a docker public registry account (say account name is "lakwarus"), you can change images as following

```
docker.wso2.com/swarm-esb-pattern1-mysql:5.5			-> lakwarus/swarm-esb-pattern1-mysql:5.5
docker.wso2.com/swarm-esb-pattern1-esb-analytics:5.0.0		-> lakwarus/swarm-esb-pattern1-esb-analytics:5.0.0
docker.wso2.com/swarm-esb-pattern1-esb-manager:5.0.0		-> lakwarus/swarm-esb-pattern1-esb-manager:5.0.0
docker.wso2.com/swarm-esb-pattern1-esb-worker:5.0.0		-> lakwarus/swarm-esb-pattern1-esb-worker:5.0.0
```
To build all docker images
```
docker-compose -f docker-compose-swarm.yml build
```

To push newly built images to relevant docker registry
```
docker-compose -f docker-compose-swarm.yml push
```

To create bundle file

```
docker-compose -f docker-compose-swarm.yml bundle
```

Copy pattern2.dab file to docker swarm manager node and run following

To deploy all docker services on swarm cluster
```
docker deploy pattern1
```
To update AWS ELB endpoits
```
docker service update --publish-add 9444:9444 pattern2_esb-analytics
docker service update --publish-add 9443:9443 pattern2_esb-namaner
docker service update --publish-add 8243:8243 pattern2_esb-worker
docker service update --publish-add 8280:8280 pattern2_esb-worker
```
#### How to access the environment
Update your DNS (or add host entries) by poining "esb-manager","esb-worker" and "esb-analytics" domain names to AWS ELB IP.  


```
https://esb-manager/carbon
```

```
https://esb-worker/
```

ESB Analytics
```
https://esb-analytics:9444/carbon/
```
