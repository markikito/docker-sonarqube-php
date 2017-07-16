FROM sonarqube:6.4-alpine

MAINTAINER Kaj Nelissen

ENV SONARQUBE_HOME /opt/sonarqube
ENV SONAR_PLUGIN_HOME $SONARQUBE_HOME/extensions/plugins

RUN apk add --update curl && \
    rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/bin/curl"]

RUN set -x && curl -o ${SONAR_PLUGIN_HOME}/sonar-php-plugin-2.8.jar -fSL http://sonarsource.bintray.com/Distribution/sonar-php-plugin/sonar-php-plugin-2.8.jar
RUN set -x && curl -o ${SONAR_PLUGIN_HOME}/sonar-javascript-plugin-2.12.jar -fSL http://sonarsource.bintray.com/Distribution/sonar-javascript-plugin/sonar-javascript-plugin-2.12.jar
