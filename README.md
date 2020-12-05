# Ansible Role: sregistry (Singularity Registry Server)

Installs and configures [Singularity Registry Server](https://github.com/singularityhub/sregistry).

## Requirements

Before this role runs, you need to make sure the following role dependencies are installed:

| Dependency                    | Suggested Role           |
| ----------------------------- | ------------------------ |
| EPEL repo (RedHat OSes only)  | `geerlingguy.repo-epel`  |
| Git                           | `geerlingguy.git`        |
| Ansible                       | `geerlingguy.ansible`    |
| Docker                        | `geerlingguy.docker`     |
| Python Pip                    | `geerlingguy.pip`        |

See this role's [`molecule/default/converge.yml`](molecule/default/converge.yml) playbook for an example that works across many different OSes.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    NOT YET IMPLEMENTED

## Dependencies

None.

## Example Playbook

```yaml
- hosts: sregistry-centos
  become: true

  vars:
    docker_install_compose: false
    pip_install_packages:
      - name: docker
      - name: docker-compose

  roles:
    - geerlingguy.repo-epel
    - geerlingguy.git
    - geerlingguy.pip
    - geerlingguy.ansible
    - geerlingguy.docker
    - zorlin.sregistry
```

## License

MIT

## Author Information

This role was created in 2020 by Benjamin Arntzen.
