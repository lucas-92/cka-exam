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
```
k explain pod.spec --recursive
```

```
k run nginx --image nginx --env teste=true --port 80 --dry-run=client -o yaml
```

```
k replace -f pod.yaml --force
```

```
k exec -it pods/meu-pod -- env
```

```
k run sleep --image busybox -o yaml --dry-run=client -- sleep 1000 > sleep.yaml
```

```
 k replace -f sleep.yaml --force --grace-period 0
```
