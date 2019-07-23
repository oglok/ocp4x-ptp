# OCP 4.x support for PTP

Linuxptp is an implementation of the Precision Time Protocol (PTP) according to IEEE standard 1588v2 for Linux. This is a DaemonSet to support PTP in OCP4.x.

## Installing

- Build DaemonSet Container
```
podman build -t bastion.example.com:5000/ocp4x/ptp:4.1 -f Dockerfile.ubi
```

- Create namespace and RBACs
    ```
    oc create -f ./assets/manifests/01_namespace.yaml
    oc create -f ./assets/manifests/002_rbac.yaml
    ```

- Update and Deploy DaemonSet
    ```
    # Edit ConfigMap
    vi ./assets/manifests/03_daemonset.yaml
    oc create -f ./assets/manifests/03_daemonset.yaml
    ```

- Testing PTP sync - in one of the nodes execute
    ```
    chronyc sources
    ```

# Credits

Some PTP reference ideas from:
https://zshisite.wordpress.com/author/zshiredhat/