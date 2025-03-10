# Teoria

## Qual a finalidade da netpol?
R.: Controlar o tráfico dentro dos pods trabalhando com IPs e Portas (Camada 3 e 4 do modelo OSI)

## Qual o 1o requisito para trabalhar com netpol?
R.: Que a nossa CNI tenha suporte a netpol

## Quais as regras que temos para controlar o tráfico entre os Pods?
R.: Allow e Deny. Não é uma ação, mas sim o tipo que escrevemos a regra.

## Como selecionamos quem vai ser selecionado pela regra de tráfico de origem ou destino?
R.: podSelector, namespaceSelector e ipBlock

## Qual o fluxo de rede que conseguimos fazer e controlar?
R.: Ingress e Egress. Fluxo de entrada de rede no pod, o Ingress e o fluxo de saída de rede do pod, o Egress

# Exercícios Ingress

## Crie 3 pods: pod-a, pod-b e pod-c. Use a imagem do nginx e a porta 80.

## Crie 3 serviços para expor os pods criados use porta 80 e target-port 80.

## Crie uma netpol onde somente o pod-a pode acessar o pod-c.

## Verifique se a netpol está funcionando.

## Edite a netpol criada e inclua a regra nameSpaceSelector.

## Crie o nameSpace full-access

## Crie 2 pods nesse nameSpace: full-pod-a e full-pod-b

## Acesse o pod-c pelo pod-a

## Acesse o pod-b pelo pod-a

## Acesse o pod-a pelo pod-a

## Acesse o pod-a pelo pod-b

## Tente acessar o pod-a pelo pod-c

## Chame o serviço do pod-a através do pod full-pod-a

## Faça o mesmo com o pod-b

## Tente fazer o mesmo com o pod-c

## Crie a label acesso=liberado para o namespace full-access

## Tente novamente fazer o acesso ao pod-c através do full-pod-a

## Altere a netpol para liberar o tráfico apenas para o pod que possuí a label: run=full-pod-b e tenha a label acesso:liberado.

## Inclua a regra IpBlock na netpol para que apenas 10.0.0.0/8 esteja liberado

# Exercícios Egress

## Crie uma nova netpol para liberar a saída do pod-c apenas para o pod-a usando tcp e porta 80.

## Tente acessar o pod-a pelo pod-c

## Tente acessar o pod-b pelo pod-c

## Acesse o pod-c pelo pod-c

## Edite a netpol criada incluindo uma regra para liberar dns, use as portas 53 TCP e UDP (CoreDNS rodando no kube-system) e inclua a regra namespaceSelector 

# Exercícios Allow

## Crie uma netpol para liberar todo tráfego de entrada (Ingress)

## Crie uma netpol para liberar todo tráfego de saída (Egress)

# Exercícios Deny

## Crie uma netpol para bloquear todo o tráfego de saída (Egress)

## Crie uma netpol para bloquear todo o tráfego de entrada (Ingress)

## Crie uma netpol para bloquear todo o tráfego de saída e entrada.
