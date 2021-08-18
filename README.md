# docker-dxp-es-cluster
DXP cluster + ES cluster samples

### Usage
Use docker to start these projects.
1. mysql-compose
1. elasticsearch654 ( 2 services )
1. Liferay71 (2 services )

### Memos:
 - Set all services in same docker v-network (name : mysql-compose_default)
 - Use docker's command to check v-network's status
    ```
     docker network ls
     docker network inspect ${network name}
    ```
 - Change network address for services.
     - elasticsearch654/es/config/elasticsearch.yml
     - elasticsearch654/es2/config/elasticsearch.yml
     - Liferay71/lr/liferay/files/tomcat/webapps/ROOT/WEB-INF/classes/ehcache/tcp.xml
     - Liferay71/lr2/liferay/files/tomcat/webapps/ROOT/WEB-INF/classes/ehcache/tcp.xml
     - Liferay71/docker-compose.yml
    -  Liferay71/lr/liferay/files/portal-ext.properties
     - Liferay71/lr2/liferay/files/portal-ext.properties
 - In case liferay's docker image can't find the jdbc driver, need this jar file.
    Liferay71/lr/liferay/files/tomcat/lib/ext/mysql-connector-java-8.0.21.jar
    Liferay71/lr2/liferay/files/tomcat/lib/ext/mysql-connector-java-8.0.21.jar
 - In case change the services jvm configs, need change this config file.
    Liferay71/lr/liferay/files/tomcat/bin/setenv.sh
    Liferay71/lr2/liferay/files/tomcat/bin/setenv.sh
 - use command to check elastic search cluster's status
    ```
    curl -X GET "[ESサーバのIP]:9200/_cat/nodes?v"
    ```
 - If DXP cluster is set-up successfuly, these message can be find in log.
    ```
    Accepted view [{service'sID} | 1] (2)
    ```
    ```
    properties: UDP                             //in case using UDP multi-cast
    ```
    ```
    properties: TCP                             // in case using TCP unicast
    ```
