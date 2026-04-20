ingress_nginx
=============

This role install the Ingress-Nginx controller via Helm.

Requirements
------------

Requires Ansible modules:
- kubernetes.core

Requires installed packages:
- helm
- kubernetes (python3-kubernetes)
- PyYAML (python3-yaml)

Role Variables
--------------

| variable | default value | description |
| -------- | ------------- | ----------- |
| `ingress_nginx_apiserver_advertise_address` | `"{{ apiserver_advertise_address }}"` | The IP address specified in the `--apiserver-advertise-address` parameter when initializing the Kubernetes cluster, or the IP address of the VIP of the Kubernetes cluster control-plane, or the IP address of the master-node of the Kubernetes cluster |
| `ingress_nginx_http_node_port` | `"{{ http_node_port }}"` | Port number for a NodePort type service in the range 30000–32767 |

Dependencies
------------

Ansible roles:
- k8s_nodes
- k8s_master
- k8s_worker
- calico
- helm

Example Playbook
----------------

```yaml
- name: Play 1 name
  hosts: k8s_servers_group
  roles:
    - k8s_nodes

- name: Play 2 name
  hosts: master_nodes_gruop
  roles:
    - k8s_master
    - calico
    - helm

- name: Play 3 name
  hosts: worker_nodes_gruop
  roles:
    - k8s_worker

- name: Play 4 name
  hosts: master_nodes_gruop
  roles:
    - ingress_nginx
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
