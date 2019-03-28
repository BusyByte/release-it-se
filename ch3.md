# Stabilize Your System

cost of poor stability is lost revenue

lost reputation

## Defining Stability

robust - user can get work done even with stresses and impulses

## Extending Your Life Span

memory leaks and data growth

longevity testing

## Failure Modes

cracks in the system - some component fail before everything else

failure mode - collective damage

design reactions to failures

crumple zones

crackstoppers

## Stop Crack Propagation

Don't block on connections forever

Always set timeouts to something than forever

partition by groups

more tightly coupled more likely error to propagate

less coupled architectures - diminish error effects

## Chain of Failure

some events are more likely 

more likely to run out of error if the db is slow

coupled layers causes dependent errors

Fault - condition causing incorrect state in software (bug, external api)

Error - visibly incorrect behavior (buying a bunch of stock)

Failure - unresponsive system

Ask failure questions about interactions with external IO/integration

two philosophies (camps)
- make systems fault-tolerant
- let it crash - restart from known good state

## Wrapping Up

every production failure is unique

common patterns

stop cracks from propagating

first look at anti-patterns


