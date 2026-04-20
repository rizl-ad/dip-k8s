k8s_nodes
=========

This role prepares the host for joining a Kubernetes cluster. It installs the necessary packages and core Kubernetes components.

Requirements
------------

No requirements.

Role Variables
--------------

| variable | default value | description |
| -------- | ------------- | ----------- |
| `k8s_nodes_version` | `"{{ lookup('env', 'K8S_VERSION') }}"` | Installable version of kubelet, kubeadm, kubectl |
| `k8s_nodes_deb_baseurl` | `"https://pkgs.k8s.io/core:/stable:/v{{ k8s_nodes_version }}/deb/"` | Link to the k8s repository for systems using a package manager to work with .deb files |
| `k8s_nodes_deb_gpg_key_url` | `"https://pkgs.k8s.io/core:/stable:/v{{ k8s_nodes_version }}/deb/Release.key"` | Link to the k8s repository gpg-key for systems using a package manager to work with .deb files |
| `k8s_nodes_rpm_baseurl` | `"https://pkgs.k8s.io/core:/stable:/v{{ k8s_nodes_version }}/rpm/"` | Link to the k8s repository for systems using a package manager to work with .rpm files |
| `k8s_nodes_rpm_gpg_key_url` | `"https://pkgs.k8s.io/core:/stable:/v{{ k8s_nodes_version }}/rpm/repodata/repomd.xml.key"` | Link to the k8s repository gpg-key for systems using a package manager to work with .rpm files |

Dependencies
------------

No dependencies.

Example Playbook
----------------

```yaml
- name: Play name
  hosts: k8s_servers_group
  roles:
    - k8s_nodes
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
