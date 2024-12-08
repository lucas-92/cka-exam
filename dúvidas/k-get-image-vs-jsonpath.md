## Diferença entre usar `kubectl get` com `jsonpath` e `kubectl describe` com `grep`

### Usando `kubectl get` com `jsonpath`:
```bash
kubectl get deployment deploy-1 -o jsonpath='{.spec.template.spec.containers[0].image}' > /tmp/deploy-image
```
- Mais preciso, ideal para automação e scripts.
- Produz uma saída silenciosa com apenas o valor da imagem.

### Usando `kubectl describe` com `grep`:
```bash
kubectl describe deployments.apps deploy-1 | grep Image
```
- Mais conveniente para inspeções manuais.
- Produz uma saída com mais contexto sobre o deployment, podendo ser mais difícil de manipular automaticamente.

**Comparação:**

| Critério                   | `kubectl get` com `jsonpath`                     | `kubectl describe` com `grep`          |
|----------------------------|-------------------------------------------------|---------------------------------------|
| **Formato da saída**       | Apenas a imagem (`nginx:1.19`)                  | Linha com contexto (`Image: nginx:1.19`) |
| **Facilidade de uso**      | Requer conhecimento do caminho JSON             | Mais simples para inspeção manual     |
| **Ideal para scripts**     | Sim, fornece apenas a informação necessária     | Não, requer processamento adicional   |
| **Detalhes adicionais**    | Não                                             | Inclui contexto, útil para debugging  |
| **Precisão**               | Alta                                            | Média (dependendo do filtro `grep`)   |

---
