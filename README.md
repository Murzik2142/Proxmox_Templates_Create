Proxmox_Templates_Create
=========

The task involves downloading Debian 12 from a repository to /tmp in qcow2 format and creating a template in Proxmox with cloudinit support.

Requirements
------------

Proxmox 8.2.4+\
ALSE 1.8+\
ansible 3.1.2+\
ansible-galaxy 2.16.11+\
Not tested on earlier versions

Role Variables
--------------

___qcow2_image_name:___ alse-1.8.1-base-cloud-mg13.3.0-amd64.qcow2
___qcow2_image_path:___ "/tmp/{{ qcow2_image_name }}"
___qcow2_download_url:___ "https://registry.astralinux.ru/artifactory/mg-generic/alse/cloud/alse-1.8.1-base-cloud-mg13.3.0-amd64.qcow2"

___vmid:___ 100 - ID template in proxmox\
___template_name:___ Debian12CloudInit-ansible - Name template in Proxmox\
___vm_storage:___ "local-lvm" - storage in Proxmox\
___vm_net:___ "virtio,bridge=vmbr0,tag=2" - networking interface in Proxmox

Dependencies
------------

Dependencies are absent

Example Playbook
----------------

```
- name: Create templates in Proxmox
  hosts: proxmox
  vars:
    vmid: "9006"
  roles:
    - Proxmox_Templates_Create
```

License
-------

BSD-3-Clause

Author Information
------------------

Murzabaev Marat (murzik2142@gmail.com)
