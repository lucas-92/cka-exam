# Exercício 1: Criando e sobrescrevendo o entrypoint

Crie um pod imperativamente que execute o comando env para listar as variáveis de ambiente no contêiner.

kubectl run command --image=nginx --command --dry-run=client -o yaml -- /bin/sh -c env > command.yaml
kubectl apply -f command.yaml
kubectl get pods
kubectl logs command

Modifique o manifesto gerado (command.yaml) para sobrescrever o comando original e adicionar argumentos (Args), para que o pod execute o comando /bin/sh e liste os processos (ps aux).

    No arquivo YAML, insira:

    spec:
      containers:
      - name: command
        image: nginx
        command: ["/bin/sh", "-c"]
        args: ["ps aux"]

Substitua o pod com a nova configuração:

    kubectl replace -f command.yaml --force

    Liste os pods novamente e verifique os logs para validar a saída do comando ps aux.

# Exercício 2: Criando uma execução longa com "sleep"

    Crie um pod imperativamente que execute o comando sleep 1d (mantendo o contêiner em execução por 1 dia):

kubectl run command --image=nginx --command --dry-run=client -o yaml -- /bin/sh -c "sleep 1d" > command.yaml

Substitua o pod caso ele já exista:

kubectl replace -f command.yaml --force

Verifique se o pod foi criado e está em execução:

kubectl get pods

Entre no contêiner usando um terminal interativo:

kubectl exec -ti command -- bash

No terminal do contêiner, instale o pacote procps para habilitar o comando ps aux:

apt update
apt install procps

Liste os processos ativos no contêiner:

    ps aux

    Explique a diferença entre configurar Command e Args no manifesto para manter o pod executando.

# Exercício 3: Explorando a ausência de Command e adicionando via manifesto

    Crie um pod imperativamente sem sobrescrever o ENTRYPOINT da imagem (sem usar --command):

kubectl run command --image=nginx --dry-run=client -o yaml > command.yaml

Aplique o manifesto para criar o pod:

kubectl replace -f command.yaml --force

Verifique o status do pod criado:

kubectl get pods

Entre no contêiner para explorar o que está sendo executado:

kubectl exec -ti command -- bash

Modifique o manifesto gerado (command.yaml) para adicionar um novo comando e argumentos, sobrescrevendo o comportamento padrão. Configure o pod para listar processos em execução (ps aux).

    No manifesto, edite a seção:

    spec:
      containers:
      - name: command
        image: nginx
        command: ["/bin/sh", "-c"]
        args: ["ps aux"]

Substitua o pod com o novo manifesto:

kubectl replace -f command.yaml --force

Liste os pods e valide o novo comportamento com os logs:

    kubectl get pods
    kubectl logs command

Objetivo dos exercícios

    Compreender como sobrescrever comandos padrão (ENTRYPOINT) com Command e Args.
    Manipular YAMLs para modificar e aplicar configurações de pods.
    Aprender a criar pods com comandos simples, execuções longas e ações customizadas.

Boa prática!
