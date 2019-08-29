# kubernetes networking

refer: 

- https://kubernetes.io/docs/concepts/cluster-administration/networking/
- https://kubernetes.io/docs/concepts/services-networking/service/

总结如下：

## 1. pod 内 

- every Pod gets its own IP address.
- containers within a Pod share their network namespaces - including their IP address

## 2. pod 与 pod, pod 与 node

- pods on a node can communicate with all pods on all nodes without NAT
- agents on a node (e.g. system daemons, kubelet) can communicate with all pods on that node
- pods in the host network of a node can communicate with all pods on all nodes without NAT

[The Kubernetes network model] 的核心内容, 有很多第三方实现。

安装并使用以下实现：

- [flannel](./flannel/README.md)
- [calico](./calico/README.md)

## 3. services

service: Kubernetes gives Pods their own IP addresses and a single DNS name for a set of Pods, and can load-balance across them.

Pod-to-Service communications: this is covered by services.

External-to-Service communications: this is covered by services.















