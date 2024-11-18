# Crie um pod nginx simples
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

# Listar Pods

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

# Criar pod rápido

```
k run nginx --image nginx --env teste=true --port 80 --dry-run=client -o yaml
```


# Editar imagem de um pod
```
k edit pod meu-pod
```

```
k describe pod meu-pod | grep Image
```

# Colocar uma variável de ambiente

```
k get pod meu-pod -o yaml > pod.yaml
```

```
k replace -f pod.yaml --force
```

# Listar as variáveis de ambiente dentro do pod

```
k exec -it pods/meu-pod -- env
```

# Criar um pod com sleep

```
k run sleep --image busybox -o yaml --dry-run=client -- sleep 1000 > sleep.yaml
```

# Excluir um pod com o comando sleep rápido

```
 k delete pod sleep --force --grace-period 0
```

# Incluir variável de ambiente

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
