# Processes on Machines

code, config, and network connections

service 
- collection of process across machines to deliver a unit of functionality
- single ip address with LB across the scenes
- same dns name

instance 
- an installation on a single machine (container, virtual, or physical)
- processes of the same executable just running in different locations

executable
- an artifact a machine can launch as a process and created by build process
- also includes shared libraries

process
 - an operating system process on a machine; the runtime image of an executable
 

installation 
- the executable and any attendant directories, config files, and other resources as they exist on a machine

deployment
- the act of create an installation on a machine
- should be automated
- definition kept in source control

## Code

### Building the Code

establish strong `chain of custody` from developer to prod instance

version control
- no excuse
- no third party libs

build and test portion locally

private library repo

include plugins (Jenkins plugins)

only make production builds on a CI server and put binary into safe repo nobody else can write to

### Immutable and Disposable Infrastructure

Chef, Puppet, and Ansible

don't pin versions (newer version via npm month later)

start from known image and apply fixed set of changes, never try to update or patch

change is needed build a new image

launch new container and throw away the old

## Configuration

## Configuration Files

reads at startup

basic

per environment

code look outside directory for per-environment changes

## Configuration with Disposable Infrastructure

- inject config at startup
- config service

zk and etcd

### Naming config properties

clear enough to avoid unforced errors

`authenticationProvider`instead of `hostname`

## Transparency

qualities that allow operators, devs, and business sponsors to gain 
historical sense of trends, present conditions, instantaneous state, and 
future projects

allow change and survive

### Designing for Transparency

built in from the beginning

roll up and alerting outside of the instance

### Enabling Technologies

black-box or white-box

black-box by ops after delivered

logging and health scrapers

white-box process during development and usually involve 3rd party libraries

usually with an api

### Logging

valuable, show activity and status

#### log locations

not where app lives

symlink logs folder

stdout

#### log levels

serve primarily for production operation rather than testing or development

`error` or `severe` needs ops to look at

`warn` for errors in business logic or user input

###### debug logs in prod

`debug` or `trace` levels in prod is rarely a good idea and create noise

#### Human Factors

human-readable

clear, accurate, and actionable

#### Voodoo Operations

restart primary db

#### Final Notes on Logging

include identifiers like user ID, session ID, transaction ID, or arbitrary request number

state transitions

### Instance Metrics

small teams use service rather than building own like Netflix

### Health Checks

applications own internal view of own health (`normal`)

more than `yup, up and running`

- host ip and addresses
- version of the runtime (jvm version, ...)
- application version or commit
- accepting work
- status of connection pools, caches, circuit breakers

load balancer check health

## Wrapping Up

deployable, configurable, and monitorable

next `interconnect` - availability and security










