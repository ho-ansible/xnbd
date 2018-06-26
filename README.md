# Ansible role: xnbd
Network block device

## Requirements
Only tested on Debian stable, for now.

Create 200GB image (cannot be sparse file):
```
ionice -c 3 dd if=/dev/zero of=/srv/nbd0.img bs=1M count=200K
```

## Role Variables
+ `xnbd_address`: public IP of server
+ `xnbd_port` (default: 8250): for server to listen on
+ `xnbd_img` (default: /srv/nbd0.img): local block device
  (e.g., /dev/sda1) or image file to export
+ `xnbd_server_group` (default: xnbd-server): name of
  ansible inventory group for all xnbd servers.
  A host using this role without being in the server group
  will be configured as a client.

## Dependencies
None.

## Example Playbook

```
- hosts: xnbd-servers
  roles:
    - { role: ho-ansible.xnbd }
```

## License
MIT

## Author Information
Sean Ho, https://github.com/ho-ansible/
