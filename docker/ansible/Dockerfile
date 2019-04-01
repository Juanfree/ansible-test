FROM ubuntu:18.10

RUN apt-get update \
    && apt-get install ansible iputils-ping ssh sudo vim -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN ln -sf /usr/bin/python3 /usr/bin/python

RUN adduser --quiet --shell /bin/bash --home /home/ansible --gecos "User" ansible

RUN echo "ansible:ansible" | chpasswd

ADD docker/ansible/rootfs /

ENTRYPOINT ["bash", "/opt/ansible/entrypoint.sh"]
