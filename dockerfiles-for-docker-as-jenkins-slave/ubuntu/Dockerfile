FROM ubuntu:14.04
MAINTAINER Oded Priva <oded.priva@ironsrc.com>
EXPOSE 22
RUN apt-get update
RUN apt-get install -y openjdk-7-jre 
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN useradd -m -d /var/lib/jenkins jenkins
RUN echo 'jenkins:jenkins' | chpasswd

CMD ["/usr/sbin/sshd", "-D"]