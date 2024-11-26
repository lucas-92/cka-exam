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
k create deployment nginx --image=nginx -o yaml --dry-run=client > deployment.yaml

vim deployment.yaml (Para adaptar o manifesto do deployment para um ReplicaSet)

vim deploy.yaml

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: primeiro-deploy
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
        image: nginx
```

k apply -f deploy.yaml

k get deployments,rs,pod

k edit deployment primeiro-deployment

E alterar quantidade de réplicas

k scale deployment --replicas 5 primeiro-deployment

Adicionar variável de ambiente no manifesto deploy.yaml

k apply -f deploy.yaml

k get rs

k describe deployment primeiro-deployment

k rollout history deployment primeiro-deployment

Alterar o valor de uma variável de ambiente 

k apply -f deploy.yaml --record

k rollout history deployment primeiro-deploy

k edit deployment primeiro-deployment

Alterar a imagem para alpine

k get pod

k get pod primeiro-deploy-98a7sdasa-dasd -o yaml | grep image

k rollout history deplyment primeiro deploy

k get rs

k rollout undo --to-revision 3 deployment primeiro-deploy

k rollout status deployment primeiro-deploy

k rollout pause deployment primeiro-deploy

k edit deployment 

ALTERAR A IMAGEM NGINX

k apply -f deploy.yaml

k get pod

k rollout resume deployment primeiro-deploy

k rollout history deployment primeiro-deploy

k edit deployment primeiro-deploy

(Adicionar um record)ALTERAR "kubernetes.io/change-cause" para: Update de imagem
(Alterar para uma versão)ALTERAR IMAGEM PARA SÓ NGINX

k rollout history deployment primeiro-deploy

