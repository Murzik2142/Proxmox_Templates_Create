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

proxmox_api_host: "proxmox1.home.local" - dns or ip-address\
proxmox_api_user: "root@pam" - login WebUI\
proxmox_api_password: "11111111" - password\
proxmox_node: "proxmox1" - node name (default: pve)\

qcow2_image_name: debian-12-genericcloud-amd64.qcow2 - name file\
qcow2_image_path: "/tmp/{{ qcow2_image_name }}" - location\
qcow2_download_url: "https://cloud.debian.org/images/cloud/bookworm/latest/debian-12-genericcloud-amd64.qcow2" - url download\

vmid: 9004 - ID template in proxmox\
template_name: Debian12CloudInit-ansible - Name template in Proxmox\
vm_storage: "local-lvm" - storage in Proxmox\
vm_net: "virtio,bridge=vmbr0,tag=2" - networking interface in Proxmox\

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
