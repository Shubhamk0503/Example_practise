FROM jenkins/jenkins:lts

USER root
RUN apt-get update \
      && apt-get install -y sudo curl\
      && apt-get install -y ansible\
      && apt-get install -y libltdl7\
      && rm -rf /var/lib/apt/lists/*
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN curl -sSL -o /bin/docker https://get.docker.io/builds/Linux/x86_64/docker-latest
RUN chmod +x /bin/docker

USER jenkins

# Job
COPY jobs/Assignment-config.xml /var/jenkins_home/jobs/Assignment/config.xml

#Jenkins Configuration
COPY config/config.xml /var/jenkins_home/config.xml
COPY config/credentials.xml  /var/jenkins_home/credentials.xml
