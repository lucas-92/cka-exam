# Criar conteúdo do arquivo Markdown
conteudo_markdown = """
# Exemplo: Usar `command` e `args` para executar `ps aux` no container Nginx

Este guia descreve como configurar um container Nginx no Kubernetes para instalar o utilitário `ps` (parte do pacote `procps`) e listar os processos em execução com o comando `ps aux`, usando `command` e `args`.

---

## Manifesto YAML

Abaixo está o manifesto YAML para criar um pod que utiliza o comando `ps aux`:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-ps
spec:
  containers:
  - name: nginx
    image: nginx:latest
    command: ["/bin/sh", "-c"]
    args:
      - |
        apt update && apt install -y procps && ps aux && sleep 3600
