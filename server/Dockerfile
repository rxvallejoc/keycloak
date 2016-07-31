FROM rxvallejoc/java:8
MAINTAINER Rodrigo Vallejo <rxvallejoc@gmail.com>

RUN addgroup keycloak -g 1000 && useradd -u 1000 -r -g keycloak -m -d /opt/keycloak -s /sbin/nologin -c "Keycloak user" keycloak && \
    chmod 755 /opt/keycloak

WORKDIR /opt/keycloak

USER keycloak

