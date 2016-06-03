from dockerhub.private.wso2.com/wso2esb:4.9.0

#RUN rm -fr /mnt/wso2/carbon-home/repository/deployment/server/*
COPY artifacts/mysql-connector-java-5.1.34-bin.jar /mnt/wso2/carbon-home/repository/components/lib/
COPY artifacts/svnkit-all-1.8.7.wso2v1.jar /mnt/wso2/carbon-home/repository/components/dropins/
COPY artifacts/trilead-ssh2-1.0.0-build215.jar /mnt/wso2/carbon-home/repository/components/lib/
COPY esb-worker/axis2.xml /mnt/wso2/carbon-home/repository/conf/axis2/
COPY esb-worker/registry.xml /mnt/wso2/carbon-home/repository/conf/
COPY esb-worker/carbon.xml /mnt/wso2/carbon-home/repository/conf/
COPY esb-worker/master-datasources.xml /mnt/wso2/carbon-home/repository/conf/datasources/
COPY esb-worker/wso2server.sh /mnt/wso2/carbon-home/bin/
