FROM xebialabsunsupported/xl-docker-demo-jenkins:2.190-alpine
MAINTAINER 'Vincent Lussenburg "vlussenburg@xebialabs.com"'

ARG xld_password
ARG xlr_password
ARG jenkins_password
ARG DOCKER_USER
ARG DOCKER_PASS

ENV xld_password=${xld_password}
ENV xlr_password=${xlr_password}
ENV jenkins_password=${jenkins_password}
ENV DOCKER_USER=${DOCKER_USER}
ENV DOCKER_PASS=${DOCKER_PASS}

COPY ./jenkins.yaml /var/jenkins_home/casc_configs/jenkins.yaml

USER root
RUN apk --no-cache add docker openrc shadow
RUN rc-update add docker boot
RUN usermod -aG docker jenkins

# Get docker-compose
RUN curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose


USER jenkins