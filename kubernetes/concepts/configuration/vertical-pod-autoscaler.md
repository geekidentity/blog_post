---
categories: Kubernetes

tags: 
  - k8s
  - Kubernetes


title: Pod 垂直扩缩容

date: 2018-11-22

---

# Pod 垂直扩缩容

## 简介

Vertical Pod Autoscaler (VPA) 使用户不需要更新 Pod 中容器资源请求。配置好后，它将根据使用情况自动设置请求，从而允许在节点上进行适当的调度，以便为每个pod提供适当的资源量。

它既可以缩小容器过度请求的资源，也可以根据其使用情况随着时间的推移逐步扩展容器请求的资源。

Autoscaling 使用名为 VerticalPodAutoscaler 的自定义资源定义对象配置。 它允许指定垂直自动扩缩容的 pod 以是否以及如何应用资源。

要在群集上启用垂直pod自动扩缩容，请按照下面介绍的安装步骤进行操作。

## 安装

