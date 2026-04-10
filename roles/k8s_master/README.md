k8s_master
==========

This role initializes the Kubernetes cluster and join additional master-nodes to the cluster.

Requirements
------------

Requires installed packages:
- container
- kubelet
- kubeadm
- kubectl

Role Variables
--------------

| variable | default value | description |
| -------- | ------------- | ----------- |
| `k8s_master_apiserver_advertise_address` | "{{ apiserver_advertise_address }}" | The IP address or hostname specified in the `--apiserver-advertise-address` parameter when initializing the Kubernetes cluster |
| `k8s_master_pod_network_cidr` | "192.168.0.0/16" | This is the range of IP addresses (in CIDR format) from which internal addresses will be allocated for each Pod. |
| `k8s_master_apiserver_cert_extra_sans` | "{{ apiserver_cert_extra_sans }}" | The IP address or hostname specified in the `--apiserver_cert_extra_sans` parameter when initializing the Kubernetes cluster |
| `k8s_master_control_plane_endpoint` | "{{ control_plane_endpoint }}" | The IP address or hostname specified in the `--control_plane_endpoint` parameter when initializing the Kubernetes cluster |

Dependencies
------------

Ansible roles:
- k8s_nodes

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
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
