```
vim pod.yaml
```

```
apiVersion: v1
kind: pod
metadata:
  name: meu-pod
spec:
  containers:
  - name: nginx
    image: nginx
    ports:
    - containerPort: 80
```
```
k apply -f pod
```
```
k get pods
```
```
k describe pod meu-pod
```
```
k explain pod
```
```
k explain pod --recursive
```
