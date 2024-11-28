
# Diferença entre alterar Deployment via `edit deployment` ou arquivo manifesto

## Alterar via `kubectl edit deployment`
### Processo:
- Você edita o recurso diretamente no cluster, abrindo o arquivo YAML atual com um editor configurado (geralmente `vim` ou outro definido pelo sistema).
- Após salvar e sair, as alterações são aplicadas automaticamente.

### Vantagens:
- **Imediato:** É rápido e direto. Útil para alterações pequenas ou urgentes.
- **Atualização incremental:** Você edita o estado atual do recurso, incluindo qualquer modificação feita automaticamente pelo Kubernetes (como campos preenchidos automaticamente).
- **Sem dependência de um arquivo local:** Não é necessário manter um manifesto atualizado localmente.

### Desvantagens:
- **Perda de controle de versão:** Se você não salvar uma cópia do novo estado, as alterações feitas não serão refletidas no arquivo de manifesto original.
- **Risco de inconsistência:** Pode causar divergências entre o que está no cluster e o que está no repositório de controle de versão (se usado).
- **Pouco organizado:** Não é ideal para equipes grandes ou para ambientes com práticas GitOps, onde os manifests são a fonte de verdade.

---

## Alterar pelo arquivo manifesto
### Processo:
- Você edita o manifesto localmente, que é o arquivo que descreve o Deployment, e aplica as alterações no cluster usando `kubectl apply -f <arquivo>`.

### Vantagens:
- **Fonte de verdade:** O arquivo de manifesto é mantido como a referência principal, geralmente versionado em um sistema de controle como Git.
- **Histórico de alterações:** Alterações feitas no arquivo podem ser rastreadas, permitindo auditoria e colaboração.
- **Consistência:** Ajuda a garantir que o estado do cluster seja sempre gerado a partir de arquivos versionados.
- **Práticas de GitOps:** Essencial para pipelines CI/CD baseados em GitOps ou sistemas como ArgoCD.

### Desvantagens:
- **Demora um pouco mais:** Você precisa editar o arquivo localmente e reaplicá-lo.
- **Dependência do arquivo correto:** Se o manifesto local estiver desatualizado em relação ao cluster, pode sobrescrever alterações não registradas no arquivo.

---

## Quando usar cada abordagem

| Situação                                    | Melhor abordagem                          |
|--------------------------------------------|-------------------------------------------|
| Alteração rápida e emergencial             | `kubectl edit deployment`                 |
| Ambiente de desenvolvimento isolado        | Qualquer uma pode ser usada               |
| Gerenciamento em equipe ou produção        | Editar o manifesto e reaplicar            |
| Uso de práticas GitOps ou automação CI/CD  | Editar o manifesto                        |
| Testando mudanças temporárias              | `kubectl edit deployment`                 |

---

## Conclusão
- **`kubectl edit deployment`**: Melhor para mudanças rápidas e situações emergenciais, mas requer cuidado para evitar inconsistências.
- **Arquivo manifesto**: Ideal para ambientes organizados, com controle de versão e quando a consistência entre o cluster e os arquivos locais é necessária. É a escolha preferida para produção ou práticas de GitOps.
