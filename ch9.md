# Interconnect

- ops
- control plane
- interconnect
- instances
- foundation

knit bunch of instances together in cohesive system

- traffic management
- load balancing
- discovery

interconnect - high availability

instance level - transparency and control

## Solutions at Different Scales

large team - Consul for dynamic discovery service

small team - DNS entries

large company - high rate of change

dedicated ops team

unrealistic every developer knows about every other developers changes

small company - rate of change is lower; all have lunch together

big company - push boundaries of dynamic tools and bring Spinnaker, k8s, Mesos, and Consul

even smallest teams must have monitoring

## DNS

IP addresses stable enough for DNS to be useful

### Service Discovery with DNS

find team, get host, put host in configuration file

provider responsible for load balancing and high availability

logical service name to call, not physical host

even if just alias it's preferable

### Load Balancing with DNS

DNS round-robin

associates sever IP addresses with a service name

IP addresses must be reachable

no info on health

no distribution of load, just initial connections

Java's build in classes  will cache first IP address it receives from DNS

### Global Server Load Balancing with DNS

GSLB

route across geographic locations

keeps track of health and responsiveness of pools

dns - which IP to offer, after is out of picture

load balancer (local traffic manager) - traffic cop, serves as a reverse proxy where call goes through it

must reach global traffic and local traffic managers

ton logic in GSLB like weight distribution, disaster recovery, or rolling deployment

### Availability of DNS

don't host on same infrastructure as production systems

more than one DNS server in different locations

different DNS for public status page

no fail-over scenarios leave without one DNS server

### Remember This

- don't change often
- round robin is low cost load balancing
- discovery is human process
- works well with global traffic management in coordination with local load balancers
- diversity is crucial in DNS hosts

## Load Balancing

horizontal scaling - capacity and resilience

active load balancing

VIP - virtual IP mapping to pools

pool - IP addresses and policy info

- load balancing algorithm
- health checks to perform
- stickiness of client sessions
- what to do with requests when no pool members are available

to the calling application should be transparent

software or hardware

both with benefits

### Software Load Balancing

low-cost solution uses application

application is reverse-proxy

Squid, HAProxy, Apache httpd, and nginx all great reverse-proxy load balancers

add x-forwarded-for so can log

can cache responses

Akamai - biggest reverse proxy cluster

involved in every request

when start talking about load balancing in front of reverse-proxy then need another solution

### Hardware Load Balancing

F5's Big-IP 

better throughput

any connection oriented protocol, not just HTTP or FTP

traffic fail-over for disaster recovery

low end - five digits

high end - six digits

### Health Checks

one of most important services can provide

### Stickiness

directing requests to same instances

can prevent load from being distributed evenly

some way to group requests

### Partitioning Request Types

content-based routing

something in URLs

### Remember This

- virtual IPs map to pools of instances
- software at application level and cheap
- hardware reach much higher skill; higher skills and cost
- health checks
- session stickiness
- content aware

## Demand Control

refuse work or scale out

### How Systems Fail

queue backing up

relationship between number of sockets available and requests per second your service can handle

depends on duration of requests (Little's Law)

going non-linear

raw I/O bandwidth

Ethernet is a serial protocol

read and write queue

buffer

listen queue

### Preventing Disaster

load shedding - turn away work we can't complete in time

load balancer sends 503 when all instances un-healthy

#### TIME_WAIT and the Bogons

inside data center can lower 

on Linux tcp_tw_reuse kernel setting

### Remember This

- reject work close to edge as possible
- provide health checks to protect application code
- start rejecting work when response time going to provoke retries

## Network Routing

vpn and destination unreachable

intermittent success

static route definitions

software-defined networking

### Unreliable Enumeration

different nic configurations because purchased different times

## Discovering Services

too many services for DNS to be practical

highly dynamic environment like containers

don't roll your own service discovery

can build on ZK or etcd

ZK is CP in "CAP"

Consul is "AP"

Docker Swarm

## Migratory Virtual IP Addresses

Virtual IP not directly tied to Ethernet MAC address

Virtual IP can migrate from one NIC to another

migratory IP fail-over

active/passive database clusters

SQLException on updates, inserts, or stored procedures when fail-over occurs

IOExceptions in strange places - retry against new node

## Wrapping Up

instances come together to form systems

load balancing, routing, load shedding, and service discovery



















