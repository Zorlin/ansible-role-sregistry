# Ansible Role: sregistry (Singularity Registry Server)

Installs and configures [Singularity Registry Server](https://github.com/singularityhub/sregistry).

## Requirements

Before this role runs, you need to make sure the following role dependencies are installed:

| Dependency                    | Suggested Role           |
| ----------------------------- | ------------------------ |
| EPEL repo (RedHat OSes only)  | `geerlingguy.repo-epel`  |
| Git                           | `geerlingguy.git`        |
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
    - geerlingguy.docker
    - zorlin.sregistry
```

## License

MIT

## Author Information

This role was created in 2020 by Benjamin Arntzen.

This role uses examples and code from [geerlingguy.awx](https://github.com/geerlingguy/ansible-role-awx) which was written by Jeff Geerling and is available under the MIT license.

This role uses examples and code from [grycap.singularity-registry](https://github.com/grycap/ansible-role-singularity-registry) which was written by Sergio López Huguet / Grid y Computación de Altas Prestaciones and is available under the Apache 2.0 License.
