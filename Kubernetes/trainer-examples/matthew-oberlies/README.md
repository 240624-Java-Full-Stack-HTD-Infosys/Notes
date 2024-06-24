# Kubernetes

This demo will host a spring boot application that exposes /hello and /crash in order to demonstrate how kubernetes orchestrates containers.

## Minikube

This demo will use minikube to create a single node kubernetes cluster on a virtual machine. IMPORTANT: minikube requires a linux machine with at least 2 cpus. This means that the free tier EC2 is not capable of running minikube for this demo. Additionally, the virtualization driver used in this demo is kvm2, which is not pre-installed on the amazon-linux AMI, so ubuntu is the preferred AMI.

### Setup

The following are dependencies for this demo. Make sure you have installed them:

- git
- Java 8
- Maven
- docker
- [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)

Note that to avoid having to run docker commands with `sudo`, create a docker group and add your user to it to avoid needing to do this:
```bash
sudo groupadd docker # create the group
sudo usermod -a -G docker $USER # add your user to it
sudo service docker restart # restart the docker daemon
```

Once minikube is installed, it can be started with `minikube start --vm-driver=kvm2`. Alternatively, you can use Virtualbox (`minikube start --vm-driver=virtualbox`) or run with `--vm-driver=none` if you are already running on a VM.

## Build Project

In the kubernetes-service/ directory, run `mvn package` to create the kubernetes-service.jar file

## Create Image

In the kubernetes-service/ directory, run `docker build -t kubernetes-service .`

Now, if needed, you can push the image to your dockerhub account.
```bash
docker login
docker tag image_hash dockerhubusername/kubernetes-service:latest
docker push dockerhubusername/kubernetes-service:latest
```

## Create Deployment

Create a kubernetes deployment in a yaml file. `kubernetes-deployment.yaml` is already set up for this, but it can be modified as needed.
It creates a deployment called `kubernetes-service-deployment` with a spec of 2 replicas of the `kubernetes-service` image, of which, it is pulling from the `ikenoxamos` dockerHub account.
Additionally, kubernetes needs to know when the containers are available, and it will send a GET request to the container to just `/`, however,
Spring boot will not send a 200 response code, so we instead configure the health check to be sent to actuator.

## Get things running

Apply the deployment with `kubectl apply -f kubernetes-service-deployment.yaml`

You can check that it is working with `kubectl get deployments`

Once the containers are up and running, we can expose the containers externally with `kubectl expose deployment kubernetes-service-deployment --name=kubernetes-service --type=NodePort`

Note: We use NodePort since we are using Minikube, and we will actually expose the containers externally through a minikube service. If we were not using minikube, we would likely use LoadBalancer as the type

Expose as a minikube service with `minikube service kubernetes-service --url`
This will provide the external url

You can otherwise check that the services are externally available with `kubectl get services`
With minikube, the external IP will say pending, but it is still exposed through minikube

## Crash the service

We can use `kubectl get deployments` to see that the kubernetes-service-deployment has 2/2 containers

If we use the url provided from minikube to send a request to /crash, we can repeatedly use `kubectl get deployments` and watch as some of the containers are brought down and then spun back up.
