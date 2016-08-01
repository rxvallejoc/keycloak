FROM rxvallejoc/java:8
MAINTAINER Rodrigo Vallejo <rxvallejoc@gmail.com>

RUN addgroup keycloak -g 1000 && adduser -u 1000 -G keycloak -h /opt/keycloak -D keycloak && \
    chmod 755 /opt/keycloak

WORKDIR /opt/keycloak

USER keycloak
