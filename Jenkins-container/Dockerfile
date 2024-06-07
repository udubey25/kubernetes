FROM jenkins/jenkins

USER root
#RUN yum install python
#RUN curl -O https://bootstrap.pypa.io/get-pip.py &&\
 #  python get-pip.py && \
  # pip install ansible --upgrade
RUN apt-get update && apt-get install -y ansible
RUN apt-get update -qq && apt-get install -qqy apt-transport-https ca-certificates curl gnupg2 software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
RUN apt-get update  -qq && apt-get -y install docker-ce
RUN groupmod -g 982 docker
RUN usermod -aG docker jenkins
#Setting up Kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
USER jenkins
