



### **Why Use Kubernetes?**  
- **Automated Scaling**: Increases or decreases the number of running containers based on demand.  
- **Self-Healing**: Automatically restarts failed containers and replaces unhealthy nodes.  
- **Load Balancing & Service Discovery**: Distributes traffic efficiently and makes services discoverable.  
- **Declarative Configuration**: Uses YAML files for managing deployments, services, and networking.  
- **Multi-Cloud & Hybrid Support**: Runs on AWS, Azure, Google Cloud, or even on-premise.  

---

### **Core Concepts of Kubernetes**  

| Concept      | Description |
|-------------|------------|
| **Pod** | The smallest unit in Kubernetes. A pod contains one or more containers. |
| **Node** | A physical or virtual machine that runs pods. |
| **Cluster** | A set of nodes managed by Kubernetes. |
| **Deployment** | Manages application rollout and updates. |
| **Service** | Exposes pods to the network, allowing communication between them. |
| **Ingress** | Manages external access to services (e.g., HTTP/HTTPS). |
| **ConfigMap & Secret** | Store configuration data and sensitive information separately from code. |

---

### **How Kubernetes Works?**  
1. **You Define Your App in YAML**  
   - Create a **Deployment** YAML file to define how many replicas you need.  
   - Use a **Service** YAML file to expose it internally or externally.  
   - Configure an **Ingress** YAML file for domain-based routing.  

2. **Kubernetes Scheduler Places Pods on Nodes**  
   - The **Scheduler** decides where to place pods based on available resources.  

3. **Kubelet Ensures Pods Stay Running**  
   - If a pod crashes, **Kubelet** restarts it automatically.  

4. **Scaling & Load Balancing**  
   - If traffic increases, Kubernetes scales up pods.  
   - The **Kube-Proxy** and **Ingress Controller** manage networking.  

---

### **Example: Deploying Nginx on Kubernetes**  

**1. Create a Deployment (`nginx-deployment.yml`)**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

**2. Create a Service (`nginx-service.yml`)**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```

**3. Apply the YAML files**
```bash
kubectl apply -f nginx-deployment.yml
kubectl apply -f nginx-service.yml
```


