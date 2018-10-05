

 - Create daemonset

```terminal
user@MASTER:~/ex$ kubectl create -f https://k8s.io/examples/controllers/daemonset.yaml
daemonset.apps/fluentd-elasticsearch created
```
- Get daemonset details

```ShellSession
user@MASTER:~$ kubectl get ds --all-namespaces --show-labels=true -l k8s-app=fluentd-logging
NAMESPACE     NAME                    DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE     LABELS
kube-system   fluentd-elasticsearch   3         3         3       3            3           <none>          7m50s   k8s-app=fluentd-logging
```

- Get all daemonset list

```ShellSession
user@MASTER:~$ kubectl get ds --all-namespaces
NAMESPACE     NAME                      DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR                     AGE
kube-system   fluentd-elasticsearch     3         3         3       3            3           <none>                            7m22s
kube-system   kube-flannel-ds-amd64     3         3         3       0            3           beta.kubernetes.io/arch=amd64     2d14h
kube-system   kube-flannel-ds-arm       0         0         0       0            0           beta.kubernetes.io/arch=arm       2d14h
kube-system   kube-flannel-ds-arm64     0         0         0       0            0           beta.kubernetes.io/arch=arm64     2d14h
kube-system   kube-flannel-ds-ppc64le   0         0         0       0            0           beta.kubernetes.io/arch=ppc64le   2d14h
kube-system   kube-flannel-ds-s390x     0         0         0       0            0           beta.kubernetes.io/arch=s390x     2d14h
kube-system   kube-proxy                3         3         3       3            3           <none>                            2d14h

```

- Get daemonset list by filtering lables

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgzMTI4MDE1MiwtNzkyMjk2MTg1LDIwND
QzNTMzMzldfQ==
-->