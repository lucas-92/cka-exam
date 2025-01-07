## **Tarefa 1**

- Crie um ConfigMap chamado `app-config` com as seguintes chaves e valores:
  - `APP_ENV=production`
  - `APP_DEBUG=false`
- Crie um Secret chamado `db-secret` com as seguintes chaves e valores (codifique os valores em Base64):
  - `DB_USER=admin`
  - `DB_PASSWORD=password123`
- Crie um Pod chamado `app` que:
  - Usa a imagem `busybox` e fica em execução contínua (`command: ["sh", "-c", "sleep 3600"]`).
  - Monta o ConfigMap em `/etc/config`.
  - Usa as variáveis de ambiente do Secret.
 
---

## **Tarefa 2**
1. Crie um ConfigMap chamado `web-config` com as seguintes chaves e valores:
   - `SERVER_PORT=8080`
   - `LOG_LEVEL=info`
2. Crie um Secret chamado `api-secret` com as seguintes chaves e valores (codifique os valores em Base64):
   - `API_KEY=myapikey`
   - `API_SECRET=myapisecret`
3. Crie um Pod chamado `web-app` que:
   - Usa a imagem `nginx` e fica em execução contínua.
   - Monta o ConfigMap em `/etc/web-config`.
   - Usa as variáveis de ambiente do Secret.

---

## **Tarefa 3**
1. Crie um ConfigMap chamado `service-config` com as seguintes chaves e valores:
   - `SERVICE_NAME=auth-service`
   - `MAX_CONNECTIONS=100`
2. Crie um Secret chamado `db-credentials` com as seguintes chaves e valores (codifique os valores em Base64):
   - `DB_HOST=db.example.com`
   - `DB_PORT=5432`
3. Crie um Pod chamado `auth-service` que:
   - Usa a imagem `python:3.10-alpine` e executa o comando `["sh", "-c", "while true; do echo running; sleep 5; done"]`.
   - Monta o ConfigMap em `/etc/service-config`.
   - Usa as variáveis de ambiente do Secret.
