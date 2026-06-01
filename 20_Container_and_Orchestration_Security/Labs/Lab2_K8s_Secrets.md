# Lab 2: K8s Secret Hunting (Conceptual)

## Goal: Steal credentials from a Kubernetes cluster.

## The Flow:
1. **Find the API Server**: Use `nmap` to find port 6443.
2. **Check for Anonymous Access**: Try to list pods using `kubectl get pods`.
3. **Steal Secrets**:
   `kubectl get secrets`
   $\rightarrow$ `kubectl get secret <secret-name> -o yaml`
4. **Decode**: The secrets are Base64 encoded. Use `echo <value> | base64 -d`.

## Success Check:
- [ ] Understand how K8s secrets are stored.
- [ ] Know how to use `kubectl` to query a cluster.
