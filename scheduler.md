# SCHEDULER- Portable Batch System

- Super computers or compute clusters, the competition among users to obtain time to run programs is typically fierce.
- Supercomputers provide excellent performance, and distribute performance among all users in a fair manner.
- Users expect that their code will run very fast and provide them with answers to their scientific questions at a high turn-around rate. 
- On a laptop or workstation any request for CPU time is immediately handled by the operating system
- Laptop or workstation is a computational resource that is used mostly by one user only - namely you
- A super computer is a shared resource. Many users can log into it at the same time and work on your code, perform computations 
- In order to prevent clashes of tasks that require time on the machine exclusively, every action on the cluster needs to be described by a user. An application called the job scheduler then uses this description to decide when and where to best place the action for execution.
- We have a 12-node cluster. Each individual computer in the cluster (also called a node) has 16 CPU cores, 32GB of memory and a connection to a network that all nodes are members of and can hence communicate by.
- A job scheduler(pbs,torque,slurm) is put in place on a compute cluster that manages tasks on it. It accepts task (or better ‘job’) descriptions. Based on the current usage of the nodes, it can then decide when a task is launched (or dispatched or spooled in HPC speak) on a node. The scheduler also helps treating the output of a job to forward it to the submitter’s terminal or write it to a file.

# PBS script
      #PBS –N jobname ---> name of the job
      #PBS -o job.out ---> output file
      #PBS -e job.err ---> error file
      #PBS -l nodes=4:ppn=2  ---> The number of nodes and processors per node.
      #PBS -l walltime=1:00:00 ---> hh:mm:ss
      #PBS -l mem=n{mb|gb} ---> Sets the maximum amount of memory allocated to the job.


# PBS commands

    qsub <job_script> --> Your job will be submitted to the PBS scheduler and executed
    when there will be nodes available.

    qstat -a --> Shows the list of all your scheduled jobs, along with their status

    qstat -f <job_id> --> Provides a long list of informations for the job requested.
    In particular, if your job isn’t running yet, you'll be notified about its
    estimated start time or, if you made an error on the job script, you will
    learn that the job won’t ever start.

    qdel <job_id> ---> Removes the job from the scheduled jobs by killing it.
   
    qhold <jobid> Place a hold on your job in the queue and stops it from running.

# PBS Job States

    F ---> Job has Finished exiting and execution. The job was completed
     successfully and had no application errors.

    H ---> Job is Held. A job is put into a held state by the server or by a user or
     administrator. A job stays in a held state until it is released by a user or
     administrator.

    Q ---> Job is Queued, eligible to run or be routed.

    R ---> Job is Running.

    S ---> Job is Suspended by server. A job is put into the suspended state when a
    higher priority job needs the resources.

# PBS Variables

    PBS_O_WORKDIR ---> PBS sets the environment variable PBS_O_WORKDIR to the
    directory from which the batch job was submitted.

    PBS_NODEFILE ---> Contains a list of the nodes assigned to the job.

    PBS_JOBNAME ---> Name of the job.

# Exercise 1
   ## Objectives
     - check the nodes in a cluster
     - run a simple job submission script 

a). ## On your terminal issue the command

     pbsnodes -a --> **check state on the nodes (state, np, properties, memory, etc)** 

b) In this exercise you would submit a job that print hostname, date and “Hello World"

    create a file with command touch hello.sh

c) Using an editor of your choice(nano,pico,vim,emacs) open hello.sh script and add the following lines;

     #!/bin/bash
     hostname
     date
     sleep 30
     echo "Hello HPC"
     date

d) Use qstat command to check the status of the job you submitted.

# Exercise 2. 
   ## objectives
       - write a simple rscript
       - submit rscript to PBS

a) On the command prompt issue a command _mkdir Rtest_ to create a folder. Create a file in Rtest with command _touch mean.R_ then copy and paste the code below using any editor. 
   
    #!/usr/bin/env Rscript
    n <- c(2, 3, 5, 10, 14)
    mean(n)
    
**Save and close the file** 

b) Issue a command _touch rpbs.sh_ to create a pbs script. Add the code below

     #!/bin/sh
     ##PBS -l nodes=2:ppn=8
     ##PBS -l walltime=00:01:00
     ##PBS -N mean**
     ##PBS -M <email address> 
     ##PBS -e /home/username/Rtest/std_err.err
     ##PBS -o /home/username/Rtest/std_out.

    module load R/3.5.0/gcc-6.2.0

    cd $PBS_O_WORKDIR

    R --file=/home/username/Rtest/mean.R

## save and close the file.

c) submit the job with the command _<qsub rpbs.sh_

d) chech the status of your job with _<qstat_

e)  When the job has completed navigate to Rtest direcory to view your files created


  For Support Contact sehurutshib@ub.ac.bw
