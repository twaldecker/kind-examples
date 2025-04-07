# kind

This is a simple example to start a service on kind (Kubernetes in Docker) on Podman with Nix.

This works on Windows with Ubuntu in WSL2 and MacOS.

# Components on Windows

    ┌──────────┐           
    │Kind      │           
    ├──────────┤           
    │Podman    ├──────────┐
    ├──────────┤   Nix    │
    │Ubuntu    ├──────────┘
    ├──────────┤           
    │WSL 2     │           
    ├──────────┤           
    │Windows   │           
    └──────────┘           

# Components on macOS

    ┌──────────┐           
    │Kind      │           
    ├──────────┤           
    │Podman VM ├──────────┐
    ├──────────┤   Nix    │
    │macOS     ├──────────┘
    └──────────┘           

The only requirement to get started is Nix installed and flakes enabled.

# Usage

Start the nix development shell with all requirements:
```
nix develop
```

On macOS you need to create and start your Podman machine (only once):

```
podman machine init
podman machine start
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

Delete the cluster and the podman machine:
```
kind delete cluster
podman machine reset
```

# Resources

* https://stackoverflow.com/questions/62432961/how-to-use-nodeport-with-kind