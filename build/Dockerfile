FROM docker.io/djzager/ansible-operator:status-flag

COPY roles/ ${HOME}/roles/
COPY watches.yaml ${HOME}/watches.yaml
COPY library/ ${HOME}/library/
ENV ANSIBLE_LIBRARY=${HOME}/library/
