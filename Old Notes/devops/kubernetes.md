# Kubernetes
## Why Use Kubernetes?

Keeping containerized apps up and running can be complex because they often involve many containers deployed across different machines. Kubernetes provides a way to schedule and deploy those containers and scale them to your desired state as well as manage their lifecycle. 

You can use Kubernetes to implement your container-based application in a portable, scalable, and extensible way.


## How Kubernetes works?

Kubernetes provides an open source API that controls how and where containers will run.
Kubernetes orchestrates clusters of virtual machines and schedules containers to run on those virtual machines based on their available compute resources and the resource requirements of each container. 

Containers are grouped into **pods**, the basic operational unit for Kubernetes. Pods scale to your desired state.

Kubernetes also automatically manages service discovery, incorporates load balancing, tracks resource allocation, and scales based on compute utilization. 

Furthermore it checks the health of individual resources and enables apps to self-heal by automatically restarting or replicating containers.


## What are Kubernetes Containers?

Containers are a method of building, packaging and deploying software. A container includes all the code, runtime, libraries and everything else the containerized workload needs to run.

Containers are standardized, self-contained execution enclosures for applications. Typically, a container will include a single application, often composed of microservices, along with the binaries and libraries needed to execute properly. By limiting containers to a single process, diagnosis of problems is easier, as is updating applications. 

Unlike VMs, containers do _not_ contain the underlying operating system, and thus considered lightweight as compared to VMs. 


## Container Deployment 

Container deployment is the act of pushing (or deploying) containers to their target environment, such as a cloud or on-premise server. While a container might hold an entire application, most container deployments are really multi-container deployments, meaning you are pushing multiple containers to the target environment. For more dynamic, large-scale systems, you might deploy hundreds or even thousands of containers a day.

## Containers and Microservices

They are designed to be spun up (started) and down (stopped) quickly depending on the application. This is because containers are often used as a method of building, packaging, and deploying microservices. Microservice describes a software architecture that divides a large solution (sometimes called a monolith or monolithic application) into smaller logical units. Each of these microservices then runs independently in its own container. There are myriad advantages to this modern software development practice, including the ability to speed up deployments and subsequent code changes. 

## Why use Container Deployment?

Container deployments are well-suited to a variety of modern software and infrastructure strategies, including the aforementioned microservices approach. They can speed up application development and reduce the budget on IT operations teams, because they’re abstracted away from the environments they run in.


As a result, containerized applications have become a popular choice among DevOps teams and other organizations that have moved away from traditional monolithic (or “legacy”) approaches to software development. Container deployments also work well with continuous integration (CI) and continuous delivery (CD) processes and tools.

> The related but distinct field of continuous deployment, another 
"CD" acronym, takes continuous delivery a step further and fully automates the deployment of code to production, without requiring manual approval.


## What is a Kubernetes Cluster?
A Kubernetes **cluster** is a set of nodes that run containerized applications. The containerization processes combines an app with its dependencies and some necessary services. 


### Master Nodes vs Worker Nodes

Kubernetes clusters are comprised of one **master node** and a number of **worker nodes**. These nodes can either be physical computers or virtual machines, depending on the cluster.

The master node controls the state of the cluster; for example, which applications are running and their corresponding images. The master node is the origin for all task assignments. It coordinates processes such as:

- Scheduling and scaling applications
- Maintaining a cluster's state
- Implementing updates


The worker nodes are the components that run these applications. Worker nodes perform tasks assigned by the master node. They can either be virtual machines or physical computers, all operating as part of one system.

> There must be a minimum of one master node and one worker node for a Kubernetes cluster to be operational. For production and staging, the cluster is distributed across multiple worker nodes. For testing, the components can all run on the same physical or virtual node.


## Namespaces 

A **namespace** is a way for a Kubernetes user to organize many different clusters within just one physical cluster. Namespaces enable users to divide cluster resources within the physical cluster among different teams via resource quotas. For this reason, they are ideal in situations involving complex projects or multiple teams. 


## What are Pods?

A **pod** is the smallest execution unit in Kubernetes. A pod encapsulates one or more applications. Pods are ephemeral by nature, if a pod (or the node it executes on) fails, Kubernetes can automatically create a new replica of that pod to continue operations. Pods include one or more containers (such as Docker containers).

In Kubernetes, containers do not run directly on cluster nodes; instead one or more containers are encased in a pod. All applications in a pod share the same resources and local network, easing communications between applications in a pod. 

Pods utilize an agent on each node called a **kubelet** to communicate with the Kubernetes API and the rest of the cluster. Although developers need API access, management of pods is transitioning to the domain of DevOps.


As the load on a pod increases, Kubernetes can automatically replicate the pod to achieve desired scalability. Thus it is important to design a pod to be as lean as possible. Pods should contain a single main process along with any helper or ‘side-car’ containers necessary for their execution.



## The Difference Between Containers and Pods?
Containers encompass the code required to execute a specific process or function. Before Kubernetes, organizations would run containers directly on a physical or virtual server, but without the scalability and flexibility offered by a Kubernetes cluster.


Pods offer another level of abstraction for containers. One or more application can be wrapped into a pod (think peas in a pod), and the pod is the smallest unit of execution in a Kubernetes cluster. For example, pods can contain initialization containers that prepare the environment for the containerized application code and then terminate before the application container begins execution. Pods are the smallest unit of replication in a cluster, so all containers in a pod will scale up or down together.


Pods include persistent storage volumes as well as containers, if access to persistent storage is necessary for the application.

## What are Kubernetes nodes?

Just as the pod is the smallest execution unit in Kubernetes, a node is the smallest unit of compute hardware in a Kubernetes cluster. Nodes can be physical on-premises servers, or VMs that reside either on-premises or at a cloud provider.


Like containers, nodes provide a layer of abstraction. If an operations team thinks of a node as simply a resource with processing power and memory, each node becomes interchangeable with the next. Working together, nodes form the Kubernetes cluster, which automates distributing workloads as demands change. If a node fails, it is automatically removed from the cluster and other nodes take over. Every node runs an agent called a **kubelet**, which communicates with the cluster control plane.

Nodes are the domain of DevOps and IT.

## Pods vs. Nodes?
Pods are an abstraction of executable code, nodes are abstractions of computer hardware, so the comparison is a bit apples to oranges.


Pods are simply the smallest unit of execution in Kubernetes, consisting of one or more containers, each with one or more application and its binaries.


Nodes are the physical servers or VMs that comprise a Kubernetes Cluster. Nodes are interchangeable and typically not addressed individually by users or IT, other than when maintenance is required.






