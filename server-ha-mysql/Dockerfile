FROM rxvallejoc/java:8
MAINTAINER Rodrigo Vallejo <rxvallejoc@gmail.com>

RUN apk add --no-cache \
      curl=7.49.1-r0 \
      heimdal-telnet=1.6_rc2-r4 \
      iputils=20121221-r3 \
      lsof=4.89-r0 \
      strace=4.11-r2 \
      tar=1.29-r0 \
      unzip=6.0-r1 \
      wget=1.18-r0

RUN addgroup keycloak -g 1000 && adduser -u 1000 -G keycloak -D keycloak

WORKDIR /home/keycloak

USER keycloak

ENV KEYCLOAK_VERSION 2.0.0.Final

ENV LAUNCH_JBOSS_IN_BACKGROUND 1

RUN cd /home/keycloak/ && curl -L https://downloads.jboss.org/keycloak/$KEYCLOAK_VERSION/keycloak-$KEYCLOAK_VERSION.tar.gz | tar zx && mv /home/keycloak/keycloak-$KEYCLOAK_VERSION /home/keycloak/keycloak

RUN mkdir -p /home/keycloak/keycloak/modules/system/layers/base/com/mysql/jdbc/main; cd /home/keycloak/keycloak/modules/system/layers/base/com/mysql/jdbc/main && curl -O http://central.maven.org/maven2/mysql/mysql-connector-java/5.1.18/mysql-connector-java-5.1.18.jar
ADD module.xml /home/keycloak/keycloak/modules/system/layers/base/com/mysql/jdbc/main/

ADD docker-entrypoint.sh /home/keycloak/

ADD standalone-ha.xml /home/keycloak/keycloak/standalone/configuration/

USER root

RUN chown keycloak:keycloak /home/keycloak/docker-entrypoint.sh \
  && chown keycloak:keycloak /home/keycloak/keycloak/standalone/configuration/standalone-ha.xml \
  && chmod 755 /home/keycloak/docker-entrypoint.sh

USER keycloak

ENV JBOSS_HOME /home/keycloak/keycloak

EXPOSE 8080

ENTRYPOINT [ "/home/keycloak/docker-entrypoint.sh" ]

CMD ["-b", "0.0.0.0", "--server-config", "standalone-ha.xml"]
