helm
====

This role install the Helm.

Requirements
------------

No requirements

Role Variables
--------------

| variable | default value | description |
| -------- | ------------- | ----------- |
| `helm_deb_repo_url` | `"https://packages.buildkite.com/helm-linux/helm-debian/any/ any main"` | Link to the Helm repository for systems using a package manager to work with .deb files |
| `helm_deb_gpg_key_url` | `"https://packages.buildkite.com/helm-linux/helm-debian/gpgkey"` | Link to the Helm repository gpg-key for systems using a package manager to work with .deb files |

Dependencies
------------

No dependencies

Example Playbook
----------------

```yaml
- name: Play name
  hosts: master_nodes_gruop
  roles:
    - helm
```

License
-------

MIT

Author Information
------------------

Yaroslav Lysenko (rizl)
