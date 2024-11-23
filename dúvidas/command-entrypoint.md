Command e Args no manifesto do Kubernetes
Finalidade

    Command: Define o comando principal que será executado pelo contêiner ao iniciar. Ele substitui o ENTRYPOINT definido na imagem Docker.
    Args: Especifica os argumentos para o comando principal. Ele complementa o comando definido em Command ou o CMD da imagem Docker, caso Command não seja sobrescrito.

Por que dois campos?

    Flexibilidade: Separar o comando e os argumentos permite mais controle e clareza. Você pode, por exemplo, alterar apenas os argumentos sem tocar no comando principal.
    Compatibilidade: O Command pode sobrescrever o ENTRYPOINT da imagem Docker, enquanto os Args substituem os CMD da imagem.

Exemplo no Kubernetes

Manifesto do pod:

containers:
  - name: my-container
    image: nginx
    command: ["/bin/sh", "-c"]
    args: ["echo Hello World"]

    Command: Substitui o ENTRYPOINT para executar o shell (/bin/sh -c).
    Args: Passa o comando echo Hello World como argumento para o shell.

ENTRYPOINT e CMD no Dockerfile
Finalidade

    ENTRYPOINT: Define o comando ou binário padrão que sempre será executado quando o contêiner iniciar. É pensado como o "ponto de entrada" fixo.
    CMD: Define os argumentos padrão passados para o ENTRYPOINT. Se o ENTRYPOINT não for especificado, o CMD se torna o comando principal.

Por que dois campos?

    Separação de responsabilidades:
        O ENTRYPOINT define o que o contêiner faz.
        O CMD define os parâmetros padrão para o que ele faz.
    Sobrescrita flexível:
        Se o ENTRYPOINT for definido, você pode sobrescrever o CMD ao rodar o contêiner.
        Sem um ENTRYPOINT, o CMD é o comportamento padrão, mas pode ser totalmente sobrescrito ao rodar docker run.

Exemplo no Docker

Dockerfile:

FROM nginx
ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-g", "daemon off;"]

    ENTRYPOINT: Define o comando nginx para sempre iniciar o servidor.
    CMD: Fornece argumentos padrão para rodar o nginx (-g daemon off;).
    Comportamento:
        Ao executar docker run nginx, o contêiner usará tanto o ENTRYPOINT quanto o CMD.
        Se você executar docker run nginx -h, o CMD será substituído por -h, mas o ENTRYPOINT (/usr/sbin/nginx) permanece.

Por que preciso preencher duas especificações (Command e Args) no Kubernetes?

    Compatibilidade com o Docker:
        O Kubernetes foi projetado para trabalhar com imagens Docker e adotar sua lógica de ENTRYPOINT e CMD.
        Command substitui o ENTRYPOINT, enquanto Args substitui o CMD.

    Separação de responsabilidades:
        No Kubernetes, você pode sobrescrever apenas o que precisa:
            Mudar só o comando (Command) sem alterar os argumentos.
            Ou, manter o comando padrão e alterar apenas os argumentos (Args).

    Maior Controle:
        Ao permitir substituir comandos e argumentos separadamente, o Kubernetes dá mais flexibilidade para adaptar imagens de contêiner sem a necessidade de reconstruí-las.


![image](https://github.com/user-attachments/assets/95003aab-8bfe-4825-963c-14e750b5e015)


  
Quando preencher ambos no Kubernetes?

    Preencha Command quando precisar sobrescrever o comando padrão (ENTRYPOINT) da imagem.
    Preencha Args quando quiser apenas alterar os argumentos (CMD) ou fornecer novos para o comando principal.

Por exemplo, se você tem uma imagem com ENTRYPOINT para executar um script e quer mudar o que o script faz:

command: ["/bin/sh", "-c"]
args: ["echo Custom Message"]
