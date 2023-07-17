---
title: "Working with Namespaces and Services in Kubernetes"
datePublished: Sat Jul 01 2023 17:31:50 GMT+0000 (Coordinated Universal Time)
cuid: cljka60l0000109l5az2j3sfl
slug: working-with-namespaces-and-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688232628057/7a66e9d2-e952-4350-88a6-1954656d264a.png
tags: opensource, kubernetes, learning, devops, 90daysofdevops

---

### **What are Namespaces and Services in Kubernetes**

**<mark>Namespaces:</mark>** In Kubernetes, Namespaces are like virtual clusters within a physical cluster. They help you organize and separate different applications or teams by providing a way to group resources together. It's like having separate rooms or compartments in a shared space.

For example, imagine you have a big building with multiple floors. Each floor represents a Namespace, and each room on that floor represents a resource, such as a pod or a service. Namespaces provide isolation and prevent resources in one Namespace from interfering with resources in another Namespace. They help you keep things organized and manageable.

**<mark>Services:</mark>** In Kubernetes, Services are like the front doors to your applications. They provide a way for other applications or users to access and communicate with your applications running inside pods.

Think of a Service as a reception desk in a building. When someone wants to visit a specific department or office, they go to the reception desk, and the receptionist directs them to the right place. Similarly, a Service acts as a central point of access to your application, regardless of which pod the application is running on.

Services help in two main ways:

1. **<mark>Load Balancing:</mark>** When multiple pods run your application, a Service distributes incoming requests evenly across those pods. It ensures that the load is distributed well, like having multiple receptionists handle visitors.
    
2. **<mark>Service Discovery:</mark>** Services provide a fixed and reliable way to access your application. Even if pods come and go or scale up and down, the Service maintains a stable network address. It's like having a directory or map at the reception desk that helps visitors find the right place.
    

By using Namespaces and Services in Kubernetes, you can keep your applications organized and separate them based on teams, projects, or any other criteria. Services provide a consistent way to access and communicate with your applications, making them reliable and scalable.

---

## Task 1:

* **Create a Namespace for your Deployment**
    

1. Open a terminal or command prompt.
    
2. Use the following command to create a Namespace:
    

```yaml
kubectl create namespace <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688194987363/956c022c-1369-4b7e-a56c-22df6ba41100.png align="center")

* **Update the deployment.yml file to include the Namespace**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688195190098/ae319852-d8ca-4386-9f5b-9d12c4a6fd6f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688195245048/e592186c-2c31-41e2-b8b9-fb7aec1a60ec.png align="center")

* **Apply the updated deployment using the command:** `kubectl apply -f deployment.yml`
    

```yaml
kubectl apply -f deployment.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688195323747/09642875-ec58-49a4-a1e9-2ab908037c97.png align="center")

* **Verify that the Namespace has been created by checking the status of the Namespaces in your cluster.**
    

```yaml
kubectl get pods -n=<namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688195373313/e9f77f21-9cd8-4e60-9871-2b497bb0a950.png align="center")

---

## Task 2:

### **Services, Load Balancing, and Networking in Kubernetes**

**<mark>Services:</mark>** In Kubernetes, a Service is an abstraction that represents a set of pods and provides a consistent way to access and communicate with those pods. It acts as a stable network endpoint for other applications or users to interact with your application running inside the pods.

Think of a Service as the front door to your application. It allows incoming traffic to be directed to the appropriate pods that are running your application, regardless of their actual IP addresses or locations.

**<mark>Load Balancing:</mark>** Load balancing is a key feature provided by Services in Kubernetes. When you have multiple pods running your application, the Service automatically distributes incoming network traffic across those pods in a balanced manner.

Imagine a busy restaurant with multiple chefs in the kitchen. Instead of all the customers going to a specific chef, a waiter ensures that the load is distributed evenly among the available chefs. Similarly, a Service evenly distributes incoming requests across multiple pods running your application, ensuring efficient utilization of resources and providing better performance.

**<mark>Networking:</mark>** Networking in Kubernetes deals with how pods and Services communicate with each other within the cluster.

Each pod in Kubernetes is assigned a unique IP address. Pods can communicate with each other using these IP addresses, even if they are running on different nodes within the cluster.

Services, on the other hand, have their own IP addresses too. These IP addresses are stable and independent of the individual pods behind the Service. When other applications or users want to access your application, they can use the IP address of the Service.

Think of pods as individual members of a team, each with its own internal phone extension, and the Service as the main phone number for external callers. The Service routes incoming calls to the appropriate pods, ensuring seamless communication and interaction.

In summary, Services in Kubernetes provide a stable network endpoint for accessing your application, while load balancing ensures that incoming traffic is evenly distributed across the pods running your application. Networking handles the communication between pods and Services, allowing seamless connectivity within the cluster. These features help make applications in Kubernetes scalable, reliable, and easily accessible.

---

In Kubernetes, there are several types of Services available to meet different networking requirements. The common types of Services are:

1. **<mark>ClusterIP</mark>:** This is the default type of Service. It provides a stable internal IP address that is accessible only within the cluster. It allows communication between different services/pods within the same cluster. ClusterIP Services are not accessible from outside the cluster.
    
2. **<mark>NodePort: </mark>** A NodePort Service exposes the Service on a static port on each node in the cluster. It creates a network route from the cluster's external IP address to the Service. Incoming traffic on the specified port is forwarded to the Service, which in turn routes it to the appropriate pods. NodePort Services are accessible externally using the node's IP address and the NodePort.
    
3. **<mark>LoadBalancer:</mark>** A LoadBalancer Service automatically provisions an external load balancer (such as a cloud load balancer) to distribute traffic to the Service. It receives a unique external IP address that acts as an entry point for external traffic. LoadBalancer Services are typically used in cloud environments to expose applications to the internet. The actual implementation of the load balancer depends on the underlying cloud provider.
    
4. **<mark>ExternalName:</mark>** An ExternalName Service maps the Service to a DNS name rather than an IP address. It is used for integrating with external services outside the cluster. When accessing the Service, the DNS resolution is performed to obtain the external name mapped to the Service.
    

Additionally, there are other advanced types of Services available in Kubernetes, including:

1. **<mark>Headless:</mark>** A Headless Service is used when you don't need load balancing or a stable IP. It allows direct DNS-based access to individual pods within a Service.
    
2. **<mark>Ingress:</mark>** An Ingress is not a Service type itself, but it provides external access to Services in a more advanced and flexible way. It acts as an API gateway or entry point to the cluster, allowing you to define routing rules, SSL termination, and more.
    

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**