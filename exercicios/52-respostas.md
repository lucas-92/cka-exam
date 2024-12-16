
# Explicação do Manifesto do Pod no Kubernetes usado na questão 37

Este arquivo descreve um manifesto YAML para criar um **Pod** no Kubernetes. Abaixo está uma análise detalhada de cada seção.

## 1. Definição do tipo de recurso
- `apiVersion: v1`: Especifica a versão da API usada para o recurso.
- `kind: Pod`: Define que o recurso a ser criado é um Pod.

## 2. Metadados
- `metadata`:
  - `name: ex-cm-pod1`: O nome do Pod é `ex-cm-pod1`.
  - `labels`: Inclui uma label chamada `run` com o valor `ex-cm-pod1`. Labels são usadas para organização e seleção de objetos no Kubernetes.

## 3. Especificação do Pod
A seção `spec` detalha como o Pod deve ser configurado.

### Containers
- Um único container é configurado:
  - `image: nginx`: O container usará a imagem do NGINX.
  - `name: ex-cm-podi`: Nome do container dentro do Pod.
  - `volumeMounts`: 
    - Monta um volume chamado `volume-config` no diretório `/data` do container.

### Porta
- `ports`:
  - `containerPort: 80`: Expõe a porta 80 no container (porta padrão do NGINX).

### Política de DNS
- `dnsPolicy: ClusterFirst`: Define que as resoluções de DNS devem priorizar os serviços do cluster.

### Política de reinício
- `restartPolicy: Always`: O Pod será reiniciado automaticamente caso o container falhe.

## 4. Volumes
A seção `volumes` define um volume chamado `volume-config`:
- O volume está vinculado a um **ConfigMap** chamado `cm2`.
- `items`:
  - Mapeia uma chave chamada `tier` (que deve existir no ConfigMap `cm2`) para um arquivo chamado `ambiente.conf` no diretório `/data` dentro do container.

## Resumo
Este Pod monta um volume baseado em um ConfigMap chamado `cm2`. Dentro do ConfigMap, a chave `tier` é salva como um arquivo chamado `ambiente.conf` no caminho `/data` no container do NGINX. A aplicação que roda no container pode usar as configurações fornecidas pelo ConfigMap, permitindo que você altere a configuração do Pod sem modificar a imagem do container.
