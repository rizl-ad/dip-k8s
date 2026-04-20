calico
======

This role is designed to install the Calico CNI plugin for a self-managed Kubernetes cluster.

Requirements
------------

Requires Ansible modules:
- kubernetes.core

Requires installed packages:
- kubernetes (python3-kubernetes)
- PyYAML (python3-yaml)

Role Variables
--------------

| variable | default value | description |
| -------- | ------------- | ----------- |
| `calico_version` | `"3.31.3"` | Installable version of Calico |
| `calico_operator_crds_url` | `"https://raw.githubusercontent.com/projectcalico/calico/v{{ calico_version }}/manifests/operator-crds.yaml"` | A link to the operator-crds.yaml manifest, which registers the object types (CRDs) required for Tigera Operator to run in Kubernetes and ensures validation of Calico configurations. |
| `calico_tigera_operator_url` | `"https://raw.githubusercontent.com/projectcalico/calico/v{{ calico_version }}/manifests/tigera-operator.yaml"` | Link to the Tigera operator manifest manifest |
| `calico_custom_resources_url` | `"https://raw.githubusercontent.com/projectcalico/calico/v{{ calico_version }}/manifests/custom-resources.yaml"` | Link to custom resource definitions |
| `calico_pod_network_cidr` | `"192.168.0.0/16"` | This is the range of IP addresses (in CIDR format) from which internal addresses will be allocated for each Pod. |
| `calico_encapsulation` | `"VXLAN"` | The encapsulation parameter determines how traffic is transmitted between cluster nodes. It controls whether the network packet will be wrapped in an additional header to pass through the existing network. |

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
    - calico
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
