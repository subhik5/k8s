
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
 
