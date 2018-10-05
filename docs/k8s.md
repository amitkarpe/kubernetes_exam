

 - Create daemonset

```shell_session
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

```Shell
user@MASTER:~$ kubectl get ds --all-namespaces --show-labels=true -l k8s-app=fluentd-logging
NAMESPACE     NAME                    DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE     LABELS
kube-system   fluentd-elasticsearch   3         3         3       3            3           <none>          7m50s   k8s-app=fluentd-logging
```

- Get pod lists which are running these ds

```
user@MASTER:~/ex$ kubectl get pods  --all-namespaces -o wide --show-labels=true -l name=fluentd-elasticsearch
NAMESPACE     NAME                          READY   STATUS    RESTARTS   AGE   IP            NODE                         NOMINATED NODE   LABELS
kube-system   fluentd-elasticsearch-7v89q   1/1     Running   0          35m   10.244.1.73   amitkarpe3.mylabserver.com   <none>           controller-revision-hash=7474489b7b,name=fluentd-elasticsearch,pod-template-generation=1
kube-system   fluentd-elasticsearch-l8gwq   1/1     Running   0          35m   10.244.2.46   amitkarpe2.mylabserver.com   <none>           controller-revision-hash=7474489b7b,name=fluentd-elasticsearch,pod-template-generation=1
kube-system   fluentd-elasticsearch-w224f   1/1     Running   0          35m   10.244.0.14   amitkarpe1.mylabserver.com   <none>           controller-revision-hash=7474489b7b,name=fluentd-elasticsearch,pod-template-generation=1
user@MASTER:~/ex$
```
