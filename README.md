# ansible-devstack

Install devstack on inside a virtual machine using libivrt

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

You then can find out the IP of the vm by running
```
$ sudo virsh doifaddr myvm
```
Or by looking at the hosts file

You can then connect using SSH using the stack user
```
$ ssh stack@<vm ip>
```
