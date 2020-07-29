# Ansible role postfix

Ansible role to configure postfix MTA.

This role is based on the [https://github.com/linux-system-roles/postfix](Red Hat, Inc. postfix role),
which has a couple of shortcomings in that it is not idempotent (which is an Ansible anti-pattern),
and also only supports adding/updating configuration items, and not removing them.

It provides Postfix configuration dictionary 'postfix_conf' which can hold key/value pairs of
all supported Postfix configuration parameters.

## Requirements

NONE

## Role Variables

TODO

## Dependencies

NONE

## Example Playbook

Install and enable postfix. Configure "relay_domains=$mydestination" and

```yaml
---
- hosts: all
  vars:
    postfix_conf:
      relay_domains: "$mydestination"
      relay_host: "example.com"
  roles:
    - postfix
```

Install and enable postfix.

```yaml
---
- hosts: all
  roles:
    - postfix
```

Install and enable postfix, and configure "relay_host=example.com":

```yaml
---
- hosts: all
  vars:
    postfix_conf:
      relay_host: "example.com"
  roles:
    - postfix
```

## License

GPLv2

## Author Information

Ashley Kleynhans
