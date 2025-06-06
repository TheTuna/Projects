## Helm

### Troubelshooting
- The "Error: INSTALLATION FAILED: Unable to continue with install: could not get information about the resource ClusterRole "prom-kube-state-metrics" in namespace " appears on ```helm install`` command
    <details>
    <summary>Reason:</summary>
    K8s user doesn't have the ClusterRole permission
    </details>

    Solution:
