## On Cluster Master

```bash
sudo swapoff -a
sudo apt-get update
sudo apt-get install docker.io -y
sudo cat <<EOF > /etc/docker/daemon.json
{
    "exec-opts": ["native.cgroupdriver=systemd"]
}
EOF

sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
sudo cat <<EOF > /etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
sudo apt update
sudo apt install -y kubeadm kubectl kubelet

sudo kubeadm init --pod-network-cidr=10.244.0.0/16
mkdir -p $HOME/.kube; sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config; sudo chown $(id -u):$(id -g) $HOME/.kube/config; kubectl get nodes;

#sudo kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
sudo kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/v0.9.1/Documentation/kube-flannel.yml
```

kubectl taint nodes --all node-role.kubernetes.io/master-

1 node(s) didn't match node selector, 1 node(s) had taints that the pod didn't tolerate.


## On Node

```bash
sudo kubeadm join XXX
```


