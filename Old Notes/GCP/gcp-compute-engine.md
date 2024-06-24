# GCP Compute Engine
Compute Engine is GCP's virtual machine service. Similar to AWS' EC2, this service offers a number of vertically scalable VM offerings you can launch into VM instances which can make use of the rest of the GCP ecosystem. There are a number of machine images (pre-built OS images) to choose from including many distributions of Linux, as well as versions of Windows, Windows Server, and MacOS.

There are a wide variety of different machine types with their own attributes.

### Tau
Tau VMs are the lowest-cost option for horizontally scaling (scale-out) workloads

### General Purpose
C3, E2, N2D, and N1 are some designations for these VMs which offer a good balance of price and performance suitable for a wide variety of use cases.

### Ultra-High Memory
M1, and M2 are designations for memory-optimized machines suited for memory-intensive workloads.

### Compute-Intensive
C2, C2D, and H3 are designations for compute-intensive workloads suitable for high performance and low latency computing such as game servers.

### Accelerator-Optimized
A2 is a designation for accelerator-optimized machines. This refers to computing chips which can do limited number of tasks, but can do many operations in parallel. Like GPUs, which were called "graphics accelerators" back in the 90s. These "accelerator chips", and thus these accelerator-optimized machines are well suited to workloads like crypto mining, generative AI, and graphics processing. All three of these workdloads utilize similar circuitry to perform similar math operations at great speed.