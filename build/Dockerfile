FROM docker.io/dymurray/ansible-operator:status

COPY roles/ ${HOME}/roles/
COPY watches.yaml ${HOME}/watches.yaml
COPY library/ ${HOME}/library/
ENV ANSIBLE_LIBRARY=${HOME}/library/
