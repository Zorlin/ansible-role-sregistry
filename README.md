# Ansible Role: sregistry (Singularity Registry Server)

Installs and configures [Singularity Registry Server](https://github.com/singularityhub/sregistry).

This role is in heavy development right now and not super ready for use.

Right now it only supports the GitHub OAuth2 methods, the rest aren't implemented.

## Requirements

Before this role runs, you need to make sure the following role dependencies are installed:

| Dependency                    | Suggested Role           |
| ----------------------------- | ------------------------ |
| EPEL repo (RedHat OSes only)  | `geerlingguy.repo-epel`  |
| Git                           | `geerlingguy.git`        |
| Docker                        | `geerlingguy.docker`     |
| Python Pip                    | `geerlingguy.pip`        |
| Nginx                         | `geerlingguy.nginx`      |

See this role's [`molecule/default/converge.yml`](molecule/default/converge.yml) playbook for an example that works across many different OSes.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    NOT YET DOCUMENTED

## Dependencies

You will need docker-compose and the "docker" python library installed on your control machine.

An easy way to install them is using pip3:

```
pip3 install docker
pip3 install docker-compose
```

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
    - geerlingguy.nginx
    - zorlin.sregistry
```

## License

MIT

## Author Information

This role was created in 2020 by Benjamin Arntzen.

This role uses examples and code from [geerlingguy.awx](https://github.com/geerlingguy/ansible-role-awx) which was written by Jeff Geerling and is available under the MIT license.

This role uses examples and code from [grycap.singularity-registry](https://github.com/grycap/ansible-role-singularity-registry) which was written by Sergio López Huguet / Grid y Computación de Altas Prestaciones and is available under the Apache 2.0 License.

## TODOs

In no particular order:

* Actually bring things up using https://docs.ansible.com/ansible/latest/collections/community/general/docker_service_module.html
* Add options for providing your own SSL certs or using certbot/generation
* Add options for providing your own database details
* Add options for configuring domain stuff
* Add options for setting Minio secrets
* Add options for providing your own Minio service
* Add optional install and configuration of "mc" tool
* Properly add support for all available OAuth providers
* Add configuration options for as much as reasonably possible
* Nginx - setup the outage pages
* Nginx - make outage pages use HTTPS if available
* Add GitHub Actions + add docker-compose and "docker" pip module to host

Actual playbooks are out of scope for now, but an "official" playbook repo should come later. So, TODOs for that:

* Playbook to take down the Docker images for maintenance and bring up nginx
* Playbook to generate certificates with Let's Encrypt (certbot certonly w/ nginx plugin)
* Playbook to renew LE certificates
