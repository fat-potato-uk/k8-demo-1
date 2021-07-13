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

The dashboard is a useful UI for your cluster and can allow you to easily make changes, view logs and manage cluster resources.

### Install/create a manifest for a published container

In this tutorial we are going to use [this docker image](https://hub.docker.com/repository/docker/fpjack/sample-app)

We will use `kubectl` to apply a YAML spec to our running cluster. These YAML specs define what we want to create

We need to ensure we are pointing at the correct cluster that we want to make changes to, running `kubectl config current-context` should return `minikube`

If this is not the case then run `kubectl config use-context minikube` to switch


Below I have put together a spec that defines a simple pod with the above image in it.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: single-pod
  labels:
    role: myrole
spec:
  containers:
    - name: server
      image: fpjack/sample-app
      ports:
        - name: web
          containerPort: 8080
          protocol: TCP
```

To apply a YAML spec to our cluster we can use `kubectl apply -f <path/to/yaml/file>`, or in this example

```shell
kubectl apply -f resources/single-pod.yaml
```

This should give you a log to say the pod was created and navigating to the dashboard should confirm this

![Created pod](single-pod-created.png)

### Port forward & View Endpoints

### View debug/output in K8 dash

### Scale out the pod

### Introduce a service/redeploy

### Node-port and port-forward the service

### Round robin visit all instances

