# Lista de Arquivos YAML do Kubernetes



## 1. Pods

```
apiVersion: v1
kind: Pod
metadata:
  name: nome-do-pod
spec:
  containers:
  - name: nome-do-container
    image: imagem
```

## 2. ReplicaSets

```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nome-do-replicaset
spec:
  replicas: 2
  selector:
    matchLabels:
      app: exemplo
  template:
    metadata:
      labels:
        app: exemplo
    spec:
      containers:
      - name: app-container
        image: nginx
```

## 3. Deployments

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nome-do-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: exemplo
  template:
    metadata:
      labels:
        app: exemplo
    spec:
      containers:
      - name: nginx
        image: nginx:latest
```
## 4. Services
```
apiVersion: v1
kind: Service
metadata:
  name: nome-do-service
spec:
  selector:
    app: exemplo
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: ClusterIP
```

## 5. ConfigMaps
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: nome-do-configmap
data:
  chave: valor
```
## 6. Secrets
```
apiVersion: v1
kind: Secret
metadata:
  name: nome-da-secret
type: Opaque
data:
  user: c3VwZXJhZG1pbg==
  password: bWluaGFzZW5oYXN1cGVyc2VndXJh
```
## 7. PersistentVolumes (PVs)
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: nome-do-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
  - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: /data
```
## 8. PersistentVolumeClaims (PVCs)
```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: nome-do-pvc
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
```

## 9. Ingress
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: nome-do-ingress
spec:
  rules:
  - host: exemplo.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: nome-do-service
            port:
              number: 80
```
## 10. Jobs
```
apiVersion: batch/v1
kind: Job
metadata:
  name: nome-do-job
spec:
  template:
    spec:
      containers:
      - name: job-container
        image: busybox
        command: ["echo", "Hello World"]
      restartPolicy: Never
```
## 11. CronJobs

```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: nome-do-cronjob
spec:
  schedule: "*/5 * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: cronjob-container
            image: busybox
            command: ["echo", "Hello Cron"]
          restartPolicy: Never
```
## 12. HorizontalPodAutoscaler (HPA)

Always show details

apiVersion: autoscaling/v1

kind: HorizontalPodAutoscaler

metadata:

  name: nome-do-hpa

spec:

  scaleTargetRef:

    apiVersion: apps/v1

    kind: Deployment

    name: nome-do-deployment

  minReplicas: 1

  maxReplicas: 5

  targetCPUUtilizationPercentage: 50

13. NetworkPolicy

Always show details

apiVersion: networking.k8s.io/v1

kind: NetworkPolicy

metadata:

  name: nome-da-policy

spec:

  podSelector:

    matchLabels:

      role: db

  policyTypes:

  - Ingress

  - Egress

  ingress:

  - from:

    - podSelector:

        matchLabels:

          role: frontend
