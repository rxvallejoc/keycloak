Comandos para levantar Keycloak con mysql 

Despliega Mysql
docker run --name mysql -e MYSQL_DATABASE=keycloak -e MYSQL_USER=keycloak -e MYSQL_PASSWORD=password -e MYSQL_ROOT_PASSWORD=root_password -d mysql

Despliega Keycloak
docker run --name keycloak --link mysql:mysql -p 8080:8080 -e MYSQL_DATABASE=keycloak -e MYSQL_USER=keycloak -e MYSQL_PASSWORD=password rxvallejoc/keycloak:2.0.0.Final-mysql

docker exec keycloak keycloak/bin/add-user-keycloak.sh -u admin -p admin
docker restart keycloak

docker exec -it keycloak /bin/bash
docker exec -it mysql /bin/bash

