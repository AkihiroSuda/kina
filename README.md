# kina: Kubernetes in Apple Containerization

Kina runs Kubernetes in [Apple Containerization](https://github.com/apple/containerization).

This is just a quick workaround until `kind` officially supports Apple Containerization.

Made in an hour during [Container Install Meetup (KubeCon North America 2025)](https://www.meetup.com/kubernetes-atlanta-meetup/events/311768936/), as an exercise to learn Apple Containerization.

## Installation

```bash
brew install container kubectl

# Install kina to ~/bin, ,/usr/local/bin, or whereever else
cp -a kina ~/bin
```

## Usage

Create a cluster:

```bash
kina create cluster
export KUBECONFIG="$HOME/.kina/kubeconfig"
kubectl get pods -A
```

Create a deployment:

```bash
kubectl create deployment nginx --image nginx:alpine
kubectl port-forward deployments/nginx 8080:80
```

Clean up:

```bash
kina delete cluster
```

Debug:

```bash
container exec kina-control-plane journalctl
```
