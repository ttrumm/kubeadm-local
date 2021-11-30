# README

This version installs kubernetes 1.20.13-0, for different version change kubelet/kubeadm version in ```install.sh```

!!Sorry!! im still based on Docker

## Create vm-s

```vagrant up```

## ssh into vms

```
vagrant ssh node1
vagrant ssh node2
vagrant ssh node3
```

## Remove vm-s
```vagrant destroy -f```


# Init cluster

## Master node

```kubeadm init --token-ttl=0 --apiserver-advertise-address=172.17.8.101 --pod-network-cidr=172.17.0.0/16 --apiserver-cert-extra-sans=node1,172.17.8.101 --ignore-preflight-errors=NumCPU```

```mkdir -p .kube && cp -i /etc/kubernetes/admin.conf /root/.kube/config```

```wget https://github.com/weaveworks/weave/releases/download/v2.7.0/weave-daemonset-k8s-1.11.yaml```

```kubectl apply -f weave-daemonset-k8s-1.11.yaml```


## Worker node

