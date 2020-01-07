FROM centos:7

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT 07-01-2020_11:00_UTC

RUN yum update -y && \
    yum install -y openssh-server initscripts ansible sudo && \
    /usr/sbin/sshd-keygen && \
    useradd -d /home/ansible -s /bin/bash -c "Ansible user" ansible && \
    mkdir -p /home/ansible/.ssh && \
    echo "ansible ALL=NOPASSWD: ALL" >> /etc/sudoers

ADD ansible_keys.tar /home/ansible/.ssh/

RUN chown -R ansible:ansible /home/ansible && \
    chmod 700 /home/ansible/.ssh 

USER ansible

WORKDIR /home/ansible

CMD [ "sudo", "/usr/sbin/sshd", "-D" ]
