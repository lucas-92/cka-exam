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
k edit pod meu-pod
```
```
k describe pod meu-pod | grep Image
```
```
k get pod meu-pod -o yaml > pod.yaml
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
 k delete pod sleep --force --grace-period 0
```
```
k apply -f sleep.yaml
```
```
vim sleep.yaml
```
```
Incluir a variável de ambiente "rápido"
```
```
k replace -f sleep.yaml --force
```
```
k get pods sleep -o yaml > sleep.yaml
```
```
Alterar a variável de ambiente de "rápido" para "mais rápido"
```
```
k replace -f sleep.yaml --force --grace-period 0
```
```
k run nginx --image nginx --port 80 --dry-run=client -o yaml > pod.yaml
```
```
k replace -f pod.yaml --force --grace-period 0
```
```
k get pods
```
```
k get pod nginx -o yaml
```
```
k drescribe pod nginx
```
```
k exec -it nginx -c nginx -- bash
curl localhost:80
curl telnet://localhost:6379
PING
```
