FROM rxvallejoc/java:8
MAINTAINER Rodrigo Vallejo <rxvallejoc@gmail.com>

RUN addgroup keycloak -g 1000 && adduser -u 1000 -G keycloak -D keycloak 

WORKDIR /home/keycloak

USER keycloak
