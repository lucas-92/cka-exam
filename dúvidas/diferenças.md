# Recriando a explicação em Markdown para a diferença entre os comandos

markdown_content_diff_commands = """
# Diferença entre os comandos `k create deployment` e `k run`

## Comando: `k create deployment nginx --image=nginx --port=80 -o yaml --dry-run=client > deploy.yaml`
### Descrição:
- Cria um manifesto YAML para um Deployment no Kubernetes.
- Especifica o nome do Deployment (`nginx`), a imagem do contêiner (`nginx`) e a porta que o contêiner irá expor (`80`).
- Utiliza a flag `--dry-run=client` para não aplicar o Deployment diretamente no cluster e gerar apenas o YAML.

### Objetivo:
- Criar um recurso do tipo **Deployment**, que gerencia Pods, garante o número de réplicas e permite estratégias de atualização.

### Características:
- **Deployment gerenciado:** Ideal para workloads com alta disponibilidade.
- **Inclui lógica de escalonamento e gerenciamento.**
- **Manifesto mais completo:** Contém especificações como estratégia de atualização e gerenciamento de réplicas.

---

## Comando: `k run nginx --image=nginx --port=80 --env test=test --dry-run=client -o yaml -- cat /etc/logs >> deploy.yaml`
### Descrição:
- Cria um manifesto YAML para um Pod diretamente no Kubernetes.
- Inclui o contêiner `nginx` com uma porta exposta (`80`) e uma variável de ambiente (`test=test`).
- Adiciona um comando (`cat /etc/logs`) ao contêiner para execução.
- Utiliza `--dry-run=client` para gerar o YAML sem aplicar o Pod no cluster.

### Objetivo:
- Criar um recurso do tipo **Pod**, sem gerenciamento de réplicas ou estratégias de atualização.

### Características:
- **Recurso direto:** Gera apenas um Pod simples, sem lógica de escalonamento.
- **Mais flexível:** Permite adicionar comandos personalizados e variáveis de ambiente específicas.
- **Útil para testes ou tarefas pontuais.**

---

## Diferenças principais

| Aspecto                        | `k create deployment`                | `k run`                              |
|--------------------------------|---------------------------------------|---------------------------------------|
| **Tipo de recurso criado**     | Deployment                           | Pod                                  |
| **Gerenciamento de réplicas**  | Sim, via controlador do Deployment   | Não, apenas um único Pod             |
| **Finalidade**                 | Aplicações gerenciadas               | Testes ou execuções específicas      |
| **Flexibilidade**              | Estrutura padrão para produção       | Configurações específicas no Pod     |
| **Comando adicional no Pod**   | Não                                  | Sim, possível com `command`          |

---

## Quando usar cada comando:
- **`k create deployment`:** Use quando configurar uma aplicação que requer gerenciamento contínuo, com réplicas e atualizações automáticas.
- **`k run`:** Use para criar um único Pod para testes, execução de comandos específicos ou casos pontuais.

"""

# Salvando o conteúdo em um arquivo Markdown
file_path_diff_commands = "/mnt/data/Diferenca_entre_comandos_k_create_deployment_k_run.md"
with open(file_path_diff_commands, "w") as file:
    file.write(markdown_content_diff_commands)

file_path_diff_commands
