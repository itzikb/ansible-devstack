# ansible-devstack

Install devstack on inside a virtual machine using libivrt

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

You then can't find out the IP of the vm by running
```
$ sudo virsh doifaddr myvm
```

You can then connect using SSH and change to the stack user
```
$ ssh root@<vm ip> (pass:123456)
$ su - stack
```
