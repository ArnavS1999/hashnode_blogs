---
title: "Kubernetes Architecture"
datePublished: Tue Jun 13 2023 18:46:55 GMT+0000 (Coordinated Universal Time)
cuid: cliumx8s2000609if1b1d5jp2
slug: kubernetes-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686681920505/cee02be9-3933-44b2-810c-735a18785dbe.png
tags: kubernetes, devops, k8s, 90daysofdevops, trainwithshubham

---

### Kubernetes Overview

With the widespread adoption of [containers](https://cloud.google.com/containers) among organizations, Kubernetes, the container-centric management software, has become a standard to deploy and operate containerized applications and is one of the most important parts of DevOps.

Unleash the potential of Kubernetes, the leading open-source container orchestration system. Simplify deployment, scaling, and management of applications with Kubernetes. Harness the agility and flexibility of containers to optimize your cloud-native infrastructure. Enhance collaboration, automate workflows, and ensure high availability with this powerful platform. Experience the future of containerized deployments with Kubernetes.

---

### **<mark>1-&gt; </mark>** What is Kubernetes?

Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform that simplifies the management and scaling of containerized applications. It automates various tasks, such as deployment, scaling, load balancing, and container distribution across clusters of machines. With its robust features and flexibility, Kubernetes enables organizations to efficiently manage and streamline their container-based workflows. Its name, K8s, stems from the fact that there are eight letters between the "K" and "s" in **<mark>"Kubernetes."</mark>** Embracing Kubernetes empowers businesses to achieve seamless application deployment, enhanced scalability, and improved resource utilization in today's dynamic, cloud-native environments.

OR

A powerful open-source beast that tames the wild containers. It orchestrates their every move, automating deployment, scaling, and management like a true magician. With Kubernetes, you can create armies of containers, effortlessly ensuring they play nice, stay available, and flex their muscles when needed. It's like having a personal assistant for your containers, making them dance to your command while optimizing resources.

---

### <mark>2-&gt;</mark> What are the benefits of using k8s?

Kubernetes (K8s) provides several advantages. It simplifies the process of deploying and managing applications. With K8s, you can easily scale your applications based on demand, ensuring efficient resource usage. It also improves the availability of your applications and makes them more resilient to failures. Overall, Kubernetes helps you streamline your application management and create more robust and scalable environments.

---

### **<mark>3-&gt; </mark>** Explain the architecture of Kubernetes.

![](https://1.bp.blogspot.com/-kCijQkEkmA8/X9ctU83lcJI/AAAAAAAAF5U/GayBI9yQ-PsUuGI9L4Mf8dJwsByp6g8WQCLcBGAsYHQ/s1192/k8%2Barchitecture.PNG align="left")

1. **<mark>Master Node:</mark>** Kubernetes architecture starts with the master node, which acts as the control plane for the cluster. It includes several components:
    
    * **<mark>API Server:</mark>** Exposes the Kubernetes API for managing and controlling the cluster.
        
    * **<mark>Scheduler:</mark>** Assigns workloads to worker nodes based on available resources and scheduling policies.
        
    * **<mark>Controller Manager:</mark>** Monitors the cluster's state, manages to scale, and handles various background tasks.
        
    * **<mark>etcd:</mark>** A distributed key-value store that securely stores the cluster's configuration data.
        
2. **<mark>Worker Nodes:</mark>** These are the machines where your applications run inside containers. Worker nodes have the following components:
    
    * **<mark>Kubelet:</mark>** Acts as an agent on the worker node, responsible for communication with the master node and managing containers.
        
    * **<mark>Container Runtime:</mark>** The software responsible for running containers, such as Docker or containerd.
        
    * **<mark>Kube Proxy:</mark>** Manages network routing and load balancing between services.
        
3. **<mark>Pod:</mark>** The basic scheduling unit in Kubernetes is a Pod, which represents one or more containers deployed together on a single worker node. Pods share the same network and storage resources.
    
4. **<mark>Service:</mark>** A Service is an abstraction that provides a stable network endpoint to access a group of Pods. It allows you to expose your applications internally or externally.
    
5. **<mark>Ingress:</mark>** An Ingress is an API object that manages external access to services within the cluster. It provides routing rules and load balancing for incoming traffic.
    

---

### **<mark>4-&gt; </mark>** What is Control Plane?

The Control Plane in Kubernetes is the central management component responsible for overseeing and controlling the cluster's operations. It consists of various components that enable efficient management and coordination of containerized applications. The Control Plane includes the API server, which serves as the entry point for managing the cluster through the Kubernetes API. It also comprises the Scheduler, Controller Manager, and etcd, a distributed key-value store that securely stores the cluster's configuration data. The Control Plane ensures scalability, fault tolerance, and high availability, allowing you to effectively manage and orchestrate your applications in a Kubernetes environment.

---

### **<mark>5-&gt; </mark>** Write the difference between kubectl and kubelets.

**<mark>kubectl:</mark>**

* CLI tool to manage Kubernetes clusters from a local machine.
    
* Deploy, manage, and monitor applications using kubectl commands.
    
* Scale deployments, update configurations, and view cluster resources.
    
* Retrieve logs, debug, and inspect the cluster's state with kubectl.
    
* Interact with the Kubernetes control plane for administrative tasks.
    

**<mark>kubelet:</mark>**

* The agent runs on each worker node in the Kubernetes cluster.
    
* Manages containers on the node according to the control plane's instructions.
    
* Communicates with the container runtime (e.g., Docker) to start, stop, and manage containers.
    
* Monitors container health and reports back to the control plane.
    
* Ensures containers run as per the desired state defined by the control plane.
    

---

### **<mark>6-&gt; </mark>** Explain the role of the API server.

The API server serves as the central control point in Kubernetes, managing the cluster's API, handling resource requests, and enforcing security. It validates incoming requests, stores the cluster's state, and supports extensibility and scalability. It acts as the primary interface for communication and plays a crucial role in managing and controlling the Kubernetes cluster effectively and securely.

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**