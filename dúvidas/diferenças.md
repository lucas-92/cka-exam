# Recriar o arquivo markdown após o reset

# Criando o conteúdo em Markdown
markdown_content_diff = """
# Diferença entre os comandos `k create deployment` e `k run`

## Comando: `k create deployment`
### Descrição:
- Cria um manifesto YAML para um Deployment no Kubernetes, especificando o nome do Deployment e a imagem a ser usada.
- É focado na criação de workloads gerenciados, como **Deployments**, que incluem lógica para escalar, atualizar e gerenciar o estado dos Pods.
- No exemplo dado, o comando adiciona uma especificação para o número da porta (80).

### Características:
- **Gera um Deployment:** Que gerencia os Pods e garante que o número especificado de réplicas esteja em execução.
- **Manifesto mais completo:** Inclui especificações para estratégias de atualização, replicação e gerenciamento do Deployment.
- **Uso principal:** Criar aplicações completas e gerenciáveis no cluster Kubernetes.

### Exemplo:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 1
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
        ports:
        - containerPort: 80
