FROM ubuntu:22.04

# Install Ansible and dependencies
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    apt-add-repository --yes --update ppa:ansible/ansible && \
    apt-get install -y ansible ssh curl iputils-ping && \
    apt-get clean

CMD [ "sleep", "infinity" ]
