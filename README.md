# kind

This is a simple example to start a service on kind (Kubernetes in Docker) on Podman with Nix.

This works on Windows with Ubuntu in WSL2 and MacOS.

Start the nix development shell with all requirements:
```
nix develop
```

Create a kind cluster with the config:
```
kind create cluster --config kind_config.yml
```

Apply kubernetes resources:
```
kubectl apply -f resources.yml
```

nginx starts and is reachable at
[http://localhost:30001](http://localhost:30001)

Delete the cluster:
```
kind delete cluster
```

Resourcen:

* https://stackoverflow.com/questions/62432961/how-to-use-nodeport-with-kind