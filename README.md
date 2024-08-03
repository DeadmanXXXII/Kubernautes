# Kubernautes

kubectl commands
Here’s an extended and detailed guide to Kubernetes (`kubectl`) CLI commands, including security configurations, monitoring, and troubleshooting.

### **Kubernetes (`kubectl`) CLI Commands**

#### **1. Cluster Management**

- **Get cluster information:**
  ```bash
  kubectl cluster-info
  ```

- **Display Kubernetes version:**
  ```bash
  kubectl version --short
  ```

- **List all nodes:**
  ```bash
  kubectl get nodes
  ```

- **Describe a specific node:**
  ```bash
  kubectl describe node NODE_NAME
  ```

- **View node resource usage:**
  ```bash
  kubectl top nodes
  ```

- **Check cluster-wide resource quotas:**
  ```bash
  kubectl get resourcequotas --all-namespaces
  ```

- **Check for cluster autoscaler status:**
  ```bash
  kubectl get clusterautoscalers
  ```

#### **2. Pod Management**

- **List all pods in a namespace:**
  ```bash
  kubectl get pods -n NAMESPACE
  ```

- **Describe a specific pod:**
  ```bash
  kubectl describe pod POD_NAME -n NAMESPACE
  ```

- **Get logs from a pod:**
  ```bash
  kubectl logs POD_NAME -n NAMESPACE
  ```

- **Stream logs from a pod:**
  ```bash
  kubectl logs -f POD_NAME -n NAMESPACE
  ```

- **Execute a command in a pod:**
  ```bash
  kubectl exec -it POD_NAME -n NAMESPACE -- COMMAND
  ```

- **Get pod resource usage:**
  ```bash
  kubectl top pods -n NAMESPACE
  ```

- **Delete a pod:**
  ```bash
  kubectl delete pod POD_NAME -n NAMESPACE
  ```

- **Get pod events:**
  ```bash
  kubectl describe pod POD_NAME -n NAMESPACE | grep Events -A 10
  ```

#### **3. Deployment Management**

- **List deployments:**
  ```bash
  kubectl get deployments -n NAMESPACE
  ```

- **Describe a specific deployment:**
  ```bash
  kubectl describe deployment DEPLOYMENT_NAME -n NAMESPACE
  ```

- **Scale a deployment:**
  ```bash
  kubectl scale deployment DEPLOYMENT_NAME --replicas=REPLICA_COUNT -n NAMESPACE
  ```

- **Roll out a new version of a deployment:**
  ```bash
  kubectl rollout update deployment DEPLOYMENT_NAME -n NAMESPACE
  ```

- **Check rollout status:**
  ```bash
  kubectl rollout status deployment DEPLOYMENT_NAME -n NAMESPACE
  ```

- **Rollback to a previous deployment version:**
  ```bash
  kubectl rollout undo deployment DEPLOYMENT_NAME -n NAMESPACE
  ```

- **Get deployment events:**
  ```bash
  kubectl describe deployment DEPLOYMENT_NAME -n NAMESPACE | grep Events -A 10
  ```

#### **4. Service Management**

- **List services:**
  ```bash
  kubectl get services -n NAMESPACE
  ```

- **Describe a specific service:**
  ```bash
  kubectl describe service SERVICE_NAME -n NAMESPACE
  ```

- **Get service endpoints:**
  ```bash
  kubectl get endpoints -n NAMESPACE
  ```

- **Port-forward a port from a service to localhost:**
  ```bash
  kubectl port-forward svc/SERVICE_NAME LOCAL_PORT:SERVICE_PORT -n NAMESPACE
  ```

#### **5. ConfigMaps and Secrets**

- **List ConfigMaps:**
  ```bash
  kubectl get configmaps -n NAMESPACE
  ```

- **Describe a ConfigMap:**
  ```bash
  kubectl describe configmap CONFIGMAP_NAME -n NAMESPACE
  ```

- **Create a ConfigMap from a file:**
  ```bash
  kubectl create configmap CONFIGMAP_NAME --from-file=FILE_PATH -n NAMESPACE
  ```

- **List secrets:**
  ```bash
  kubectl get secrets -n NAMESPACE
  ```

- **Describe a secret:**
  ```bash
  kubectl describe secret SECRET_NAME -n NAMESPACE
  ```

- **Create a secret from literal values:**
  ```bash
  kubectl create secret generic SECRET_NAME --from-literal=KEY=VALUE -n NAMESPACE
  ```

- **Create a secret from a file:**
  ```bash
  kubectl create secret generic SECRET_NAME --from-file=FILE_PATH -n NAMESPACE
  ```

- **Delete a secret:**
  ```bash
  kubectl delete secret SECRET_NAME -n NAMESPACE
  ```

#### **6. Namespace Management**

- **List namespaces:**
  ```bash
  kubectl get namespaces
  ```

