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

# Exercícios

## Crie 3 pods: pod-a, pod-b e pod-c. Use a imagem do nginx e a porta 80.

## Crie 3 serviços para expor os pods criados use porta 80 e target-port 80.

## Crie uma regra onde somente o pod-a pode acessar o pod-c.

