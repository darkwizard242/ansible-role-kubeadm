[![build-test](https://github.com/darkwizard242/ansible-role-kubeadm/workflows/build-and-test/badge.svg?branch=master)](https://github.com/darkwizard242/ansible-role-kubeadm/actions?query=workflow%3Abuild-and-test) [![release](https://github.com/darkwizard242/ansible-role-kubeadm/workflows/release/badge.svg)](https://github.com/darkwizard242/ansible-role-kubeadm/actions?query=workflow%3Arelease) ![Ansible Role](https://img.shields.io/ansible/role/d/darkwizard242/kubeadm) [![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-kubeadm&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=ansible-role-kubeadm) [![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-kubeadm&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=ansible-role-kubeadm) [![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-kubeadm&metric=security_rating)](https://sonarcloud.io/dashboard?id=ansible-role-kubeadm) ![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/darkwizard242/ansible-role-kubeadm?label=release) ![GitHub repo size](https://img.shields.io/github/repo-size/darkwizard242/ansible-role-kubeadm?color=orange&style=flat-square)

# Ansible Role: kubeadm

Role to install (_by default_) [kubeadm](https://kubernetes.io/docs/reference/setup-tools/kubeadm/) on **Debian/Ubuntu** and **EL** systems.

## Requirements

None.

## Role Variables

Available variables are listed below (located in `defaults/main.yml`):

### Variables list:

```yaml
kubeadm_app: kubeadm
kubeadm_version: 1.31.0
kubeadm_os: "{{ ansible_system | lower }}"
kubeadm_architecture_map:
  amd64: amd64
  arm: arm64
  x86_64: amd64
  armv6l: armv6
  armv7l: armv7
  aarch64: arm64
  32-bit: "386"
  64-bit: amd64
kubeadm_dl_url: https://dl.k8s.io/release/v{{ kubeadm_version }}/bin/{{ kubeadm_os }}/{{ kubeadm_architecture_map[ansible_architecture] }}/{{ kubeadm_app }}
kubeadm_bin_path: /usr/local/bin
kubeadm_file_mode: '0755'
```

### Variables table:

Variable                 | Description
------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------
kubeadm_app              | Defines the app to install i.e. **kubeadm**
kubeadm_version          | Defined to dynamically fetch the desired version to install. Defaults to: **1.31.0**
kubeadm_os               | Defines OS type.
kubeadm_architecture_map | Defines os architecture. Used for obtaining the correct type of binaries based on OS System Architecture.
kubeadm_dl_url           | Defines URL to download the kubeadm binary from.
kubeadm_bin_path         | Defined to dynamically set the appropriate path to store kubeadm binary into. Defaults to (as generally available on any user's PATH): **/usr/local/bin**
kubeadm_file_mode        | Mode for the binary file of kubeadm.

## Dependencies

None

## Example Playbook

For default behaviour of role (i.e. installation of **kubeadm**) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.kubeadm
```

For customizing behavior of role (i.e. specifying the desired **kubeadm** version) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.kubeadm
  vars:
    kubeadm_version: 1.22.0
```

For customizing behavior of role (i.e. placing binary of **kubeadm** package in different location) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.kubeadm
  vars:
    kubeadm_bin_path: /bin/
```

## License

[MIT](https://github.com/darkwizard242/ansible-role-kubeadm/blob/master/LICENSE)

## Author Information

This role was created by [Ali Muhammad](https://www.alimuhammad.dev/)
