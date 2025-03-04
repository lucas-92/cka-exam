# Simulated CKA Exam (Killercoda-Compatible)

⏳ **Time Limit:** 2 hours  
🔧 **Setup:** Execute `kubectl` commands to create the necessary resources before troubleshooting.  

---

## 📂 Section 1: Troubleshooting & Cluster Operations (6 Questions)

### 1. Fix a Failing Pod
**Setup:**  
```sh
kubectl run crashpod --image=nginx -- /bin/false
```
🔹 The pod `crashpod` is in **CrashLoopBackOff**.  
✅ **Fix the issue and restart the pod.**  

---

### 2. Identify and Fix a Node Issue  
**Setup:**  
```sh
kubectl taint nodes $(kubectl get nodes -o=jsonpath='{.items[0].metadata.name}') key=value:NoSchedule
```
🔹 The first node is **NotReady** for scheduling.  
✅ **Identify the issue and make the node schedulable again.**  

---

### 3. Debug a Service Not Responding  
**Setup:**  
```sh
kubectl create deployment broken-app --image=nginx
kubectl expose deployment broken-app --port=8080 --name=broken-service
```
🔹 The service `broken-service` is **not accessible**.  
✅ **Find out why and fix it.**  

---

### 4. Restart a Stuck Pod  
**Setup:**  
```sh
kubectl run stuck-pod --image=nginx
```
🔹 The pod `stuck-pod` is running but needs to be restarted without deleting it.  
✅ **Restart the pod properly.**  

---

### 5. View Logs of a Pod  
**Setup:**  
```sh
kubectl run logpod --image=busybox --command -- sh -c "while true; do echo 'Error: Something went wrong'; sleep 2; done"
```
🔹 The pod `logpod` is generating logs.  
✅ **Display the last 10 log lines.**  

---

### 6. Check Events in a Namespace  
✅ **List all recent events in the `default` namespace.**  

---

## 📂 Section 2: Workloads & Scheduling (5 Questions)

### 7. Deploy an Nginx Pod  
✅ **Create a pod named `nginx-pod` running `nginx:latest`.**  

---

### 8. Scale a Deployment  
**Setup:**  
```sh
kubectl create deployment scale-test --image=nginx
```
✅ **Scale `scale-test` deployment to 3 replicas.**  

---

### 9. Create a CronJob  
✅ **Create a CronJob `daily-job` that runs `date` every 12 hours.**  

---

### 10. Assign a Pod to a Specific Node  
✅ **Create a pod `node-pod` that runs only on the worker node.**  

---

### 11. Configure Pod Affinity  
✅ **Create a pod `affinity-pod` that only runs on nodes labeled `zone=us-east`.**  

---

## 📂 Section 3: Networking & Services (5 Questions)

### 12. Create a Service for a Deployment  
**Setup:**  
```sh
kubectl create deployment webapp --image=nginx
```
✅ **Expose `webapp` as a ClusterIP service on port 80.**  

---

### 13. Expose a Service Using NodePort  
✅ **Modify `webapp` service to be accessible via NodePort on `30080`.**  

---

### 14. Configure an Ingress Resource  
✅ **Create an Ingress for `http://web.example.com` to `webapp` service on port 80.**  

---

### 15. Implement a NetworkPolicy  
✅ **Create a NetworkPolicy `deny-all` that blocks all incoming traffic in the `secure` namespace.**  

---

### 16. Allow Traffic from a Specific Pod  
✅ **Modify `deny-all` to allow traffic from pods labeled `role=trusted`.**  

---

## 📂 Section 4: Storage & Persistent Data (3 Questions)

### 17. Create a PersistentVolume  
✅ **Create a PV `data-pv` with 10Gi storage using `hostPath`.**  

---

### 18. Create a PersistentVolumeClaim  
✅ **Create a PVC `data-pvc` of 5Gi and bind it to `data-pv`.**  

---

### 19. Mount a PVC in a Pod  
✅ **Create a pod `storage-pod` that mounts `data-pvc` at `/data`.**  

---

## 📂 Section 5: Security & RBAC (3 Questions)

### 20. Create an RBAC Role for Read Access  
✅ **Create a Role `read-role` in `dev` namespace with `get`, `list`, and `watch` permissions on pods.**  

---

### 21. Bind the Role to a User  
✅ **Bind `read-role` to the user `developer` using RoleBinding.**  

---

### 22. Create a Service Account and Use It  
✅ **Create a ServiceAccount `app-sa` and assign it to the pod `app-pod`.**  

---

## 💡 Tips
- Use `kubectl explain <resource>` to check object definitions.  
- Use `kubectl get events -A` to detect failures.  
- For debugging, use `kubectl describe` and `kubectl logs`.  
- To generate YAML quickly, use `kubectl create <resource> --dry-run=client -o yaml`.  

---

Now the **scenarios are created before troubleshooting**! 🚀 **Good luck!**
