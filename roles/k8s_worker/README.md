k8s_worker
==========

This role joins worker nodes to a Kubernetes cluster.

Requirements
------------

Requires installed packages:
- container
- kubelet
- kubeadm
- kubectl

Role Variables
--------------

No variables.

Dependencies
------------

Ansible roles:
- k8s_nodes
- k8s_master

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

- name: Play 3 name
  hosts: worker_nodes_group
  roles:
    - k8s_worker
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
