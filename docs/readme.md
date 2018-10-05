

[Create](link)

[Get1](link)

[Get2](link)

[Delete](link)

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
