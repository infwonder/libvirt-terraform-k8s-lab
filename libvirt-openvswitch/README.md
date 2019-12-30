#### Note: requires libvirtd and openvswitch packages installed on host
on Ubuntu (18.04): 

  ``` sudo apt-get install -y openvswitch-switch openvswitch-testcontroller openvswitch-switch-dpdk openvswitch-common ```

Create openvswitch bridge:

 ``` sudo ovs-vsctl add-br ovsbr0 ```

Assuming your ethernet device is enp1s0, then hook up that device into vswitch:

 ``` sudo ovs-vsctl add-port ovsr0 enp1s0 ```

then connect ovs bridge to your host network:

 ``` dhclient -v ovsbr0 ```

and then use virsh to enable openvswitch.xml:

  ``` sudo virsh net-create openvswitch.xml ```
