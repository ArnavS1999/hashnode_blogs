---
title: "Working with Services in Kubernetes"
datePublished: Sat Jul 01 2023 17:34:53 GMT+0000 (Coordinated Universal Time)
cuid: cljka9x7q000109l2gkem9cpj
slug: working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688232857002/909e82b1-6e40-471f-9dae-a2ae16d19b35.png
tags: opensource, kubernetes, learning, devops, 90daysofdevops

---

## What are Services in K8s

In Kubernetes, a Service is a method for exposing a network application that is running as one or more [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) in your cluster.

**OR**

In Kubernetes, Services are objects that provide stable network identities to Pods and abstract away the details of Pod IP addresses. Services allow Pods to receive traffic from other Pods, Services, and external clients.

Imagine you have a group of pods running your application, and you want other applications or users to be able to interact with it. Services provide a consistent and stable way for them to do that.

Think of a Service as a reception desk in a building. When someone wants to visit a specific department or office, they go to the reception desk, and the receptionist directs them to the right place. Similarly, a Service acts as a central point of access to your application.

![Kubernetes: part 1 – architecture and main components overview](https://rtfm.co.ua/wp-content/uploads/2019/07/Screenshot_20190722_110641.png align="left")

**NodePort** Service in Kubernetes is a way to make your application accessible from outside the cluster. It allows external traffic to reach your application by opening a specific port on all the nodes in the cluster.

Here's how it works:

1. You create a NodePort Service and specify the port you want to use for external access.
    
2. Kubernetes opens that specified port on each node in the cluster.
    
3. When an external request arrives at any node's IP address on that port, Kubernetes routes the traffic to the Service.
    
4. The Service, in turn, forwards the traffic to the pods running your application.
    

It's like having multiple doors to your application, with each door (node) listening on the same specified port. When someone accesses any of those doors from outside, the request is directed to your application running in the pods.

## Task-1:

* ### **Create a Service for your todo-app Deployment from Day-32**
    
* ### **Create a Service definition for your todo-app Deployment in a YAML file.**
    

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-django-service
  namespace: my-todo-app
spec:
  type: NodePort
  selector:
    app: todo-app
  ports:
      # By default and for convenience, the `targetPort` is set to the same value as the `port` field.
    - port: 80
      targetPort: 8000
      # Optional field
      # By default and for convenience, the Kubernetes control plane will allocate a port from a range (default: 30000-32767)
      nodePort: 30015
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688198590823/537f5ec4-bd9f-4675-8418-b986202d6729.png align="center")

* **Apply the Service definition to your K8s cluster using the** `kubectl apply -f service.yml -n <namespace-name>` **command.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688198941203/e4e4fe83-bf59-49d8-b825-e7e58d1efba8.png align="center")

* **Verify that the Service is working by accessing the todo-app using the Service's IP and Port in your Namespace.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688200774125/08b31ce4-dbe1-4fef-a3cd-78657b2ae283.png align="center")

---

## Task-2:

* ### **Create a ClusterIP Service for accessing the todo-app from within the cluster.**
    
* ### **Create a ClusterIP Service definition for your todo-app Deployment in a YAML file.**
    

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-django-app-cluster
  namespace: my-todo-app
spec:
  type: ClusterIP
  selector:
    app: todo-app
  ports:
    - name: http
      protocol: TCP
      port: 8000
      targetPort: 8000
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214039385/fc48358a-bc6a-4b42-9f84-f59f570f317c.png align="center")

* **Apply the ClusterIP Service definition to your K8s cluster using the** `kubectl apply -f cluster-ip-service.yml -n <namespace-name>` **command.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214122874/b403bd0d-e140-40b7-9f2e-91b160b125d2.png align="center")
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214159022/79236198-6f8d-4d39-a387-c90f54a8ca6e.png align="center")

* **Verify that the ClusterIP Service is working by accessing the todo-app from another Pod in the cluster in your Namespace.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214282372/009258b0-2137-45d7-8334-c024605df1b4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214339532/60fe0855-0eb6-4926-921d-df4d8f1b33e7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214392982/425203d6-41c4-44b0-b19a-341bea8fd1fe.png align="center")

Now we can say that ClusterIP Service is working by accessing the todo-app from another Pod in the cluster in your Namespace.

## Task-3:

* ### **Create a LoadBalancer Service for accessing the todo-app from outside the cluster**
    
* ### **Create a LoadBalancer Service definition for your todo-app Deployment in a YAML file.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214764865/6e603e86-98d4-4113-821b-68d578732066.png align="center")

* **Apply the LoadBalancer Service definition to your K8s cluster using the** `kubectl apply -f load-balancer-service.yml -n <namespace-name>` **command.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214826571/83757d52-dff3-485c-a06d-c9b0f5ef40b4.png align="center")

* **Verify that the LoadBalancer Service is working by accessing the todo-app from outside the cluster in your Namespace.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688214892319/ab030487-1afe-4351-afe5-17b0cd7ad316.png align="center")
    
    ---
    

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**