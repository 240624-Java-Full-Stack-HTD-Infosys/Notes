# GCP Cloud Shell
Google Cloud Shell is an online development environment that can be accessed anywhere from your browser. It is basically a command-line Linux shell integrated into the Google Cloud Platform. It differs from a Linux VM in that only your user environment is persistent. You get 5GB of storage for your $HOME directory which persists, everything else is completely transient and will be deleted when your session ends.

## GCP Integration
Like most of these services, Cloud Shell integrates with the rest of GCP. Cloud Shell comes loaded with the gcloud CLI, allowing you to manage your GCP services from the command line convienently. Other tools and command-line interfaces are installed as well such as MySQL, Docker, Kuberctl, minikube, and Skaffold.

## Developing
Cloud Shell offers an editor as well, so you can develop apps in this environment. It's basically an in-browser instance of VSCode ready to support Python, C#, Go, Java, and Node.js.