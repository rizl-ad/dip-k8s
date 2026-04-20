argocd
======

This role installs ArgoCD into the Kubernetes cluster, creates a namespase for ArgoCD, sets an administrative password, removes the temporary password, creates an application to connect to the GitHub repository, and configures the ingress controller.

Requirements
------------

Requires Ansible modules:
- kubernetes.core

Requires installed packages:
- passlib (python3-passlib)
- kubernetes (python3-kubernetes)
- PyYAML (python3-yaml)

Role Variables
--------------

| variable | default value | description |
| -------- | ------------- | ----------- |
| `argocd_app_name` | `"{{ lookup('env', 'APP_NAME') }}"` | Name of the deployed application. |
| `argocd_app_namespace` | `"{{ lookup('env', 'APP_NAMESPACE') }}"` | The name of the namespace into which applications should be deployed. |
| `argocd_admin_password` | `"{{ lookup('env', 'ARGOCD_ADMIN_PASSWORD') }}"` | ArgoCD administrative password |
| `argocd_namespace` | `argocd` | The name of the namespace into which all ArgoCD components will be installed. |
| `github_repo_url` | `"{{ lookup('env', 'GITHUB_REPO_URL') }}"` | The URL of the GitHub repository that ArgoCD will track changes to. |
| `guthub_target` | `"{{ lookup('env', 'GUTHUB_TARGET') }}"` | Path to the directory with helm charts. |
| `argocd_sa_key_file_path` | `"{{ lookup('env', 'YC_INFRA_SA_KEY_FILE_PATH') }}"` | Path to the file containing the Yandex Cloud service account key |

Dependencies
------------

Ansible roles:
- k8s_nodes
- k8s_master
- k8s_worker
- calico

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
    - argocd
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
