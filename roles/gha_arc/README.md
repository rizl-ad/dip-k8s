gha_arc
=======

This role installs the GiHub ARC controller and scalable runner set in the Kubernetes cluster, assigns permissions to manage ephemeral pods, and assigns permissions to deploy applications.

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
| `app_namespace` | "{{ lookup('env', 'APP_NAMESPACE') }}" | The name of the namespace into which applications should be deployed. |
| `gha_arc_namespace` | gha-arc-system | The name of the namespace in which the ARC controller is installed. |
| `gha_arc_secret_name` | gha-arc-secret | The name of the secret associated with the GitHub App |
| `gha_runner_set_name` | gha-arc-runner-set | Runner Scale Set name for GitHub Actions |
| `github_config_url` |  | The URL of the GitHub entity (repository, organization or enterprise) to which your self-hosted runners will be linked. This defines the scope of the runner set. |
| `gha_arc_deploer_role_name` | gha-arc-runner-deploer-role | The name of the role assigned to the GitHub ARC service account for deploying applications. |
| `github_app_id` | "{{ lookup('env', 'APP_ID') }}" | Unique identifier of your GitHub App |
| `github_app_installation_id` | "{{ lookup('env', 'APP_INSTALLATION_ID') }}" | This is the ID of a specific installation of the application per account, organization, or repository. |
| `github_app_private_key` | "{{ lookup('env', 'APP_PRIVATE_KEY') }}" | This is the content of your GitHub App private key. |

Dependencies
------------

Ansible roles:
- k8s_nodes
- k8s_master
- k8s_worker
- helm
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
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
