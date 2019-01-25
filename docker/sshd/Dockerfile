FROM rastasheep/ubuntu-sshd:18.04

RUN apt-get update \
    && apt-get install -y sudo vim \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN adduser --quiet --disabled-password --shell /bin/bash --home /home/ansible --gecos "User" ansible

RUN echo "ansible:ansible" | chpasswd

ADD docker/sshd/rootfs /

ADD docker/shared/ssh/id_rsa.pub /home/ansible/.ssh/authorized_keys

RUN chown ansible:ansible /home/ansible/.ssh/authorized_keys
