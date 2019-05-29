# Ansible role: xnbd
Network block device

## Requirements
Only tested on Debian stable, for now.

Create 200GB image (cannot be sparse file):
```
ionice -c 3 dd if=/dev/zero of=/srv/nbd0.img bs=1M count=200K
```

## Role Variables
+ `xnbd_role` (default: server): a `server` exports a local block dev
  for a `client` to mount remotely
+ `xnbd_address`: IP to bind to

### For servers:
+ `xnbd_port` (default: 8250): for server to listen on
+ `xnbd_img` (default: /srv/nbd0.img): local block device 
  (e.g., /dev/sda1) or image file to export

## Dependencies
None.

## Example Playbook

```
- hosts: all
  roles:
    - { role: ho-ansible.xnbd }
```

## License
MIT

## Author Information
Sean Ho, https://github.com/ho-ansible/
