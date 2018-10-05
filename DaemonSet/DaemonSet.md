
---shell
///
user@MASTER:~$ kubectl get ds --all-namespaces --show-labels=true -l k8s-app=fluentd-logging
NAMESPACE     NAME                    DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE     LABELS
kube-system   fluentd-elasticsearch   3         3         3       3            3           <none>          7m50s   k8s-app=fluentd-logging

---


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwODM5NDI2Nl19
-->