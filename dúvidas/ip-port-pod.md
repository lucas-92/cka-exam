# Explicação de IPs e Portas do Pod `nginx`

Aqui está a explicação dos **IPs** e **portas** associados ao Pod `nginx` descrito:

---

### **1. IPs**
#### **Pod IP**: `10.244.0.17`
- **Significado**: Este é o IP atribuído ao Pod no **Cluster Network** (rede do cluster Kubernetes). Cada Pod no Kubernetes recebe um IP exclusivo dentro do espaço de rede do cluster, permitindo a comunicação entre os Pods sem a necessidade de NAT (Network Address Translation).
- **Uso**: 
  - Outros Pods no mesmo cluster podem se comunicar diretamente com este IP.
  - Exemplo: um Pod pode enviar requisições HTTP para `http://10.244.0.17`.

#### **Node IP**: `172.18.0.2` (control-plane)
- **Significado**: Este é o IP do nó Kubernetes onde o Pod está sendo executado.
- **Uso**:
  - É usado pela rede do cluster para rotear o tráfego até o nó específico que hospeda o Pod.
  - O Pod em si não "vê" ou usa diretamente este IP.

---

### **2. Portas**
#### **Container Port**: `80/TCP`
- **Significado**: A aplicação `nginx` dentro do contêiner está ouvindo na porta **80** usando o protocolo TCP.
- **Uso**:
  - Este é o ponto de entrada para o tráfego dentro do contêiner.
  - Exemplo: Se outro Pod ou um Service enviar uma requisição para o Pod, ela será roteada para esta porta dentro do contêiner.

#### **Host Port**: `0/TCP`
- **Significado**: A porta **0/TCP** indica que o Kubernetes **não mapeou nenhuma porta do nó host** para o contêiner.
- **Uso**:
  - Não há exposição direta do contêiner para o host (máquina física/virtual que executa o nó).
  - Normalmente, você usa um **Service** para expor o Pod em vez de mapear diretamente uma porta do host.

---

### **Resumo**
- **Comunicação interna no cluster**:
  - Outros Pods no mesmo cluster podem usar o IP do Pod (`10.244.0.17`) e a porta 80 para se comunicar com ele.
  - Exemplo: `wget http://10.244.0.17:80`.

- **Comunicação externa ao cluster**:
  - Como o `Host Port` não foi configurado, o Pod não está acessível diretamente fora do cluster.
  - Para permitir acesso externo, você precisa criar um **Service** (ClusterIP, NodePort ou LoadBalancer) que exponha o Pod.

Se você precisar criar um Service para expor este Pod, posso ajudar a configurar!
