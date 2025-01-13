
# Criar Pods no Kubernetes usando Linha de Comando e Dry-Run

Este guia mostra como criar um Namespace e Pods usando o comando `kubectl` com a flag `--dry-run=client` para gerar arquivos YAML.

---

## 1. Criar o Namespace `network-test`

```bash
kubectl create namespace network-test --dry-run=client -o yaml > namespace.yaml
```

Isso gera o arquivo `namespace.yaml` com o seguinte conteúdo:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: network-test
```

---

## 2. Criar o Pod `pod-a`

```bash
kubectl run pod-a --image=busybox --namespace=network-test --command --dry-run=client -o yaml -- sh -c "sleep 3600" > pod-a.yaml
```

Isso gera o arquivo `pod-a.yaml` com o seguinte conteúdo:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-a
  namespace: network-test
spec:
  containers:
  - name: pod-a
    image: busybox
    command:
    - sh
    - -c
    - sleep 3600
```

---

## 3. Criar o Pod `pod-b`

```bash
kubectl run pod-b --image=busybox --namespace=network-test --command --dry-run=client -o yaml -- sh -c "sleep 3600" > pod-b.yaml
```

Isso gera o arquivo `pod-b.yaml` com o seguinte conteúdo:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-b
  namespace: network-test
spec:
  containers:
  - name: pod-b
    image: busybox
    command:
    - sh
    - -c
    - sleep 3600
```

---

## 4. Aplicar os Arquivos YAML

Depois de gerar os arquivos YAML, aplique-os com o seguinte comando:

```bash
kubectl apply -f namespace.yaml
kubectl apply -f pod-a.yaml
kubectl apply -f pod-b.yaml
```

---

## 5. Verificar os Pods

Certifique-se de que os Pods estão em execução:

```bash
kubectl get pods -n network-test
```

---

## 6. Testar Conectividade

Entre no Pod `pod-a` e faça o teste de conectividade com `pod-b`:

```bash
kubectl exec -n network-test pod-a -- ping pod-b
```

Isso confirma a conectividade entre os Pods. 🚀
