# Ansible role postfix

Ansible role to configure postfix MTA.

This role is based on the [Red Hat, Inc. postfix role](https://github.com/linux-system-roles/postfix),
which has a couple of shortcomings in that it is not idempotent (which is an Ansible anti-pattern),
and also only supports adding/updating configuration items, and not removing them.

It provides  Postfix configuration dictionary `postfix_conf_enabled` which can hold key/value pairs of
all Postfix configuration parameters to be added/updated, as well as a list `postfix_conf_disabled`
which can hold the keys of all Postfix configuration parameters to be removed.

## Requirements

NONE

## Role Variables

TODO

## Dependencies

NONE

## Example Playbook

Install and enable postfix:

```yaml
---
- hosts: all
  roles:
    - postfix
```

Install and enable postfix. Configure `relay_domains=$mydestination` and
`relay_host=example.com`:

```yaml
---
- hosts: all
  vars:
    postfix_conf_enabled:
      relay_domains: "$mydestination"
      relay_host: "example.com"
  roles:
    - postfix
```

Install and enable postfix, configure `relay_host=example.com`, and
remove configuration item for `smtpd_tls_security_level`:

```yaml
---
- hosts: all
  vars:
    postfix_conf_enabled:
      relay_host: "example.com"
    postfix_conf_enabled:
      - smtpd_tls_security_level
  roles:
    - postfix
```

## License

GPLv2

## Author Information

Ashley Kleynhans
