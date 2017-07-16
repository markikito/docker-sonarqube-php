FROM sonarqube:6.4-alpine

MAINTAINER Kaj Nelissen

ENV SONARQUBE_HOME /opt/sonarqube
ENV SONAR_PLUGIN_HOME $SONARQUBE_HOME/extensions/plugins

RUN apk add --update curl && \
    rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/bin/curl"]

RUN set -x && curl -o ${SONAR_PLUGIN_HOME}/sonar-php-plugin-2.8.jar -fSL http://sonarsource.bintray.com/Distribution/sonar-php-plugin/sonar-php-plugin-2.8.jar
RUN set -x && curl -o ${SONAR_PLUGIN_HOME}/sonar-javascript-plugin-2.12.jar -fSL http://sonarsource.bintray.com/Distribution/sonar-javascript-plugin/sonar-javascript-plugin-2.12.jar

RUN curl --insecure -o ./sonarscanner.zip -L https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.0.3.778-linux.zip
RUN unzip sonarscanner.zip
RUN rm sonarscanner.zip

ENV SONAR_RUNNER_HOME=/root/sonar-scanner-3.0.3.778-linux
ENV PATH $PATH:/root/sonar-scanner-3.0.3.778-linux/bin

#   ensure Sonar uses the provided Java for musl instead of a borked glibc one
RUN sed -i 's/use_embedded_jre=true/use_embedded_jre=false/g' /root/sonar-scanner-3.0.3.778-linux/bin/sonar-scanner

# Use bash if you want to run the environment from inside the shell, otherwise use the command that actually runs the underlying stuff
#CMD /bin/bash
#CMD sonar-scanner -Dsonar.projectBaseDir=./src