# [Ansible role vault_configuration](#ansible-role-vault_configuration)

Configure HashiCorp Vault on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-vault_configuration/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-vault_configuration/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-vault_configuration/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-vault_configuration)|[![downloads](https://img.shields.io/ansible/role/d/buluma/vault_configuration)](https://galaxy.ansible.com/buluma/vault_configuration)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-vault_configuration.svg)](https://github.com/buluma/ansible-role-vault_configuration/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-vault_configuration/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
- become: true
  gather_facts: true
  hosts: all
  name: Converge
  roles:
  - role: buluma.vault_configuration
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-vault_configuration/blob/master/molecule/default/prepare.yml):

```yaml
- become: true
  gather_facts: false
  hosts: all
  name: Prepare
  roles:
  - role: buluma.bootstrap
  - role: buluma.core_dependencies
  - role: buluma.hashicorp
  - role: buluma.vault
    vault_hardening_disable_swap: false
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-vault_configuration/blob/master/defaults/main.yml):

```yaml
vault_configuration_api_addr: https://{{ ansible_fqdn }}:8200
vault_configuration_cluster_addr: https://{{ ansible_fqdn }}:8201
vault_configuration_default_lease_ttl: 768h
vault_configuration_disable_cache: false
vault_configuration_disable_clustering: false
vault_configuration_disable_mlock: true
vault_configuration_group: vault
vault_configuration_listeners:
- address: 127.0.0.1:8200
  cluster_address: 127.0.0.1:8201
  http_idle_timeout: 5m
  http_read_header_timeout: 10s
  http_read_timeout: 30s
  http_write_timeout: '0'
  max_request_duration: 90s
  max_request_size: 33554432
  profiling:
    unauthenticated_in_flight_request_access: false
    unauthenticated_pprof_access: false
  proxy_protocol_authorized_addrs: ''
  proxy_protocol_behavior: ''
  telemetry:
    unauthenticated_metrics_access: false
  tls_cert: '-----BEGIN CERTIFICATE-----

    MIIDlDCCAnwCCQDKshDt/N9YbTANBgkqhkiG9w0BAQsFADCBiTELMAkGA1UEBhMC

    TkwxEDAOBgNVBAgMB1VUUkVDSFQxEjAQBgNVBAcMCUJyZXVrZWxlbjEXMBUGA1UE

    CgwOUm9iZXJ0IGRlIEJvY2sxGjAYBgNVBAMMEUNBIFJvYmVydCBkZSBCb2NrMR8w

    HQYJKoZIhvcNAQkBFhByb2JlcnRAbWVpbml0Lm5sMB4XDTIzMDIxMzA4NTg1MloX

    DTIzMDMxNTA4NTg1MlowgY0xCzAJBgNVBAYTAk5MMRAwDgYDVQQIDAdVVFJFQ0hU

    MRIwEAYDVQQHDAlCcmV1a2VsZW4xFzAVBgNVBAoMDlJvYmVydCBkZSBCb2NrMR4w

    HAYDVQQDDBV2YXVsdC5yb2JlcnRkZWJvY2submwxHzAdBgkqhkiG9w0BCQEWEHJv

    YmVydEBtZWluaXQubmwwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDN

    LeDgfuElvJL+EPY6zaPx/lF8nblytGvxIy/8BBpsu9wyvI0Ty9XXxk7alwdTM+mE

    LYA1Nznnk0ekC9gaQTLRUGqTOJ92la0Z6M4/yVxe9gvN5yNsUjU01dXXiFzgx0e4

    usdnrqkZchi5Ib0SunHm1sE0O3uEYdW9mJrqWb25HLLmQwtrztr9bE5PBUH8CzlX

    fqM6+6e2e1pnmPmt533GtIJcwfBg+pUkc01EfhKzLjtILgAijfx+m+XjpKShGLUg

    QTL4V9fmXCmPBP0IYjw8I5k64aBLTQ/oj1sw4EzkaVKxTtluiAENDf2x9yPaoH3x

    PkPG36D5/4JK90THTihlAgMBAAEwDQYJKoZIhvcNAQELBQADggEBAAdPO8l+ww5p

    YJKZ3COyzz/RWHQ4R1fH3KQE53Jk4kjARoEcuh34YQJ3uWbiyrMMorHUrKStWrEO

    297pMizrA45bFm79gwoZ1yI/2WdejnC86JFdAbHRWLkEKs40Fy9JhEU0ouHLk7ya

    Gr9hGKWNVJmnNpk+xpmIY1hi5L4Opb8/hRe16MzhpVivyenyekEpu4S0muZXvUKt

    igLKDsMemBMADA1xS05IJ8PVfSpsGxhB9cga1DL94Bpq+p1ZSSbupQUNEIObi8BK

    vIciVdKVLy30rGn2JGKSEQ9fnULuZUWxjOv0awqKRpFE5WVnav2iwF4pzvRxFw7Y

    ba0Ft217IrI=

    -----END CERTIFICATE-----

    '
  tls_cipher_suites: ''
  tls_client_ca_file: ''
  tls_disable: false
  tls_disable_client_certs: false
  tls_key: '-----BEGIN PRIVATE KEY-----

    MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQDNLeDgfuElvJL+

    EPY6zaPx/lF8nblytGvxIy/8BBpsu9wyvI0Ty9XXxk7alwdTM+mELYA1Nznnk0ek

    C9gaQTLRUGqTOJ92la0Z6M4/yVxe9gvN5yNsUjU01dXXiFzgx0e4usdnrqkZchi5

    Ib0SunHm1sE0O3uEYdW9mJrqWb25HLLmQwtrztr9bE5PBUH8CzlXfqM6+6e2e1pn

    mPmt533GtIJcwfBg+pUkc01EfhKzLjtILgAijfx+m+XjpKShGLUgQTL4V9fmXCmP

    BP0IYjw8I5k64aBLTQ/oj1sw4EzkaVKxTtluiAENDf2x9yPaoH3xPkPG36D5/4JK

    90THTihlAgMBAAECggEBAL0sxL8YHOyXPowkBXLYMYWob2dPYTHiKfft8osRGXAR

    kYfyEr0i3iqRPBkM0QMkxPRKo3/tSGU8hPw6s2gZnwogc/MDbPuAK1bNMITdWl5v

    yxhwOVfhQA9T7VNI9iGFe5pWFA6DmoPMkAD5m4NOBkDI1uAay9qV/eVOc98JGQU3

    Scc5H9gMvxe2J0njyUv+W4p5y8oMz0iVxqDvbQEduUuVZ7xKp1YysitfKViss2ej

    Ug3VcsPltuUrARfC/vO5PYJ2BXt9tHxPfu+nykGi42zAM6ex4xJyFiXnpZBOvjk1

    XIklhN9CoelxoECAxl7YgtweRwlbKf7belYd61HkmS0CgYEA9/zlX/BjIgmQjG7T

    odbb36pw9qW5M8ZVIIPQj5hndtPlGoESjcmHeogV1zAmsKvnQ6BuRUB4ZUh/nEpf

    HMPY1UaJ1L9jR8GjXh9mlVMAStYVwOxU2iILYditQ+BzLbr4ChNriI/Zo1/wIhxZ

    fk/cyutSF4z+RJ3C3+wPCk1n7H8CgYEA087pobuaiF5vSlnbjHIbb4zxPrxT1rW3

    k5KTC6RyMVW92yoOr6Gwgizzyq+qW4YSs3lePfN9oHxkkFJ9SU1/uV2ta64fnsxI

    HqbbgsMTKX1BbtkxNDYOCWvduJmC83LBYPVblPDvSr4G7zqxWyo3PQm9O/MrbtlW

    zrjGJrEYSRsCgYAINB2CZvlgjuBxRNlLaUgsxf6mqiTOSalXQgUMOwZxL+FMVyi9

    +AS7UPUoATfGcGleG1iKge95qkROb0dmNDRgGc1FdG9cWFOHMZK7Ldu8nghqMWc9

    MBMgUYKp1Cr7QEwkSTAtfFS+ytWuyzFKtGmhbNdyX/+pVW606aI1vQnLEQKBgQC0

    jXtHLR7sBGQmIzcuH88XZjP34J4vNzRIDfhfQk09lPOEsfNW8CQAs8UWEGzOHBow

    99LISJnchm1LQaYfKHsqTpqYYhP+T/Fif6Y7b4MUKPvwPCDfevy4N0UIKYQhdr81

    obHx4vh45EgRAh1Rs0jnNTgktINfuNFw4r23Gduz5QKBgD1qGo2Yjtk9blNV5v4Z

    oEKp5NQ+2Fbkpwl9k+nyA9CaSs98uf7C7Br7vrt/JBjAu447p/myeT9GiJSao6xj

    g8DTnnIvFuiLS9NKJMH4S2sd7P73j9djdV8J0qpxiEE6PMGjXrz455G6vowdKldu

    xWZvV9q5Ouxf7iRPf3o2cfKw

    -----END PRIVATE KEY-----

    '
  tls_min_version: tls12
  tls_require_and_verify_client_cert: false
  type: tcp
  x_forwarded_for_authorized_addrs: ''
  x_forwarded_for_hop_skips: 0
  x_forwarded_for_reject_not_authorized: true
  x_forwardesd_for_reject_not_present: true
- address: /run/vault/vault.sock
  socket_group: vault
  socket_mode: '666'
  socket_user: vault
  type: unix
vault_configuration_log_level: ''
vault_configuration_max_lease_ttl: 768h
vault_configuration_owner: vault
vault_configuration_plugin_directory: ''
vault_configuration_storage_raft:
  autopilot_reconcile_interval: 10s
  autopilot_redundancy_zone: ''
  autopilot_update_interval: 2s
  autopilot_upgrade_version: ''
  max_entry_size: 1048576
  node_id: '{{ ansible_hostname }}'
  path: /opt/vault/data
  performance_multiplier: 0
  retry_join:
  - auto_join: ''
    auto_join_port: 8200
    auto_join_scheme: https
    leader_api_addr: https://127.0.0.1:8200
    leader_ca_cert: '-----BEGIN CERTIFICATE-----

      MIIDkDCCAngCCQCDSFQRyRuDWDANBgkqhkiG9w0BAQsFADCBiTELMAkGA1UEBhMC

      TkwxEDAOBgNVBAgMB1VUUkVDSFQxEjAQBgNVBAcMCUJyZXVrZWxlbjEXMBUGA1UE

      CgwOUm9iZXJ0IGRlIEJvY2sxGjAYBgNVBAMMEUNBIFJvYmVydCBkZSBCb2NrMR8w

      HQYJKoZIhvcNAQkBFhByb2JlcnRAbWVpbml0Lm5sMB4XDTIzMDIxMzA4NTg1MVoX

      DTIzMDMxNTA4NTg1MVowgYkxCzAJBgNVBAYTAk5MMRAwDgYDVQQIDAdVVFJFQ0hU

      MRIwEAYDVQQHDAlCcmV1a2VsZW4xFzAVBgNVBAoMDlJvYmVydCBkZSBCb2NrMRow

      GAYDVQQDDBFDQSBSb2JlcnQgZGUgQm9jazEfMB0GCSqGSIb3DQEJARYQcm9iZXJ0

      QG1laW5pdC5ubDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALSXuMkY

      ROOcKbZBb63oWoDE26I3MNLsCvTY7vqMAZU0Mshe7rv+TfIw8RIYV8vXS9fBo11U

      ICG8q+q3vaDrFJR1Vfdk2GMrk/sTL+E4VzJirqLmaAAEzWAnQ+woGvYNXuGl9x3I

      /B0CJcrRQOJi0lL7NKKQmMXwhdw/m5eZDjekfp+JyHt7vuhKlLaOcY2d6An4Pmc6

      MxdQIFWy89HRU604uFFoExDNFZkEWr8a/bVGb8lRiG+AnxW0cuus1kgbl9/avW9d

      kDDi7hE7FO9apr0GfF0nva6C39zaiUxG/ZB0IPWaAOsEHXhRtMUUJM6J9FT3LhPS

      GGVV+bK5PEs/ekMCAwEAATANBgkqhkiG9w0BAQsFAAOCAQEAYJ1D2h7nEQoXC8Ka

      w87hNP37oYDLgkXZoxNK+h5UBmYjMATGcZPbbeGsppdi3qRb3pEqNwCWlzETSJqG

      0HzUSEeRjLp2mxLZuMHSlq+wRj2vtsN/IV5Gz/hs23LSxVXMEF7DLRSWY++sOPC9

      /2bN3eJGhjMoDP4Pgr/h/7Kk2dqOrxR4Etgli7nxIKiUNpCAwhv+yodGz3qDBSj1

      KWn9KbjlX/IIRakY9Gh7X+UDUWFJU30vU0so5hKKtrq0ZQoDCPhfYV9T0SLd5N3y

      JHufLAJw5yK8WMpBOhqmnoGco48nnsRJ55qK8xeTiVGgsewhjyeHNMUP7RDDptua

      mo3kZQ==

      -----END CERTIFICATE-----

      '
    leader_client_cert: ''
    leader_client_cert_file: ''
    leader_client_key: ''
    leader_client_key_file: ''
    leader_tls_servername: ''
  retry_join_as_non_voter: false
  snapshot_threshold: 8192
  trailing_logs: 10000
vault_configuration_tls_directory: /opt/vault/tls
vault_configuration_ui: false
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-vault_configuration/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.core_dependencies](https://galaxy.ansible.com/buluma/core_dependencies)|[![Build Status GitHub](https://github.com/buluma/ansible-role-core_dependencies/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-core_dependencies/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-core_dependencies/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-core_dependencies)|
|[buluma.hashicorp](https://galaxy.ansible.com/buluma/hashicorp)|[![Build Status GitHub](https://github.com/buluma/ansible-role-hashicorp/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-hashicorp/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-hashicorp/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-hashicorp)|
|[buluma.vault](https://galaxy.ansible.com/buluma/vault)|[![Build Status GitHub](https://github.com/buluma/ansible-role-vault/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-vault/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-vault/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-vault)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-vault_configuration/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-vault_configuration/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-vault_configuration/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

