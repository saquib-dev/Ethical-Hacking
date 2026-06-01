# Module 2: Container Escapes & Kubernetes

## The Container Escape
A "Breakout" happens when a process inside a container gains access to the host.
- **Privileged Mode**: If a container is run with `--privileged`, it has almost root access to the host.
- **Mounted Sockets**: If `/var/run/docker.sock` is mounted inside the container, you can use the Docker API to start a new container that has access to the host's root filesystem.

## Kubernetes (K8s)
K8s is the "Manager" of thousands of containers.
- **Kubelet**: The agent running on each node. If the Kubelet API is exposed, you can run commands in any pod.
- **Secrets**: K8s stores passwords in "Secrets". If you have access to the API, you can steal these secrets.
