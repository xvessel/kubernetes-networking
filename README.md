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


实现方式：

### userspace proxy mode

Since Kubernetes v1.0 you have been able to use the userspace proxy mode.

![user space proxy mode](https://d33wubrfki0l68.cloudfront.net/e351b830334b8622a700a8da6568cb081c464a9b/13020/images/docs/services-userspace-overview.svg)

### iptables proxy mode

Kubernetes v1.1 added iptables mode proxying, and in Kubernetes v1.2 the iptables mode for kube-proxy became the default. 

![iptables proxy mode](https://d33wubrfki0l68.cloudfront.net/27b2978647a8d7bdc2a96b213f0c0d3242ef9ce0/e8c9b/images/docs/services-iptables-overview.svg)

### IPVS proxy mode

Kubernetes v1.8 added ipvs proxy mode.

![IPVS proxy mode](https://d33wubrfki0l68.cloudfront.net/2d3d2b521cf7f9ff83238218dac1c019c270b1ed/9ac5c/images/docs/services-ipvs-overview.svg)














