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


