```
vim replica.yaml
```
```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: meu-rs
spec:
  replicas: 3
  selector:
    matchLabels:
      tier: web
  template:
    metadata:
      labels:
        tier: web
    spec: 
      containers:
      - name: nginx
        image: nginx
```
```
k apply replica.yaml
```
