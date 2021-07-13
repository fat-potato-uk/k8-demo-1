# k8-demo-1

### Install minikube

Minikube is what we will use to run Kubernetes locally. Therefore, the first step we need to do is to install minikube

To install the latest minikube on macOS run the following

```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube
```

Once we have minikube installed we can run `minikube start` to start our local cluster, the following is what we expect to see


```console
➜  k8-demo-1 git:(main) ✗ minikube start
😄  minikube v1.22.0 on Darwin 11.4
✨  Using the docker driver based on user configuration
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
💾  Downloading Kubernetes v1.21.2 preload ...
    > preloaded-images-k8s-v11-v1...: 502.14 MiB / 502.14 MiB  100.00% 1.76 MiB
    > gcr.io/k8s-minikube/kicbase...: 361.09 MiB / 361.09 MiB  100.00% 1.24 MiB
🔥  Creating docker container (CPUs=2, Memory=8100MB) ...
🐳  Preparing Kubernetes v1.21.2 on Docker 20.10.7 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

If this is not the case then more information for installing minikube on alternative systems can be found here [minikube start](https://minikube.sigs.k8s.io/docs/start/)

### Overview of dashboard

To monitor the cluster we can use a dashboard, the [Kubernetes Dashboard](https://github.com/kubernetes/dashboard) is a simple web-based UI for kubernetes.

The dashboard makes it easy and simple to monitor and troubleshoot applications running in the cluster.

Conveniently, minikube already comes with integrated support for this dashboard, to start the dashboard run `minikube dashboard`


![minikube dashboard](k8s-dashboard.png)

### Install/create a manifest for a published container

### Port forward & View Endpoints

### View debug/output in K8 dash

### Scale out the pod

### Introduce a service/redeploy

### Node-port and port-forward the service

### Round robin visit all instances

