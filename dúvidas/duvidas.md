
## 1. Comando para listar os pods e filtrar pelo nome

**Comando:**
```bash
kubectl get pod -n default -o custom-columns=NAME:.metadata.name
```

- **Explicação do Comando:**
    - `kubectl get pod`: lista todos os pods no namespace `default`.
    - `-n default`: especifica o namespace `default`.
    - `-o custom-columns=NAME:.metadata.name`: formata a saída para mostrar apenas o nome de cada pod.

## 2. Como saber que `k8s-app=kube-dns` é o rótulo do CoreDNS?

- O rótulo `k8s-app=kube-dns` pode ser encontrado usando o comando:
    ```bash
    kubectl get pods -n kube-system --show-labels
    ```
- O rótulo `k8s-app=kube-dns` é usado para identificar os pods do CoreDNS.

## 3. Explicação do comando `-o jsonpath='{.items[0].spec.containers[0].image}'`

- **Comando:**
    ```bash
    kubectl get deployment deploy-1 -o jsonpath='{.spec.template.spec.containers[0].image}'
    ```
- **Explicação do `jsonpath`:**
    - `kubectl get deployment deploy-1`: obtém o deployment `deploy-1`.
    - `-o jsonpath='{.spec.template.spec.containers[0].image}'`: usa `jsonpath` para extrair o campo da imagem do primeiro container.

## 4. Como alterar a imagem do deployment para `nginx:latest` com um motivo

**Comando para alterar a imagem:**
```bash
kubectl set image deployment/deploy-1 app-container=nginx:latest --record
```
- **Explicação:**
    - `kubectl set image`: altera a imagem do container no deployment.
    - `app-container=nginx:latest`: define a imagem para `nginx:latest`.
    - `--record`: registra o motivo da mudança no histórico do deployment.

**Comando para verificar a causa:**
```bash
kubectl rollout history deployment/deploy-1
```

## 5. Reverter o deployment para a revisão 1

**Comando para reverter:**
```bash
kubectl rollout undo deployment/deploy-1 --to-revision=1
```
- **Explicação:**
    - Reverte o deployment para a revisão 1.

**Verificar o histórico do deployment:**
```bash
kubectl rollout history deployment/deploy-1
```

## 6. Como verificar a imagem do deployment e salvar em `/tmp/deploy-image`

**Comando para obter a imagem:**
```bash
kubectl get deployment deploy-1 -o jsonpath='{.spec.template.spec.containers[0].image}' > /tmp/deploy-image
```
- **Explicação:**
    - Extrai a imagem do primeiro container do deployment `deploy-1` e grava no arquivo `/tmp/deploy-image`.

**Verificar o conteúdo do arquivo:**
```bash
cat /tmp/deploy-image
```

## 8. Comando para consultar o status do Deployment `deploy-1`

**Comando:**
```bash
kubectl rollout status deployment/deploy-1
```

---

## 9. Revertendo o Deployment `deploy-1` para a revisão 1

**Comando para reverter a revisão:**
```bash
kubectl rollout undo deployment/deploy-1 --to-revision=1
```

**Comando para verificar o histórico de revisões:**
```bash
kubectl rollout history deployment/deploy-1
```
