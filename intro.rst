What is a cluster?
=====================

A cluster consists of a large number of interconnected machines.

Each machine is very much like your own desktop computer, except it’s much more powerful. Like your desktop computer, each machine (often referred to as node) has a CPU, some memory, and a hard disk. The nodes running your programs are usually called compute nodes.

To turn the nodes into a cluster we need three more ingredients: a network, data storage, and a queue manager. In section we’ll discuss these components in a bit more detail to give you an understanding of how a cluster works.


Network
--------
Nodes in the cluster connect to a high-performance network. The network allows programs running on different nodes to “talk” to each other.


Storage
--------
Bioinformatics is data intensive so we can’t just use a single hard disk as you would in your own computer. Instead, we buy several dedicated hard disks and use a file system that can manage files across these disks.
The storage might be divided into partitions, and presented to the user in different locations on their path.


Queue manager
---------------
In theory, any user would be able to log in to any node and run a program, which may consume the resources of the entire node. This could cause other users’ programs on the same node to crash. Alternatively, one user could start thousands of runs of a program on different nodes, consuming the resources of the entire cluster for an unknown duration of time. In short, it would be impossible to share the HPC without a system to handle requests.
To solve this problem we need a queue manager, which is a software that manages the requests for resources in a fair way.
Like at the supermarket or an office, you stand in the queue and wait until it’s your turn. On the cluster, you submit jobs to the queue and your jobs will run on some node chosen by the queue manager, once resources are available.

The queue manager also allows you to specify certain requirements for your program to run. For example, your program may need to run on a node with a lot of memory. If you specify this when submitting your job, the queue manager will make sure to run the job on a node with at least that amount of memory available.

At NIBSC we use a queue manager called Slurm: to run your programs on the HPC, you’ll be interacting a lot with Slurm.


Things to remember…
--------------------

A few things that you should keep in mind when using the cluster:

    - The nodes in a cluster are set up so that they’re all (more or less) identical. Software that is available on one node will also be available on all other nodes and you can access your files in the same way on all nodes. When the queue manager runs your job on a node, it more or less corresponds to you logging in to the node and running the program yourself.

    - You access the cluster through a single node, often denoted the frontend or head node (in our case *hpc-head*). The frontend node is identical to the other nodes, but it is set up to allow access from the Internet. Your day-to-day interaction with the cluster goes through the frontend. But, you should not run any computation or memory intensive programs on the frontend. All users share the frontend’s resources and you should only use it for basics things like looking around the file system, writing scripts, and submitting jobs.

In the coming sections you will learn how to connect to the cluster so that you can start submitting jobs.


Learning to use the shell
--------------------------
When interacting with the cluster you will be using a shell on a Linux/UNIX system. If you are not familiar with these concepts we recommend the Shell novice tutorial from `Software Carpentry`_.

.. _Software Carpentry: https://swcarpentry.github.io/shell-novice/
