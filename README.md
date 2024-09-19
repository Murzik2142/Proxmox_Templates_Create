Proxmox_Templates_Create
=========

The task involves downloading Debian 12 from a repository to /tmp in qcow2 format and creating a template in Proxmox with cloudinit support.

Requirements
------------

Proxmox 8.2.4+
Debian 12.4+
ansible 3.1.2+
ansible-galaxy 2.16.11+
Not tested on earlier versions

Role Variables
--------------

# Vars file for Proxmox_Templates_Create
proxmox_api_host: "proxmox1.home.local"
proxmox_api_user: "root@pam"
proxmox_api_password: "11111111"
proxmox_node: "proxmox1"

# Image disk qcow2
qcow2_image_name: debian-12-genericcloud-amd64.qcow2
qcow2_image_path: "/tmp/{{ qcow2_image_name }}"
qcow2_download_url: "https://cloud.debian.org/images/cloud/bookworm/latest/debian-12-genericcloud-amd64.qcow2"

### vars templates
# Templates ID
vmid: 9004
# Template Name
template_name: Debian12CloudInit-ansible
# Location disk storage
vm_storage: "local-lvm"
# Network interface
vm_net: "virtio,bridge=vmbr0,tag=2"

Dependencies
------------

Dependencies are absent

Example Playbook
----------------

- name: Create templates in Proxmox
  hosts: proxmox
  roles:
    - Proxmox_Templates_Create

License
-------

BSD-3-Clause

Author Information
------------------

Murzabaev Marat (murzik2142@gmail.com)
