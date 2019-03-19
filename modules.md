# Environment Modules – A Great Tool for Clusters

- How do you have multiple compilers and multiple MPI libraries on the cluster at the same time and not get them confused?
- Traditional way – you change your $PATH in the .bashrc file (if you are   using Bash) - Initially this sounds like a pain - It doesn’t work in the situation where you want to run multiple jobs each with a different compiler/MPI combination and software.
- The Easy Way ---> **Environment modules** are used to manage multiple versions of software on a single system.
With modules you can keep both compiler versions on the system and move between the two easily.
- There is therefore a need to maintain multiple versions of the same applications on HPC systems.

# Using Environment Modules

        module avail - check is what modules are available to you.
        module list - check which modules are “loaded” in your environment
        module unload - To unload or remove a module

## _Exercise 1_
     Objectives
        view software installed
        load openmpi and R 
       
- On your terminal type the following commands     

         module avail
         which openmpi 
         module load openmpi/2.1.1/gcc-4.4.7 
         which openmpi
         module list

         which R 
         module load R/3.4.5
         which R




         Support or Contact sehurutshib@ub.ac.bw


