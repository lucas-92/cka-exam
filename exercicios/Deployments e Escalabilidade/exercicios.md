
## Deployments e Escalabilidade

### Tarefa 1:

- Crie um Deployment chamado `frontend` com 3 réplicas que usa a imagem `nginx:1.21`.
- Atualize o Deployment para usar a imagem `nginx:1.22`.
- Escale o Deployment para 5 réplicas.
- Verifique o estado das réplicas.

---

## Deployments e Escalabilidade

### Tarefa 2:

- Crie um Deployment chamado `backend` com 2 réplicas que utiliza a imagem `node:14`.
- Atualize o Deployment para usar a imagem `node:16`.
- Escale o Deployment para 6 réplicas.
- Verifique se todas as réplicas estão em execução e prontas.

---

## Deployments e Atualizações

### Tarefa 3:

- Crie um Deployment chamado `api-service` com 4 réplicas que usa a imagem `python:3.9-slim`.
- Altere o Deployment para usar a imagem `python:3.10-slim`.
- Reduza o número de réplicas para 2.
- Liste os Pods e valide as alterações realizadas.

---

## Deployments e Rollback

### Tarefa 4:

- Crie um Deployment chamado `web-app` com 5 réplicas que utiliza a imagem `httpd:2.4`.
- Atualize o Deployment para usar a imagem `httpd:2.4.54`.
- Realize um rollback para a versão anterior.
- Verifique o histórico de revisões do Deployment.