- **Describe a specific namespace:**
  ```bash
  kubectl describe namespace NAMESPACE
  ```

- **Create a new namespace:**
  ```bash
  kubectl create namespace NAMESPACE
  ```

- **Delete a namespace:**
  ```bash
  kubectl delete namespace NAMESPACE
  ```

#### **7. Resource Management**

- **List all resources in a namespace:**
  ```bash
  kubectl get all -n NAMESPACE
  ```

- **Describe a specific resource:**
  ```bash
  kubectl describe RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE
  ```

- **Delete a specific resource:**
  ```bash
  kubectl delete RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE
  ```

- **Apply a configuration from a YAML file:**
  ```bash
  kubectl apply -f FILE_PATH.yaml
  ```

- **Delete resources defined in a YAML file:**
  ```bash
  kubectl delete -f FILE_PATH.yaml
  ```

- **Get a resource in YAML format:**
  ```bash
  kubectl get RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE -o yaml
  ```

- **Get a resource in JSON format:**
  ```bash
  kubectl get RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE -o json
  ```

#### **8. Security Configurations**

- **View RBAC roles:**
  ```bash
  kubectl get roles -n NAMESPACE
  ```

- **Describe a specific RBAC role:**
  ```bash
  kubectl describe role ROLE_NAME -n NAMESPACE
  ```

- **List role bindings:**
  ```bash
  kubectl get rolebindings -n NAMESPACE
  ```

- **Describe a specific role binding:**
  ```bash
  kubectl describe rolebinding ROLEBINDING_NAME -n NAMESPACE
  ```

- **View ClusterRoles:**
  ```bash
  kubectl get clusterroles
  ```

- **Describe a specific ClusterRole:**
  ```bash
  kubectl describe clusterrole CLUSTERROLE_NAME
  ```

- **List ClusterRoleBindings:**
  ```bash
  kubectl get clusterrolebindings
  ```

- **Describe a specific ClusterRoleBinding:**
  ```bash
  kubectl describe clusterrolebinding CLUSTERROLEBINDING_NAME
  ```

- **View PodSecurityPolicies:**
  ```bash
  kubectl get podsecuritypolicies
  ```

- **Describe a specific PodSecurityPolicy:**
  ```bash
  kubectl describe podsecuritypolicy PSP_NAME
  ```

- **View NetworkPolicies:**
  ```bash
  kubectl get networkpolicies -n NAMESPACE
  ```

- **Describe a specific NetworkPolicy:**
  ```bash
  kubectl describe networkpolicy NETWORKPOLICY_NAME -n NAMESPACE
  ```

#### **9. Monitoring and Logging**

- **View logs for a specific container in a pod:**
  ```bash
  kubectl logs POD_NAME -c CONTAINER_NAME -n NAMESPACE
  ```

- **Get the status of a specific pod:**
  ```bash
  kubectl get pod POD_NAME -n NAMESPACE -o wide
  ```

- **Monitor resource usage of all pods:**
  ```bash
  kubectl top pods -n NAMESPACE
  ```

- **View events in the cluster:**
  ```bash
  kubectl get events --all-namespaces
  ```

- **Export cluster resource metrics:**
  ```bash
  kubectl top nodes --sort-by=cpu
  ```

#### **10. Advanced Usage**

- **Use `kubeconfig` files to manage multiple clusters:**
  ```bash
  kubectl config use-context CONTEXT_NAME
  ```

- **View all contexts in `kubeconfig`:**
  ```bash
  kubectl config get-contexts
  ```

- **Add a new context to `kubeconfig`:**
  ```bash
  kubectl config set-context CONTEXT_NAME --cluster=CLUSTER_NAME --user=USER_NAME --namespace=NAMESPACE
  ```

- **Set a new current context:**
  ```bash
  kubectl config set-context --current --namespace=NAMESPACE
  ```

- **Remove a context from `kubeconfig`:**
  ```bash
  kubectl config delete-context CONTEXT_NAME
  ```

- **Check cluster access with RBAC rules:**
  ```bash
  kubectl auth can-i ACTION RESOURCE --namespace=NAMESPACE
  ```

- **Get a list of all API resources:**
  ```bash
  kubectl api-resources
  ```

- **View detailed API resources information:**
  ```bash
  kubectl api-resources --verbs=list --namespaced=true
  ```

- **Get API version information:**
  ```bash
  kubectl api-versions
  ```

- **Get detailed API information about a resource:**
  ```bash
  kubectl explain RESOURCE_TYPE
  ```

- **Describe a specific resource's API:**
  ```bash
  kubectl explain RESOURCE_TYPE --recursive
  ```

- **Edit a resource in place:**
  ```bash
  kubectl edit RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE
  ```

- **Patch a resource with a JSON patch:**
  ```bash
  kubectl patch RESOURCE_TYPE RESOURCE_NAME -p '{"spec": {"replicas": 3}}' -n NAMESPACE
  ```

