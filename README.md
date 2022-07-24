# ansible-devstack

Provision a VM (As a default Ubuntu 20.04) and install a devstack inside the VM using libivrt

### prerequisites
The vkhitrin.libguestfs collection should be installed 
```
ansible-galaxy collection install vkhitrin.libguestfs
```

### How to run
It's advisable to create a YAML file such as myfile.yml
```
libvirt_vm_name: myvm
libvirt_vm_memory_mb: 8000                                                  
libvirt_vm_vcpus: 2                                                         
tmp_image_path: /tmp/myvm.qcow2  
```
And then run
```
$ ansible-playbook -i hosts -e @myvm.yml main.yml
```
It's possible to run only provisioning using the **provison** tag or devstack installation by using the **devstack** tag  

### Devstack
The default local.conf is taken from roles/devstack/templates/local.conf 
It's possible to supply a different local.conf by either overriding the file or passing the **local_conf** variable to point one with a different name.  

### local.conf templates
Currently there are 3 templates:  
- local.conf (The basic devstack)
- kuryr.conf (Including Kuryr)
- designate.conf (Including Designate)

### Connecting to the VM
You can find out the IP of the vm by running
```
$ sudo virsh doifaddr myvm
```
Or by looking at the hosts file

You can then connect using SSH using the stack user
```
$ ssh stack@<vm ip>
```

### Cleanup
If you delete the VM and want to reprovsion it's important to remove the line with the VM name from the hosts file  
