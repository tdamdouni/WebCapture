# How to Install and Deploy Kubernetes on Ubuntu 16.04

_Captured: 2018-06-26 at 19:28 from [dzone.com](https://dzone.com/articles/how-to-install-and-deploy-kubernetes-on-ubuntu-160-1?edition=383261&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-06-26)_

## Introduction

Kubernetes is an open-source container management system for automating deployment, scaling, and management of containerized applications. Kubernetes is absolutely free and open source, so it gives you the freedom to take advantage of on-premises, hybrid, or public cloud infrastructure, letting you effortlessly move workloads to where it matters to you. Kubernetes was originally designed by Google and maintained by the Cloud Native Computing Foundation. Kubernetes is quickly becoming the new standard for deploying and managing software in the cloud, and provides a platform for automating deployment, scaling, and operations of application containers across clusters of hosts. It helps you to run containerized applications whenever you want. Kubernetes follows the master-slave architecture, where it has a master that provides centralized control for an all agents. Kubernetes has several components, including: etcd, flannel, kube-apiserver, kube-controller-manager, kube-scheduler, kubelet, kube-proxy, docker and much more.

In this tutorial, we are going to set up multi-node Kubernetes Cluster on Ubuntu 16.04 server.

## Requirements 

  * Two fresh Alibaba cloud instance with Ubuntu 16.04 server installed.

  * A static IP address 192.168.0.103 is configured on the first instance (Master) and 192.168.0.104 is configured on the second instance (Slave).

  * Minimum 2GB RAM per instance.

  * A Root password is set up on each instance.

## Launch Alibaba Cloud ECS Instance

First, login to your _[Alibaba Cloud ECS Console](https://account.alibabacloud.com/login/login.htm?oauth_callback=https://ecs.console.aliyun.com/?spm=a3c0i.o25424en.a3.13.388d499ep38szx)_ . Create a new _[ECS instance](https://www.alibabacloud.com/help/doc-detail/25424.htm?spm=a3c0i.11021464.a2c1b31.19.591117b7KqwrtY)_ , choosing Ubuntu 16.04 as the operating system with at least 2GB RAM. Connect to your _[ECS instance](https://www.alibabacloud.com/help/doc-detail/25434.htm?spm=a3c0i.11021464.a2c1b31.20.591117b7KqwrtY)_ and log in as the root user.

Once you are logged into your Ubuntu 16.04 instance, run the following command to update your base system with the latest available packages.

## Getting Started

Before starting, you will need to configure hosts file and hostname on each server, so each server can communicate with each other using the hostname.

First, open /etc/hosts file on the first server:

Add the following lines:

Save and close the file when you are finished, then setup hostname by running the following command:

Next, open /etc/hosts file on the second server:

Add the following lines:

Save and close the file when you are finished, then setup hostname by running the following command:

Next, you will need to disable swap memory on each server. Because kubelets do not support swap memory and will not work if swap is active or even present in your /etc/fstab file.

You can disable swap memory usage with the following command:

You can disable this permanent by commenting out the swap file in /etc/fstab:

Comment out the swap line as shown below:

Save and close the file, when you are finished.

## Install Docker

Before starting, you will need to install Docker on both the master and slave server. By default, the latest version of the Docker is not available in Ubuntu 16.04 repository, so you will need to add Docker repository to your system.

First, install required packages to add Docker repository with the following command:

Next, download and add Docker's GPG key with the following command:

Next, add Docker repository with the following command:

Next, update the repository and install Docker with the following command:

## Install Kubernetes

Next, you will need to install kubeadm, kubectl and kubelet on both the server. First, download and GPG key with the following command:

Next, add Kubernetes repository with the following command:

Finally, update the repository and install Kubernetes with the following command:

## Configure Master Node

All the required packages are installed on both servers. Now, it's time to configure Kubernetes Master Node.

First, initialize your cluster using its private IP address with the following command:

You should see the following output:

**Note :** Note down the token from the above output. This will be used to join Slave Node to the Master Node in the next step.

Next, you will need to run the following command to configure kubectl tool:

Next, check the status of the Master Node by running the following command:

You should see the following output:

In the above output, you should see that Master Node is listed as not ready. Because the cluster does not have a Container Networking Interface (CNI).

Let's deploy a Calico CNI for the Master Node with the following command:

Make sure Calico was deployed correctly by running the following command:

You should see the following output:

Now, run the `kubectl get nodes` command again, and you should see the Master Node is now listed as Ready.

Output:

## Add Slave Node to the Kubernetes Cluster

Next, you will need to log in to the Slave Node and add it to the Cluster. Remember the join command in the output from the Master Node initialization command and issue it on the Slave Node as shown below:

Once the Node is joined successfully, you should see the following output:

Now, go back to the Master Node and issue the command kubectl get nodes to see that the slave node is now ready:

Output:

## Deploy the Apache container to the Cluster

Kubernetes Cluster is now ready, it's time to deploy the Apache container.

On the Master Node, run the following command to create an Apache deployment:

Output:

You can list out the deployments with the following command:

Output :

You can see more information about Apache deployment with the following command:

Output:

Next, you will need to make the Apache container available to the network with the command:

Now, list out the current services by running the following command:

You should see the Apache service with assigned port 30267:

Now, open your web browser and type the URL http://192.168.0.104:30267 (Slave Node IP). You should see the default Apache Welcome page:

![Image title](https://dzone.com/storage/temp/9458019-page1.png)

Congratulations! Your Apache container has been deployed on your Kubernetes Cluster.
