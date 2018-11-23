# FROM jenkins/jenkins:latest
FROM jenkins
USER root
RUN apt-get update && apt-get install -y sudo && rm -rf /var/lib/apt/lists/* 
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers
USER jenkins

RUN /usr/local/bin/install-plugins.sh git mstest matrix-auth workflow-aggregator docker-workflow blueocean credentials-binding

ENV JENKINS_USER admin
ENV JENKINS_PASS 6YHN7ujm8ik,

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/
