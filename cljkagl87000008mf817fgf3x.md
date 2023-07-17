---
title: "Mastering ConfigMaps and Secrets in Kubernetes"
datePublished: Sat Jul 01 2023 17:40:04 GMT+0000 (Coordinated Universal Time)
cuid: cljkagl87000008mf817fgf3x
slug: mastering-configmaps-and-secrets-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688233164805/69c20625-ecf3-4161-b1b2-5285ef658ff2.png
tags: opensource, kubernetes, learning, devops, 90daysofdevops

---

### **What are ConfigMaps and Secrets in k8s**

ConfigMaps and Secrets in Kubernetes are used to manage and provide configuration data to applications running within a cluster.

**<mark>ConfigMaps:</mark>** ConfigMaps is a way to store and manage configuration data in Kubernetes. They allow you to decouple the configuration from the application code, making it easier to manage and update configurations without modifying the application itself. ConfigMaps can store key-value pairs or configuration files and are typically used for non-sensitive data, such as environment variables, command-line arguments, or configuration files needed by your application.

**<mark>Secrets: </mark>** Secrets are similar to ConfigMaps, but they are specifically designed for storing sensitive information, such as passwords, API keys, or TLS certificates. Secrets are encoded and stored securely within Kubernetes. They can be used to provide sensitive data to your applications without exposing them directly in the deployment configuration or source code. Secrets can be mounted as files or exposed as environment variables within the application's containers.

Both ConfigMaps and Secrets are created using YAML definitions and can be referenced within your application's deployment configuration. They provide a way to manage and propagate configuration data and sensitive information to your applications consistently across the Kubernetes cluster.

**<mark>Example:-</mark>** *Imagine you're in charge of a big spaceship (Kubernetes cluster) with lots of different parts (containers) that need the information to function properly. ConfigMaps are like a file cabinet where you store all the information each part needs in simple, labeled folders (key-value pairs). Secrets, on the other hand, are like a safe where you keep important, sensitive information that shouldn't be accessible to just anyone (encrypted data). So, using ConfigMaps and Secrets, you can ensure each part of your spaceship (Kubernetes cluster) has the information it needs to work properly and keep sensitive information secure!*

## Task 1:

* ### **Create a ConfigMap for your Deployment**
    
* ### **Create a ConfigMap for your Deployment using a file or the command line**
    

```yaml
kind: ConfigMap
apiVersion: v1
metadata:
  name: mysql-config
  labels:
    app: todo-app
  namespace: my-todo-app 
data:
  MYSQL_DB: "todo-db"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688222748627/544d74d8-5dfc-473a-b45d-436a4c869f48.png align="center")

* **Apply the updated deployment using the command:** `kubectl apply -f deployment.yml -n <namespace-name>`
    

```yaml
kubectl apply -f config.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688222551382/26c6fb9c-c5b1-459c-aa50-e7b8cff2ced8.png align="center")

* **Verify that the ConfigMap has been created by checking the status of the ConfigMaps in your Namespace.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688222811059/bd6c544c-5a27-439a-8afc-5f69ad7db906.png align="center")

---

## Task 2:

* ### **Create a Secret for your Deployment**
    
* ### **Create a Secret for your Deployment using a file or the command line**
    

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: mysql-secret
  namespace: my-todo-app
type: Opaque
data:
  password: QXJuYXZkZXZvcHMK
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688223112917/be7fe2d8-c276-478d-84a7-5b374568172c.png align="center")

* **We can Encode & decode the Base64 key by ourselves.**
    

```yaml
# To Decode Base64 key
  echo "QXJuYXZkZXZvcHMK" | base64 --decode

# To Encode Base64 key
  echo "Arnavdevops" | base64
```

* **Apply the updated deployment using the command:** `kubectl apply -f deployment.yml -n <namespace-name>`
    

```yaml
kubectl apply -f secret.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688223157126/241e3995-5bd9-4056-882a-42eb78d74a27.png align="center")

* **Verify that the Secret has been created by checking the status of the Secrets in your Namespace.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688223331175/4bd657ea-4645-40fc-93e4-42a983843e43.png align="center")

### **Now update the deployment.yml file to include the configMap & Secret**

1. **Now update the deployment.yml file to include the configMap & Secret**
    

```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: mysql
    labels:
      app: mysql
    namespace: my-todo-app
  spec:
    replicas: 3
    selector:
      matchLabels:
        app: mysql
    template:
      metadata:
        labels:
          app: mysql
      spec:
        containers:
        - name: mysql
          image: mysql:8
          ports:
          - containerPort: 3306
          env:
          - name: MYSQL_ROOT_PASSWORD
            valueFrom:
              secretKeyRef:
                name: mysql-secret
                key: password
          - name: MYSQL_DATABASE
            valueFrom:
              configMapKeyRef:
                name: mysql-config
                key: MYSQL_DB
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688223969411/66c36a0a-d1ed-4a18-bbfe-68072021d257.png align="center")

1. **Apply the updated deployment using the command**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688224113276/8c0ac2cc-d0b7-46e0-92cb-177501e55efc.png align="center")

1. **verify whether the pods running or not by running the below command**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688224172140/6e7af172-e5f6-4ec9-9ca8-61fa0bb18143.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**