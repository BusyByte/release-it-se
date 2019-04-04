# Stability Antipatterns

through 51

## Integration Points

## Socket-Based Protocols

all threads blocked then server down

## The 5 A.M. Problem

## Packet Capture

- tcpdump
- wireshark

tcp_retries2

firewall drop connection on idle connections in pool
ping from db server keep them alive

## HTTP Protocols

use client library with fine grain controls over timeouts
- connection and read timeouts 

avoid client libraries map responses on to domain objects (interesting)

treat as data until you confirmed expectations

assume it doesn't work so well in streaming

text in maps and lists until decide what to extract

## Vendor API Libraries

## Countering Integration Point Problems

- circuit breaker
- decoupling middleware
- testing
  - integration test harness

## Remember This 

- necessary evil - every integration point will eventually fail in some way
  - need to be prepared
 
- prepare for many forms of failure

- know when to open up abstractions
  - packet sniffers and other network diagnostics
  
- failures propagate quickly
  - cascading failure if not defensive enough
  
- apply patterns to avert integration point problems
  - defensive programming via circuit breaker, timeouts, decoupling middleware, and handshaking
  
## Chain reactions

- horizontal scaling
- vertical scaling

fault tolerance through redundancy

load related failure - if 1 of 8 fails remaining 7 
likely to fail because they need bear extra load

bulkhead pattern

cascading failure in one layer causes cascading failure in another

## Searching

- health checks route to healthy instances

## Remember This

- recognize one server down jeopardizes the rest
 - one down others more likely as pick up slack

- hunt for resource leaks
 - memory
 
- hunt for obscure timing bugs
 - race conditions cause by traffic deadlocks could deadlock entire cluster

- use autoscaling
  - health checks and kill failing ones and bring up new ones
  
- defend with bulkheads
  - partition servers with bulkheads
  - prevent chain reactions
  
## Cascading Failures

- high fan in spread failures widely

- no timeouts will cause cascading failure

- circuit breaker

- circuit breaker and timeouts

## Remember This

- stop cracks from jumping the gap

- scrutinize resource pools
  - limit time for thread checkout
  
- defend with timeouts and circuit breaker  



