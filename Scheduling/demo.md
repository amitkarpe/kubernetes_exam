
### Created

```ShellSession
user@MASTER:~/ex$ kubectl create -f scheduling_pod2.yaml
pod/busybox-sleep2 created
```

### Verified

```ShellSession
user@MASTER:~/ex$ kubectl label node amitkarpe3.mylabserver.com name=node3
node/amitkarpe3.mylabserver.com labeled

user@node1:~$ ssh k1 kubectl get nodes --show-labels=true
NAME                         STATUS   ROLES    AGE     VERSION   LABELS
amitkarpe1.mylabserver.com   Ready    master   3d15h   v1.12.0   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/os=linux,color=black,kubernetes.io/hostname=amitkarpe1.mylabserver.com,node-role.kubernetes.io/master=
amitkarpe2.mylabserver.com   Ready    <none>   3d15h   v1.12.0   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/os=linux,color=blue,kubernetes.io/hostname=amitkarpe2.mylabserver.com
amitkarpe3.mylabserver.com   Ready    <none>   3d15h   v1.12.0   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/os=linux,color=red,kubernetes.io/hostname=amitkarpe3.mylabserver.com,name=node3

user@node1:~$ ssh k1 kubectl get pod  -o wide --show-labels=true -l type=exercise
NAME             READY   STATUS    RESTARTS   AGE    IP            NODE                         NOMINATED NODE   LABELS
busybox-sleep1   1/1     Running   0          50s    10.244.1.82   amitkarpe3.mylabserver.com   <none>           sub=scheduling,type=exercise
busybox-sleep2   1/1     Running   0          107s   10.244.1.81   amitkarpe3.mylabserver.com   <none>           sub=scheduling,type=exercise

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM2MTk4OTQwNl19
-->