# fluxcd-gitops

[![license](https://img.shields.io/badge/license-Apache%202.0-blue)](./LICENSE)

A playground to manage [Kubernetes](https://kubernetes.io) cluster(s) using [FluxCD](https://fluxcd.io) with [Kustomize](https://kustomize.io).

## Requirements

- [flux cli](https://fluxcd.io/flux/installation/#install-the-flux-cli)
- [kind](https://kind.sigs.k8s.io) or [minikube](https://minikube.sigs.k8s.io/docs/)

## Setup

Create a cluster with `kind`

```shell
kind create cluster --name cluster --config ./multi-nodes-cluster.yaml
```

or start a `minikube` cluster

```shell
minikube start
```

[Install flux onto the cluster](https://fluxcd.io/flux/get-started/#install-flux-onto-your-cluster)

```shell
export GITHUB_TOKEN=token
export GITHUB_USER=username

flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=fluxcd-gitops \
  --branch=master \
  --path=./clusters/dev \
  --personal
```
