# CentOS7
FROM centos:7

# install ssh server
RUN yum -y install openssh-server && yum clean all
RUN yum -y sudo

# create Public key
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa
RUN ssh-keygen -A

# set to login as root
RUN sed -ri 's/^#PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config

# set a password for root
RUN echo "root:" | chpasswd

# expose 22 port
EXPOSE 22

# start up sshd
CMD ["/usr/sbin/sshd", "-D"]