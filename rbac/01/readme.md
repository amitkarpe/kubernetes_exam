# read-only rbac role

You are working for BeeBox, a company that provides regular shipments of bees to customers. The company is in the process of building a Kubernetes-based infrastructure for some of their software.

Your developers frequently request that you provide information from the Kubernetes cluster, so you would like to give them the ability to read data from the cluster but not make any changes to it. Using Kubernetes role-based access control, ensure the dev user can read pod metadata and container logs from any pod in the beebox-mobile namespace.

A kubeconfig file for the dev user has already been created on the server. You can use this file to test your RBAC setup as the dev user like so:
```
kubectl get pods -n beebox-mobile --kubeconfig /home/cloud_user/dev-k8s-config
```

### More info
```
❯ kubectl explain roles
KIND:     Role
VERSION:  rbac.authorization.k8s.io/v1

DESCRIPTION:
     Role is a namespaced, logical grouping of PolicyRules that can be
     referenced as a unit by a RoleBinding.

❯ kubectl api-resources --verbs=list,get | grep rbac.authorization.k8s.io/v1
clusterrolebindings                            rbac.authorization.k8s.io/v1           false        ClusterRoleBinding
clusterroles                                   rbac.authorization.k8s.io/v1           false        ClusterRole
rolebindings                                   rbac.authorization.k8s.io/v1           true         RoleBinding
roles                                          rbac.authorization.k8s.io/v1           true         Role
```

### CMD
```
❯ kaf read-role.yaml
role.rbac.authorization.k8s.io/read created

❯ kaf read-rolebinding.yaml
rolebinding.rbac.authorization.k8s.io/read-pods created

❯ k auth can-i 'get' 'pods' --as testuser
yes
❯ k auth can-i 'get' 'log' --as testuser
Warning: the server doesn't have a resource type 'log'
no
❯ k auth can-i 'get' 'logs' --as testuser
Warning: the server doesn't have a resource type 'logs'
yes
❯ k auth can-i 'get' 'pods/logs' --as testuser
yes

❯ k auth can-i 'delete' 'pods' --as testuser
no

# Delete
❯ k delete role read
role.rbac.authorization.k8s.io "read" deleted
❯ k delete rolebinding read-pods
rolebinding.rbac.authorization.k8s.io "read-pods" deleted
```