- **Apply a patch to a resource from a file:**
  ```bash
  kubectl patch RESOURCE_TYPE RESOURCE_NAME -p "$(cat patch-file.json)" -n NAMESPACE
  ```

- **Replace a resource with a new configuration:**
  ```bash
  kubectl replace -f FILE_PATH.yaml
  ```

- **Export a resource to a file:**
  ```bash
  kubectl get RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE -o yaml > resource.yaml
  ```

- **Create a custom resource definition (CRD):**
  ```bash
  kubectl create -f crd-definition.yaml
  ```

- **List custom resources:**
  ```bash
  kubectl get CUSTOM_RESOURCE_TYPE -n NAMESPACE
  ```

- **Describe a custom resource:**
  ```bash
  kubectl describe CUSTOM_RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE
  ```

- **Delete a custom resource:**
  ```bash
  kubectl delete CUSTOM_RESOURCE_TYPE RESOURCE_NAME -n NAMESPACE
  ```

#### **11. Security Configurations**

- **View RoleBindings:**
  ```bash
  kubectl get rolebindings -n NAMESPACE
  ```

- **Describe a specific RoleBinding:**
  ```bash
  kubectl describe rolebinding ROLEBINDING_NAME -n NAMESPACE
  ```

- **View ClusterRoleBindings:**
  ```bash
  kubectl get clusterrolebindings
  ```

- **Describe a specific ClusterRoleBinding:**
  ```bash
  kubectl describe clusterrolebinding CLUSTERROLEBINDING_NAME
  ```

- **Create a ClusterRole:**
  ```bash
  kubectl create clusterrole CLUSTERROLE_NAME --verb=GET --resource=pods
  ```

- **Bind a ClusterRole to a user or group:**
  ```bash
  kubectl create clusterrolebinding BINDING_NAME --clusterrole=CLUSTERROLE_NAME --user=USER_NAME
  ```

- **View PodSecurityPolicies (if enabled):**
  ```bash
  kubectl get podsecuritypolicies
  ```

- **Describe a specific PodSecurityPolicy:**
  ```bash
  kubectl describe podsecuritypolicy PSP_NAME
  ```

- **Enforce security context constraints:**
  ```bash
  kubectl apply -f security-context-constraints.yaml
  ```

#### **12. Helm Integration**

- **List Helm releases:**
  ```bash
  helm list
  ```

- **Install a Helm chart:**
  ```bash
  helm install RELEASE_NAME CHART_NAME
  ```

- **Upgrade a Helm release:**
  ```bash
  helm upgrade RELEASE_NAME CHART_NAME
  ```

- **Rollback a Helm release:**
  ```bash
  helm rollback RELEASE_NAME REVISION
  ```

- **Uninstall a Helm release:**
  ```bash
  helm uninstall RELEASE_NAME
  ```

- **View Helm release history:**
  ```bash
  helm history RELEASE_NAME
  ```

#### **13. Advanced Monitoring and Debugging**

- **Access a pod’s shell:**
  ```bash
  kubectl exec -it POD_NAME -n NAMESPACE -- /bin/bash
  ```

- **Run a temporary pod for debugging:**
  ```bash
  kubectl run -i --tty debug --image=busybox -- /bin/sh
  ```

- **View detailed information about the Kubernetes API server:**
  ```bash
  kubectl describe pod -n kube-system -l component=kube-apiserver
  ```

- **Check pod events and errors:**
  ```bash
  kubectl describe pod POD_NAME -n NAMESPACE | grep -A 20 Events
  ```

- **List all containers in a pod:**
  ```bash
  kubectl get pod POD_NAME -n NAMESPACE -o jsonpath='{.spec.containers[*].name}'
  ```

- **Fetch pod and node network details:**
  ```bash
  kubectl exec POD_NAME -n NAMESPACE -- ip a
  ```

- **Run network troubleshooting tools:**
  ```bash
  kubectl exec POD_NAME -n NAMESPACE -- ping GOOGLE.COM
  ```

#### **14. Miscellaneous Commands**

- **List all kubeconfig contexts:**
  ```bash
  kubectl config get-contexts
  ```

- **Set a default namespace for the current context:**
  ```bash
  kubectl config set-context --current --namespace=NAMESPACE
  ```

- **Use a specific kubeconfig file:**
  ```bash
  kubectl --kubeconfig=/path/to/kubeconfig
  ```

- **Show detailed information about a specific context:**
  ```bash
  kubectl config view -o jsonpath="{.contexts[?(@.name=='CONTEXT_NAME')].context}"
  ```

This list provides advanced and comprehensive `kubectl` commands covering a wide range of Kubernetes management tasks, from basic operations to complex configurations, security settings, monitoring, and integration with Helm. These commands will help you efficiently manage and troubleshoot Kubernetes clusters.
