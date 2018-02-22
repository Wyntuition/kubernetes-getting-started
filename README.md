# Kube using Minikube

This tutorial uses Minikube to create a local cluster. This tutorial also assumes you are using Docker for Mac on OS X. If you are on a different platform like Linux, or using VirtualBox instead of Docker for Mac, the instructions to install Minikube may be slightly different. For general Minikube installation instructions, see the Minikube installation guide.

1. Use curl to download and install the latest Minikube release:

```bash
  curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 && \
  chmod +x minikube && \
  sudo mv minikube /usr/local/bin/
```

1. Use Homebrew to install the xhyve driver and set its permissions:

```bash
brew install docker-machine-driver-xhyve
sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
Use Homebrew to download the kubectl command-line tool, which you can use to interact with Kubernetes clusters:
```

1. Use Homebrew to download the kubectl command-line tool, which you can use to interact with Kubernetes clusters:

`brew install kubectl`

1. Determine whether you can access sites like https://cloud.google.com/container-registry/ directly without a proxy, by opening a new terminal and using

curl --proxy "" https://cloud.google.com/container-registry/
If NO proxy is required, start the Minikube cluster:

minikube start --vm-driver=xhyve

1. Now set the Minikube context. The context is what determines which cluster kubectl is interacting with. You can see all your available contexts in the ~/.kube/config file.

`kubectl config use-context minikube`

Verify that kubectl is configured to communicate with your cluster:

`kubectl cluster-info`




  REFERENCE: 
  https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/