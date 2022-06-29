ARG JENKINS_VERSION=lts-jdk11
FROM jenkins/jenkins:${JENKINS_VERSION}
COPY docker_files/jenkins-log.properties /etc/jenkins-log.properties
USER root
RUN apt-get update && apt-get install -y \
       ca-certificates curl gnupg2 \
       software-properties-common && \
    mkdir -p /data1/jenkins /var/cache/jenkins/war && chown -R jenkins:jenkins /data1/jenkins /var/cache/jenkins

USER jenkins
ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false -Duser.home=/data1/jenkins -Djenkins.model.Jenkins.slaveAgentPort=50000 -Djava.util.logging.config.file=/etc/jenkins-log.properties" \
    JENKINS_HOME="/data1/jenkins" \
    JENKINS_OPTS="--webroot=/var/cache/jenkins/war --httpPort=8081" \
    JENKINS_SLAVE_AGENT_PORT="50000"

EXPOSE 8081

RUN jenkins-plugin-cli --latest false --plugins " \
ansicolor:1.0.1 \
ant:1.11 \
antisamy-markup-formatter:2.1 \
"