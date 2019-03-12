# SCHEDULERS-

- Super computers or compute clusters, the competition among users to obtain time to run programs is typically fierce
- On the other hand, expectations by users are high, that their code will run very fast and provide them with answers to their scientific questions at a high turn-around rate
- Supercomputers provide excellent performance, and distribute performance among all users in a fair manner.
- On a laptop or workstation any request for CPU time is immediately handled by the operating system
laptop or workstation is a computational resource that is used mostly by one user only - namely you
- A super computer is a shared resource. Many users can log into it at the same time and work on your code, perform computations 
- In order to prevent clashes of tasks that require time on the machine exclusively, every action on the cluster needs to be described by a user. An application called the job scheduler then uses this description to decide when and where to best place the action for execution.

- We have a 12-node cluster. Each individual computer in the cluster (also called a node) has 16 CPU cores, 32GB of memory and a connection to a network that all nodes are members of and can hence communicate by.
-A job scheduler is put in place on a compute cluster that manages tasks on it. It accepts task (or better ‘job’) descriptions. Based on the current usage of the nodes, it can then decide when a task is launched (or dispatched or spooled in HPC speak) on a node. The scheduler also helps treating the output of a job to forward it to the submitter’s terminal or write it to a file.

# Exercise

## On your terminal

-_pbsnodes -a_ - * check state on the nodes (state, np, properties, memory, etc) *

- A first exercise would be to submit a job that does nothing else but print “Hello World!”.
-_touch hello.sh_
using an editor (nano,pico,vim,emacs) open hello.sh script and add the following
-_#!/bin/bash_

-_hostname_
-_date_
-_sleep 30_
-_date_

b)A


qsub echo Hello World.sh


