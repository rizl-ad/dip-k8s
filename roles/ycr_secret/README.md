ycr_secret
==========

This role creates a secret for accessing the Yandex Cloud image registry.

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
| `app_namespace` | "{{ lookup('env', 'APP_NAMESPACE') }}" | The name of the namespace into which applications should be deployed. |
| `sa_key_file_path` | "{{ lookup('env', 'YC_INFRA_SA_KEY_FILE_PATH') }}" | Path to the file containing the Yandex Cloud service account key |

Dependencies
------------

Ansible roles:
- k8s_nodes
- k8s_master
- k8s_worker
- helm
- calico
- gha_arc

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
    - helm
    - calico

- name: Play 3 name
  hosts: worker_nodes_group
  roles:
    - k8s_worker

- name: Play 4 name
  hosts: master_nodes_group
  roles:
    - gha_arc
    - ycr_secret
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
