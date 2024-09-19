Proxmox_Templates_Create
=========

The task involves downloading Debian 12 from a repository to /tmp in qcow2 format and creating a template in Proxmox with cloudinit support.

Requirements
------------

Proxmox 8.2.4+\
Debian 12.4+\
ansible 3.1.2+\
ansible-galaxy 2.16.11+\
Not tested on earlier versions

Role Variables
--------------

___proxmox_api_host: "proxmox1.home.local"___ - dns or ip-address\
___proxmox_api_user: "root@pam"___ - login WebUI\
___proxmox_api_password: "11111111"___ - password\
___proxmox_node: "proxmox1"___ - node name (default: pve)

___qcow2_image_name: debian-12-genericcloud-amd64.qcow2___ - name file\
___qcow2_image_path: "/tmp/{{ qcow2_image_name }}"___ - location\
___qcow2_download_url: "https://cloud.debian.org/images/cloud/bookworm/latest/debian-12-genericcloud-amd64.qcow2"___ - url download

___vmid: 9004___ - ID template in proxmox\
___template_name: Debian12CloudInit-ansible___ - Name template in Proxmox\
___vm_storage: "local-lvm"___ - storage in Proxmox\
___vm_net: "virtio,bridge=vmbr0,tag=2"___ - networking interface in Proxmox

Dependencies
------------

Dependencies are absent

Example Playbook
----------------

```
- name: Create templates in Proxmox
  hosts: proxmox
  roles:
    - Proxmox_Templates_Create
```

License
-------

BSD-3-Clause

Author Information
------------------

Murzabaev Marat (murzik2142@gmail.com)
