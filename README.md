# ansible-test

docker-compose -f docker-compose-sshd.yml build

docker-compose -f docker-compose-sshd.yml up -d

# Show servers

ansible test-servers --list-hosts

export ANSIBLE_PYTHON_INTERPRETER=/usr/bin/python3
export ansible_python_interpreter=/usr/bin/python3