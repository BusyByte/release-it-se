# Stability Patterns

not the number of patterns applied

recovery oriented mind-set
 
## Timeouts

networks are fallible

any resource pool that blocks threads needs a timeout

### Is all this clutter worth it?

nobody notices when the system doesn't go down

generic gateway to handle templating

make full use of platform - Amazon api gateway

retries are likely to fail again

keeps resources busy longer than needed

queing work for slow retry later can be good

web api 10 to 100 ms

timeouts synergy with circuit breakers

## Remember This

- apply timeouts to integration points, blocked threads, and slow responses

- apply timeouts to recover from unexpected failures 

- consider delayed retries

## Circuit Breaker

fuse - burn up before the house does

fuse is disposable - one time use

same size as a copper penny

circuit breakers
- detect excess usage
- fail first
- open the circuit

allow one subsystem to fail without destroying the entire system

onces danger has passed can be reset to restore full function of the system

wrap dangerous operations in component that can circumvent calls when not healthy

closed state - operate normal

number of failures or rate over threshold trips circuit breaker open

after a suitable amount of time goes into half open where call has chance of succeeding

trial call fails - go back into open state until ready to try again

trial call fails - goes back into closed state

may also have a fallback strategy 
- last known state or cached value
- secondary service

involve a systems stakeholders on handling open state

usually interested in fault density than total count

leaky bucket pattern - Pattern Languages of Program Design 2

changes to circuit breaker state should always be logged

current state queried by monitoring

need a way to manually reset circuit breaker

circuit breaker around a single process

not share circuit breaker across multiple processes

use a framework so you don't single thread your calls

## Remember This

- don't do it if it hurts
- use together with timeouts
- expose, track, and report state changes

## Bulkheads

- partitions when sealed divide ship up into separate, watertight compartments

hatches prevent water from moving from one section to another

single penetration of hull does not sink the ship

principle of damage containment

physical redundancy

across zones and AWS regions

partition baz when foo band bar depend on it

## Remember This

- save part of the ship
- pick a useful granularity
- consider bulkheads with shared services model

## Steady State

keep people off of production systems to greatest extend possible

pets rather than cattle

no fiddling - one release cycle without human intervention

data - buckets fill up over time and must be drained

## Data Purging

db after about 2 years compromize the whole system

increasing I/O rates and latency

usually left for later and doesn't happen

## Log Files

log file rotation

### What about compliance?  Don't we have to keep our log files forever?

logstash

## In Memory Cache

- space of keys finite?
- cached items ever change?

time based or LRU

## Remember This

- avoid fiddling
  - eliminate need for recurring human intervention
- purge data with application logic
- limit caching
- roll the logs

## Fail Fast

if any of circuit breakers open for any ingredient then fail fast rather than 
doing work and then ending up failing

parameter checking before talking to the database

### We Got the Fax -- It's All Black

push validation errors to the beginning

report system failure (resources not available) differently than an applicaiton failure (param violations or illegal state)

reporting generic error cause circuit breaker to trip because some user entered bad data and hit reload three or four times

fail fast improves stability by avoiding slow responses

## Remember This

- avoid slow responses and fail fast
- reserve resources, verify integration points early
- use for input validation



  










