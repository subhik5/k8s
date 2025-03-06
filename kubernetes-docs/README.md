

# k8s
about kubernetes



### **What is Ingress in Kubernetes?**  
Imagine you have a **big house** (your Kubernetes cluster), and inside, you have **many rooms** (your applications or services). Now, people (users) from outside want to visit different rooms.  

But there's a problem! 🚪  
Your house has **only one main gate**, and visitors don’t know how to reach the right room inside.  

This is where **Ingress** comes in! 🎉  
Ingress is like a **smart security guard** standing at the gate. When a visitor comes and asks,  
"Hey, I want to go to Room A," the guard (Ingress) checks the rules and **guides them** to the correct room.  



### **How Does Ingress Work?**  
- Without Ingress, each room (application) would need a separate door (IP address), which is confusing!  
- Ingress allows you to use **one main door (single IP)** but still send visitors to the right place inside.  



### **Example of Ingress in Kubernetes**  
Let’s say you have **two applications** running in Kubernetes:  
1. **Online Shop** → `shop.example.com` 🛒  
2. **Blog** → `blog.example.com` ✍️  

Now, instead of opening two separate doors, we use **Ingress** like this:

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
  namespace: online-shop
spec:
  rules:
  - host: shop.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: shop-service
            port:
              number: 80

  - host: blog.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: blog-service
            port:
              number: 80
```



### **What’s Happening Here?**  
- When someone visits **shop.example.com**, Ingress will send them to the **shop-service** 🛒  
- When someone visits **blog.example.com**, Ingress will send them to the **blog-service** ✍️  

Now, everything is handled by **one main door** but people still reach the right place inside! 🚀  



### **Why Use Ingress?**  
✔ **One entry point** instead of many IPs  
✔ **Easier to manage traffic**  
✔ **Can handle HTTPS (SSL) for security**  

So, Ingress is like a **smart gatekeeper** for your Kubernetes applications!
 
=======
 Documentation

## Introduction

Kubernetes (K8s) is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It is widely used in DevOps workflows to ensure application reliability and scalability.

## What is Kubernetes?
Kubernetes is a system that helps manage applications that are packaged in containers (such as Docker). It allows you to deploy these applications across multiple machines, scale them up or down as needed, and handle failures automatically.

Instead of manually managing each container, Kubernetes does this for you using predefined configurations and automation. It groups containers into logical units called Pods and manages them efficiently.
 ## EXAMPLE-
Imagine you have a toy store, and you have many different kinds of toys (apps). You want to make sure your toys are always available to customers, even if some of them break or go missing. Kubernetes (K8s) is like a magic toy organizer that keeps all your toys in order, replaces broken ones, and makes sure everything runs smoothly! 🏗️🎠

## Why Kubernetes?

- **Automated Deployment & Scaling**: Helps deploy applications and scale them based on demand.
- **Self-healing**: Restarts failed containers, replaces and reschedules them when necessary.
- **Load Balancing**: Distributes network traffic efficiently.
- **Storage Orchestration**: Manages storage needs dynamically.
- **Secret & Configuration Management**: Handles sensitive data securely.

## Prerequisites

To run Kubernetes, you need:

- **Basic Knowledge**: Understanding of containers (Docker), Linux commands, and networking.
- **System Requirements**:
  - Minimum **2 CPU cores** and **4GB RAM** (8GB recommended).
  - At least **20GB free disk space**.
- **Required Tools**:
  1. Docker (for containerized applications)
  2. kubectl (Kubernetes command-line tool)
  3. Minikube or Kind (for local cluster setup)

## Installation

### 1. Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
```

### 2. Install kubectl (Kubernetes CLI)

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client
```

### 3. Install Minikube (For Local Cluster)

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
```

### 4. Verify Installation

```bash
kubectl get nodes
```

## Basic Kubernetes Concepts

- **Pods**: The smallest unit in Kubernetes, containing one or more containers.
- **Deployments**: Manages the deployment and scaling of Pods.
- **Services**: Exposes Pods as network services internally or externally.
- **Ingress**: Manages external access to services using HTTP/HTTPS.
- **ConfigMaps & Secrets**: Stores configuration data securely

This `README.md` serves as a beginner-friendly guide for Kubernetes.

