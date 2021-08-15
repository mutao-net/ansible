FROM centos:centos7

# yum update
RUN yum -y update && yum -y install epel-release  wget  make

RUN yum -y install openssh-server openssh-clients
RUN sed -ri 's/^#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN echo "root:password" | chpasswd

RUN ssh-keygen -t rsa -N "" -f /etc/ssh/ssh_host_rsa_key

EXPOSE 22

## Python install
RUN yum install -y https://repo.ius.io/ius-release-el7.rpm

RUN yum install -y python36u python36u-libs python36u-devel python36u-pip

RUN yum install -y ansible

CMD /bin/bash