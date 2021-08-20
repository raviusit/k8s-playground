# k8s-playground
playground to learn kubernetes and GitOps using ArgoCD



This is just a placeholder repo. The code repos for this whole exercise are - 

https://github.com/raviusit/k8s-kind-cluster.git

https://github.com/raviusit/k8s-argocd.git

https://github.com/raviusit/k8s-argocd-apps.git

https://github.com/raviusit/k8s-solve-problems.git

https://github.com/raviusit/hello-kubernetes-dev-config.git

https://github.com/raviusit/hello-kubernetes-prod-config.git

https://github.com/raviusit/k8s-ingress-nginx.git

#Welcome to the playgorund wiki!

### Pre-Req
Docker Desktop should be installed & running on your system. 
Make sure you have enough Memory assigned to docker > 4GB (or 2GB). Preference --> Resource.

# Step 1
## Download and install kubectl on local system
```sh
https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/
https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/
```
Verify kubectl version by running the below command
```sh
kubectl version   
```

# Step 2
## Download kind binary and install on local system

### MAC (Using curl)
```sh
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.0/kind-darwin-amd64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind
```
### MAC (Using brew)
```sh
brew install kind
```

### WINDOWS (Using curl)
```sh
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.11.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe
```
## Verify kind version by running the below command
```sh
kind version 
```

# Step 3
## Install kubernetes cluster locally using the downloaded "kind" binary in the previous step
```sh
git clone https://github.com/raviusit/k8s-kind-cluster.git
cd k8s-kind-cluster
kind create cluster --config=kind-v1.19.7.yaml
```
# Step 4
## Verify the nodes are up and running
```sh
kubectl get nodes
kubectl get pods --all-namespaces
```
# Step 5
## Install ArgoCD

```sh
kubectl create ns argocd
git clone https://github.com/raviusit/k8s-argocd.git
cd k8s-argocd
kubectl apply -k overlays/dc2/ -n argocd
kubectl apply -k overlays/dc2/ -n argocd
```
## Verify ArgoCD is up and running

```sh
kubectl get pods -n argocd
```

Once ArgoCD is up & running, check if all Applications are deployed, synced and shows up healthy

```sh
kubectl get applications -n argocd
```


# Step 6
## Accessing ArgoCD

_**Disconnect from any VPN.**_

Add an entry to /etc/hosts file.

```sh
127.0.0.1 argocd-playground.com hello-dev-playground.com hello-stage-playground.com hello-prod-playground.com
```
Type the below URL in browser
https://argocd-playground.com/

## Credentials
```sh
username: training
password: training
```
