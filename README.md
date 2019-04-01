# Receiver container

docker-compose -f docker-compose.receiver.yml build

docker-compose -f docker-compose.receiver.yml up -d

# Show servers

ansible receiver --list-hosts

export ANSIBLE_PYTHON_INTERPRETER=/usr/bin/python3
export ansible_python_interpreter=/usr/bin/python3

# Run receiver container

docker-compose -f docker-compose.receiver.yml up -d

# Commands
ansible all -m ping -u ansible -e ansible_python_interpreter=/usr/bin/python

ansible all -m setup -u ansible -e ansible_python_interpreter=/usr/bin/python

ansible all -b -m apt -a "name=ntp state=present" -u ansible -e ansible_python_interpreter=/usr/bin/python


# Install nginx 
ansible all -b -m apt -a "name=nginx state=present" -u ansible -e ansible_python_interpreter=/usr/bin/python

# Remove nginx
ansible all -b -m apt -a "name=nginx state=absent" -u ansible -e ansible_python_interpreter=/usr/bin/python

ansible all -b -a "service nginx status" -u ansible -e ansible_python_interpreter=/usr/bin/python
ansible all -b -a "service nginx start" -u ansible -e ansible_python_interpreter=/usr/bin/python
ansible all -b -a "service nginx stop" -u ansible -e ansible_python_interpreter=/usr/bin/python
ansible all -b -a "service nginx status" -u ansible -e ansible_python_interpreter=/usr/bin/python

# Modules

## Information about files

ansible receiver -m stat -a "path=/etc/hosts" -u ansible -e ansible_python_interpreter=/usr/bin/python
ansible receiver -b -m stat -a "path=/etc/hosts" -u ansible -e ansible_python_interpreter=/usr/bin/python

ansible receiver -b -m copy -a "src=/etc/hosts dest=/tmp/hosts" -u ansible -e ansible_python_interpreter=/usr/bin/python

ansible receiver -m stat -a "path=/tmp/hosts" -u ansible -e ansible_python_interpreter=/usr/bin/python

ansible receiver -m fetch -a "src=/etc/hosts dest=/tmp" -u ansible -e ansible_python_interpreter=/usr/bin/python

## Crons
ansible all -b -m apt -a "name=cron state=present" -u ansible -e ansible_python_interpreter=/usr/bin/python
ansible receiver -b -m cron -a "name='first cron' hour=4 job='script.sh'" -u ansible -e ansible_python_interpreter=/usr/bin/python
