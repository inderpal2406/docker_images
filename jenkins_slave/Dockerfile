FROM centos:7

ENV REFRESHED_AT 21-12-2019_11:27_UTC

# run command to install openssh server
RUN yum update -y && \
    yum install -y openssh-server initscripts

# user add in container image and configure it
RUN useradd -c "Remote user to ssh to run jenkins jobs" -d /home/remote_user -s /bin/bash remote_user && \
    echo "Corp@123" | passwd remote_user --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 home/remote_user/.ssh

# copy public key generated on local docker host to authorized keys inside image
COPY remote_user_key.pub /home/remote_user/.ssh/authorized_keys

# change ownership and permissions of .ssh and authorized_keys
RUN chown -R remote_user:remote_user /home/remote_user/.ssh/ && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

# generate ssh global keys, commented below line as it gives errors during build. It works fine without below command.
RUN /usr/sbin/sshd-keygen

# install mysql client
RUN yum install -y mysql

# install aws cli using pip
# RUN yum install -y python2.7 && \   # commented because centos already has python 2.7 installed in it
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py && \
    pip install awscli

# set command to run sshd service in foreground during runtime of docker container
CMD /usr/sbin/sshd -D
