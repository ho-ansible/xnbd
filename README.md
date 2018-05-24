# Ansible role: xnbd
Network block device

## Requirements
Only tested on Debian stable, for now.

Create 200GB image (cannot be sparse file):
```
ionice -c 3 dd if=/dev/zero of=/srv/nbd0.img bs=1M count=200K
```


## Role Variables

## Dependencies
None.

## Example Playbook

```
- hosts: xnbd
  roles:
    - { role: ho-ansible.xnbd }
```

## License
MIT

## Author Information
Sean Ho, https://github.com/ho-ansible/
