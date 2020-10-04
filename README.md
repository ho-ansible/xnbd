# Ansible role: xnbd
Network block device

## DEPRECATED
This functionality has been moved to kubernetes,
so this ansible role is no longer maintained.

## Requirements
Only tested on Debian buster.

Create 200GB image (cannot be sparse file):
```
ionice -c 3 dd if=/dev/zero of=/srv/nbd0.img bs=1M count=200K
```

## Role Variables
+ `xnbd_role` (default: server): a `server` exports a local block dev
  for a `client` to mount remotely

### For clients:
+ `xnbd_hosts`: inventory list of servers to connect to.
  Parsed by `inventory_hostnames`, so can include groups and set operators.

### For servers:
+ `xnbd_address` (default: localhost): 
+ `xnbd_port` (default: 8250): IP and port for server to listen on
+ `xnbd_img` (default: /srv/nbd0.img): local block device 
  (e.g., /dev/sda1) or image file to export

## Playbooks
+ `main.yml`: apply role
+ `uninstall.yml`: remove. Run before removing config from inventory.

## Dependencies
None.

## License
+ Ansible role licensed [MIT](LICENSE)

## Author Information
+ Ansible role by [Sean Ho](https://github.com/ho-ansible/)
