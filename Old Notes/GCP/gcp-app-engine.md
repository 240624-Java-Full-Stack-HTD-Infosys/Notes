# GCP App Engine
Google Cloud App Engine "is a fully managed serverless application platform with simple administration." This quote from GCP sums up what App Engine is: a hardware agnostic platform for development which lets you easily deploy your projects into the larger google cloud ecosystem. Write your code in one of the supported languages, and this platform-as-a-service (PaaS) will handle the rest. When your code is ready you simply tell GCP to deploy it to their data centers, and make use of all the features GCP has to offer, such as scaling, fault tolerance, load balancing, and more.

## Serverless
If an application is reachable on a network, it can't be serverless. This is true of apps in GCP. When we say "serverless" we don't actually mean "no servers", instead it just means we are abstracted away from those concerns. When we use App Engine (and much of GCP) we are abstracted away from infrastructure concerns. We don't need to worry about the server hardware, where it's located, how much power it has, etc. If we want our app to be highly available and have redundancies, GCP handles that for is. If we are getting no traffic, GCP will scale our resources down and charge us less. If we get more traffic our app's available resources will scale up, and we will pay more.

A large portion of GCP services are "serverless" and they often overlap in functionality. With GCP it can be difficult to understand what services are utilized, it's all an ever expanding ecosystem.

## Supported Languages
App Engine supports a few common languages natively, which means we will find a fully supported development environment withy many of the tools we would be familiar with. 
 - Go
 - PHP
 - Java
 - Python
 - Node (JS)
 - .NET (C#)
 - Ruby

Even if our choice of language isn't directly supported we can run custom containers with our choice of languages and frameworks.

## App Engine Environments
Each App Engine project uses one (or both) of the following environments: standard, and flexible. Both can be used silmultaneously.

### Standard
This is the environment for natively supported languages and is best for apps which would require rapid scaling. The standard environment can scale down to 0 resources, where it doesn't cost a thing. They can scale back up to handle traffic as it comes. This environment option is good for handling sudden extreme changes in traffic.

### Flexible
This environment runs applications in Docker containers, and supports any languages and frameworks which can run in a Docker container. This environment scales a bit slower, and can't scale down to 0, a minimum of one container always runs. Adding more instances (horizontal scaling) will take minutes as opposed to seconds for standard environments. 

## App Engine & GCP Features
Where App Engine ends and the rest of GCP services begin is a little hard to define. App Engine allows us to deploy our applications, but where do they go? Is App Engine scaling our apps up and down or some other service? There is some overlap with other services, and App Engine represents an entry point into the wider GCP ecosystem.

### Hosting
Servers can be hosted by a few different services, including GCP Compute Engine. Front ends can likewise be deployed to Firebase, another Google product. 

### Scaling
Scaling is what these cloud platforms are all about. If our app doesn't have any work to do today, we don't need entire data centers to manage a workload of 0. The resources we would have idling will be re-purposed for other apps running in Google's data centers.  
  
GCP will perform both vertical and/or horizontal scaling depending on the needs of the application.

### Load Balancing
If we are scaling horizontally (adding additional instances to take some of the workload) we need to handle that workload and make sure it gets split among the instances. This is load balancing. When Google spins up more VMs or containers, it handles routing traffic between the whole set.

### Fault Tolerance
Another feature that goes hand-in-hand with horizontal scaling is fault tolerance. If one of the instances goes down for whatever reason, we can re-balance the traffic to the remaining instances. Meanwhile now that there is more traffic on those, GCP will scale up more instances to replace the crashed one. With modern infrastructure this is seamless and simple. These systems are how we can measure application availability in terms of "nines", for instance a benchmark for high availability might be "five nines" or 99.999%.

### and more...
 - We can split traffic to preform A/B testing
 - We can monitor application performance, and debug issues
 - GCP offers a suite of security features, including SSL certificates for hosted sites.