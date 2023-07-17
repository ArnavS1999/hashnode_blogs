---
title: "Managing Persistent Volumes in Your Deployment"
datePublished: Sat Jul 01 2023 17:44:01 GMT+0000 (Coordinated Universal Time)
cuid: cljkalong000409mgdypcgapw
slug: managing-persistent-volumes-in-your-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688233416762/62215571-5633-4b1d-a881-eca29db5d802.png
tags: opensource, kubernetes, learning, devops, 90daysofdevops

---

### **Volume in k8s.**

In Kubernetes, a volume is a way to provide storage to containers running within a pod. It allows data to be shared and persisted across pod restarts or rescheduling.

Volumes in Kubernetes can be thought of as directories that exist within the pod's filesystem, separate from the container's own filesystem. They provide a way to store and access data that needs to be shared between containers within the same pod or preserved even when the pod is terminated and recreated.

In Kubernetes, there are several types of volumes available to provide storage to containers within pods. Here are some commonly used volume types:

1. **<mark>EmptyDir:</mark>** An EmptyDir volume is created empty when a pod is created and exists for the lifetime of that pod. It is designed for storing temporary data that is tied to the pod. The data in an EmptyDir volume is deleted when the pod is terminated or restarted.
    
2. **<mark>HostPath:</mark>** A HostPath volume mounts a file or directory from the host node's filesystem into the pod. It allows containers to access files on the host node's filesystem. This volume type can be useful when you need to share files between containers on the same host or access host-specific resources.
    
3. **<mark>PersistentVolumeClaim (PVC):</mark>** A PersistentVolumeClaim is used to request a specific amount and type of storage from a PersistentVolume (PV). PVs and PVCs enable separation between storage provisioning and application deployment. PVCs can be used to bind to available PVs, which provide durable and shared storage across pod restarts.
    
4. **<mark>ConfigMap:</mark>** A ConfigMap volume allows you to inject configuration data, such as environment variables or configuration files, into containers within a pod. It is suitable for providing configuration data to applications without hardcoding it in the container image or deployment configuration.
    
5. **<mark>Secret:</mark>** A Secret volume is used to securely provide sensitive data, such as passwords, API keys, or TLS certificates, to containers within a pod. Secrets are stored securely within Kubernetes and can be mounted as files or exposed as environment variables to the container.
    
6. **<mark>NFS:</mark>** NFS (Network File System) is a volume type that allows you to mount an NFS share from a remote server into a pod. It enables sharing and accessing files across multiple pods and nodes within a Kubernetes cluster.
    
7. **<mark>CSI (Container Storage Interface) volumes:</mark>** CSI volumes provide a standardized way to integrate external storage systems with Kubernetes. They allow you to use various storage solutions, such as cloud storage, block storage, or distributed file systems, as volumes in your pods.
    

### **What are Persistent Volumes in k8s**

Persistent Volumes (PVs) in Kubernetes are a way to provide durable storage to applications running within a cluster.

Think of Persistent Volumes as a shared storage pool that is independent of any specific pod or container. It acts as a persistent storage resource that can be dynamically provisioned or statically configured and then bound to a Persistent Volume Claim (PVC), which is used by pods to request storage.

**<mark>Here's how it works:</mark>**

1. Persistent Volumes are created by cluster administrators or dynamically provisioned by storage classes. They represent a piece of storage that can be utilized by applications.
    
2. Persistent Volume Claims (PVCs) are created by application developers or administrators to request a specific amount and type of storage. PVCs act as a request for a Persistent Volume that meets the specified requirements.
    
3. When a PVC is created, Kubernetes finds an appropriate Persistent Volume that matches the requested size, access mode, and other criteria. If a suitable Persistent Volume is found, it is bound to the PVC.
    
4. Once a PVC is bound to a Persistent Volume, the pod can use that PVC to access the storage. The pod can mount the Persistent Volume as a directory and read from or write to it, just like any other filesystem.
    

The benefits of using Persistent Volumes include:

* **<mark>Persistence:</mark>** The data stored in a Persistent Volume remains intact even if the pod or container is restarted, rescheduled, or terminated. This enables applications to store and retrieve data reliably.
    
* **<mark>Portability:</mark>** Persistent Volumes can be used by multiple pods across different nodes within the cluster. This allows data to be shared and accessed by multiple applications or replicas of the same application.
    
* **<mark>Dynamic Provisioning:</mark>** Kubernetes can automatically provision Persistent Volumes based on the storage requirements defined in PVCs. This simplifies storage management and eliminates the need for manual provisioning.
    

### **Task 1:**

**Add a Persistent Volume to your Deployment todo app.**

* ### **Create a Persistent Volume using a file on your node.**
    

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-todo-app
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: "/tmp/data"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688228984243/f4f9a9cc-5021-4fe3-958c-af4afb6ab69a.png align="center")

**<mark>The </mark>** `persistentVolumeReclaimPolicy` **<mark>is set to "Retain", which means the PV will not be automatically deleted when released</mark>**

* **Create a Persistent Volume Claim that references the Persistent Volume.**
    

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-todo-app
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 500Mi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688229103235/c1e5e0e2-a371-45ad-9d66-48b4159a4c02.png align="center")

* **Update your deployment.yml file to include the Persistent Volume Claim. After Applying pv.yml pvc.yml your deployment file.**
    

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: todo-app
  template:
    metadata:
      labels:
        app: todo-app
    spec:
      containers:
        - name: todo-app
          image: trainwithshubham/django-todo
          ports:
            - containerPort: 8000
          volumeMounts:
            - name: todo-app-data
              mountPath: /app
      volumes:
        - name: todo-app-data
          persistentVolumeClaim:
            claimName: pvc-todo-app
```

* **Apply the updated deployment using the command:** `kubectl apply -f deployment.yml`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688229345512/b5c0f688-c221-4888-8e75-27179fee9e7a.png align="center")

* **Verify that the Persistent Volume has been added to your Deployment by checking the status of the Pods and Persistent Volumes in your cluster. Use this commands** `kubectl get pods,kubectl get pv.`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688229616126/9820e9bb-cafc-4a2b-9f96-ec4e1d3fb757.png align="center")

### **Task 2:**

**Accessing data in the Persistent Volume,**

* ### **Connect to a Pod in your Deployment using the command : kubectl exec -it -- /bin/bash**
    
* ### **Verify that you can access the data stored in the Persistent Volume from within the Pod**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688230808727/f77e83b4-c228-4f3b-a25e-e9108d5a4882.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**