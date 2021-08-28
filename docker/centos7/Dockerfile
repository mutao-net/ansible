FROM centos:centos7

RUN yum -y install openssh-server
RUN sed -ri 's/^#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN echo "root:password" | chpasswd

RUN ssh-keygen -t rsa -N "" -f /etc/ssh/ssh_host_rsa_key

EXPOSE 22

# yum update
RUN yum -y update && yum -y install epel-release  wget  make sudo glibc


## Python install
RUN yum install -y https://repo.ius.io/ius-release-el7.rpm

RUN yum install -y python36u python36u-libs python36u-devel python36u-pip

RUN yum install -y ansible

RUN touch ~/.vimrc && echo "set encoding=utf-8" > ~/.vimrc

CMD ["/usr/sbin/sshd", "-D"]