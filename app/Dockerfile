FROM jenkins/jenkins:lts-jdk17

# No utilizar en un ambiente de producción
ENV JENKINS_USER=admin
ENV JENKINS_PASS=admin
ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false

USER root
RUN apt-get update && apt-get install -y docker.io python3 python3-pip python3-django pylint && apt-get clean

USER jenkins