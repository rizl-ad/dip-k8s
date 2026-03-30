kube_prometheus
===============

This role deploys kube-prometheus (https://github.com/prometheus-operator/kube-prometheus) in a Kubernetes cluster, and configures the ingress controller and network rules for accessing Grafana.

Requirements
------------

Requires Ansible modules:
- kubernetes.core

Requires installed packages:
- kubernetes (python3-kubernetes)
- PyYAML (python3-yaml)

Role Variables
--------------

No variables.

Dependencies
------------

Ansible roles:
- k8s_nodes
- k8s_master
- k8s_worker
- calico
- ingress_nginx

Example Playbook
----------------

```yaml
- name: Play 1 name
  hosts: k8s_servers_group
  roles:
    - k8s_nodes

- name: Play 2 name
  hosts: master_nodes_group
  roles:
    - k8s_master
    - calico

- name: Play 3 name
  hosts: worker_nodes_group
  roles:
    - k8s_worker

- name: Play 4 name
  hosts: master_nodes_group
  roles:
    - ingress_nginx
    - kube_prometheus
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
