1. Criação e Manipulação de Pods

Enunciado:

    Crie um arquivo pod.yaml que defina um pod chamado meu-pod, contendo um contêiner com a imagem nginx.
    Aplique o manifesto no cluster.
    Liste os pods no cluster e verifique os detalhes do pod criado.

Tarefas:

    Use o comando para criar e editar o arquivo pod.yaml com o conteúdo fornecido.
    Aplique o arquivo no cluster.
    Liste os pods existentes no cluster.
    Descreva o pod meu-pod para verificar se ele foi criado corretamente.

2. Explicação e Estrutura de Pods

Enunciado:

    Explore a estrutura do recurso Pod e suas especificações utilizando o comando k explain.

Tarefas:

    Explique a definição de um Pod no Kubernetes com o comando adequado.
    Liste todos os campos disponíveis de forma recursiva para um Pod.
    Faça o mesmo para a seção spec do recurso Pod.

3. Execução e Alteração de Configurações

Enunciado:

    Use o comando k run para gerar um arquivo YAML de um pod chamado sleep com a imagem busybox e o comando sleep 1000.
    Modifique o arquivo para incluir a variável de ambiente rápido.
    Reaplique o arquivo no cluster.
    Em seguida, altere a variável de ambiente para mais rápido e reimplante.

Tarefas:

    Gere o arquivo YAML do pod sleep com k run e salve-o como sleep.yaml.
    Edite o arquivo para incluir a variável de ambiente rápido.
    Reaplique o manifesto com k replace.
    Extraia o YAML novamente, altere a variável para mais rápido e reaplique.

4. Depuração e Comandos Interativos

Enunciado:

    Verifique as configurações do pod meu-pod e inspecione suas imagens.
    Acesse o contêiner dentro do pod para verificar variáveis de ambiente e testar conectividade local.

Tarefas:

    Use o comando para verificar a imagem do pod meu-pod.
    Entre no contêiner do pod meu-pod e liste as variáveis de ambiente.
    Dentro do contêiner, use o curl para testar a conectividade com localhost:80.
    Tente acessar o Redis na porta padrão (6379) com curl.

5. Forçar Substituições e Recriação de Pods

Enunciado:

    Recrie o pod nginx usando um arquivo YAML gerado pelo comando k run.
    Aplique mudanças no pod e força a substituição repetidamente.

Tarefas:

    Use k run para criar um manifesto pod.yaml para o pod nginx.
    Aplique o arquivo YAML com k apply ou k replace usando a flag --force.
    Extraia novamente o YAML do pod nginx e edite para incluir uma variável de ambiente fictícia.
    Reaplique as alterações usando k replace --force.
    Liste o pod e verifique as mudanças no YAML.

Exercícios Avançados sobre Comandos Kubernetes
1. Manipulação de Pods e Debugging

Enunciado:
Crie um pod chamado nginx-debug com a imagem nginx, configure a porta 80 e adicione uma variável de ambiente chamada DEBUG com valor true. Realize as seguintes operações de depuração no pod:

    Acesse o contêiner e verifique se o servidor web responde na porta 80 usando curl.
    Simule um erro removendo a imagem do contêiner via kubectl edit. Observe o que acontece com o pod.
    Use comandos para restaurar a configuração original sem recriar o pod manualmente.

Tarefas:

    Gere o YAML do pod com k run e salve em um arquivo nginx-debug.yaml.
    Aplique o YAML e acesse o pod para verificar o serviço usando curl localhost:80.
    Edite o pod para simular o erro e descreva o estado do pod.
    Extraia o YAML, corrija a configuração e aplique as mudanças para restaurar o pod.

2. Testando Alterações no Ambiente de Pods

Enunciado:
Implemente um pod chamado sleep-test com a imagem busybox que execute o comando sleep 1000. Inicialmente, inclua a variável de ambiente MODE=dev. Após a criação, altere essa variável para MODE=prod usando os comandos disponíveis.

Tarefas:

    Gere o YAML inicial com k run e salve como sleep-test.yaml.
    Aplique o manifesto e liste o pod criado.
    Extraia o YAML do pod e altere a variável MODE para prod.
    Reaplique o YAML usando k replace e verifique as mudanças.
    Confirme a nova configuração diretamente dentro do contêiner, usando k exec e o comando env.

3. Validando Políticas e Recriação de Recursos

Enunciado:
Configure um pod chamado meu-nginx com a imagem nginx e exporte o YAML. Aplique uma política de segurança fictícia que exige que todos os pods tenham variáveis de ambiente chamadas SECURE=true.

Tarefas:

    Crie o pod com k run e exporte seu YAML para meu-nginx.yaml.
    Adicione a variável de ambiente SECURE=true e reaplique o YAML com k replace.
    Teste o pod antes e depois de aplicar a política (simule a política manualmente alterando o YAML).
    Use k exec para verificar se a variável está presente no ambiente do contêiner.
    Gere um novo YAML que falhe na política e descreva o erro usando k describe pod.

4. Automação e Comparação de Configurações

Enunciado:
Automatize a criação e modificação de pods com scripts. Use os comandos para criar dois pods (nginx1 e nginx2) e compare suas configurações YAML. Após isso, force ambos os pods a serem recriados com mudanças idênticas.

Tarefas:

    Use k run para criar os pods nginx1 e nginx2, salvando seus YAMLs em arquivos separados (nginx1.yaml e nginx2.yaml).
    Extraia os YAMLs dos pods já criados e compare-os usando diff.
    Edite ambos os YAMLs para adicionar a variável de ambiente VERSION=1.0.
    Reaplique as configurações alteradas com k replace.
    Liste os pods e verifique as mudanças.

5. Simulação de Ciclo de Vida de Aplicações

Enunciado:
Simule o ciclo de vida de uma aplicação usando o pod nginx:

    Crie o pod a partir de um manifesto gerado por k run.
    Configure variáveis de ambiente e simule uma atualização para uma nova versão do software (alterando a imagem).
    Force a recriação do pod para aplicar as mudanças e verifique se ele responde corretamente.
    Por fim, delete o pod forçando o encerramento imediato.

Tarefas:

    Gere o YAML inicial com k run nginx --image=nginx:1.19.
    Adicione a variável de ambiente APP_ENV=production ao YAML e aplique a mudança.
    Atualize a imagem do pod para nginx:1.21 diretamente no YAML e force a recriação com k replace --force.
    Acesse o pod para confirmar que o servidor está respondendo corretamente.
    Delete o pod com --force --grace-period=0.
