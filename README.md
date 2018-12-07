# Bitcoin Ansible Operator

Bitcoin Ansible Operator deploys a containerized [Bitcoin
SV](https://github.com/bitcoin-sv/bitcoin-sv) `bitcoind` application on
Kubernetes using Ansible playbooks via the [Ansible
Operator](https://github.com/water-hole/ansible-operator)

## Quickstart

1. Start [minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) (e.g. `minikube start`)

    We will be using the `default` namespace, and the `default` account.

1. Deploy the Bitcoin operator

    * Create the Bitcoin operator RBAC and Service Account files
        ```bash
        $ kubectl create -f deploy/service_account.yaml
        $ kubectl create -f deploy/role.yaml
        $ kubectl create -f deploy/role_binding.yaml
        ```

    * Create the Bitcoin operator Custom Resource Definitions (CRD)
        ```bash
        kubectl create -f deploy/crds/bitcoin_v1_bitd_crd.yaml
        ```
    * Deploy the etcd operator
        ```bash
        kubectl create -f deploy/operator.yaml
        ```

1. Create the Vault Ansible Operator Custom Resource (CR)

    ```bash
    kubectl create -f deploy/crds/bitcoin_v1_bitd_cr.yaml
    ```

## Uninstall

To uninstall the Bitd Deployment and the Bitcoin Ansible Operator, run the following commands

1. Uninstall Bitd
    ```bash
    kubectl delete -f deploy/crds/bitcoin_v1_bitd_cr.yaml
    ```
1. Uninstall Bitcoin Ansible Operator
    ```bash
    kubectl delete -f deploy/operator.yaml
    ```

Verify that the all pods created with the deployment are being `terminated` and are deleted
