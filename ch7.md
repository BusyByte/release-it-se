# Foundations

design for production

operations

## Networking in the Data Center and Cloud

## NICs and Names

FQDN = host name + search domain

hostname command

dns = external name

return ip

don't need to match up

many to many relationship

ifconfig/ipconfig

machine have multiple NIC's

multi-homed

desktop = wifi + ethernet + loopback (127.0.0.1)

data center = admin and monitoring on different network

backups - separate switches or vlan

ssh only available through admin interface

## Programming for Multiple Networks

apps configurable to which interfaces must bind to

### Outbound Connections

- en0
- en1
- bond0

routing table has default gateway bond0

## Physical Hosts, Virtual Machines, and Containers

### Physical Hosts

now expendable hardware

huge shift from 10 years

2 specialized computing
- extra RAM
- GPU

bulk storage SAN or NAS

bonnie64

most likely virtualized

### Virtual Machines in the Data Center

many vm's on same physical host

don't move vm's because disruptive to guest operating system

any resource can be oversubscribed (CPU, RAM, network)

contention and slowdown

watch out for:

- distributed programming that waits on synch responses for whole cluster to respond
- "special" machines like cluster managers or lock managers
- subtle dependency on event / request ordering

different physical host different clock

sync vm clock when it wakes up

if external human time is important don't use os time use local ntp server

### Containers in the Data Center

effects older monitoring systems like Nagios

overlay network - vlans - network for just containers

k8s, mesos, docker swarm

#### Virtual LANs for Virtual Machines

- allow containers to believe they are on isolated networks
- support load balancing via virtual IPs
- use a firewall as a gateway to the external network

12-factor app

injecting configuration when starting container

password vaulting

https://12factor.net

Avoid long startup

### Virtual Machines for the Cloud

VMs killed for no reason

told to restart or else

rent elastic IP addresses

one NIC with private IP

NIC supports about 64k connections

setup another for monitoring and management

### Containers in the Cloud

pushes complexity out of the boxes and into the control plane

## Wrapping Up

- how is the network structured?
- do machines have long-lasting identities?
- are machines automatically set up and torn down?

 
chapter 8 for next week
Ignacio lead it


