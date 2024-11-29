
# Exercícios: Persistent Volumes (PV) e Tipos de Volume no Kubernetes

## **1. Tipos de Volumes**

Liste os tipos de volumes suportados pelo Kubernetes e associe-os aos cenários corretos:

**Exercício 1.1**  
Associe o tipo de volume ao provedor correto:  
- **awsElasticBlockStore**  
- **azureDisk**  
- **gcePersistentDisk**  
- **cinder**  

**Exercício 1.2**  
Explique em poucas palavras as diferenças entre os volumes **hostPath**, **nfs** e **cephfs**.  

**Exercício 1.3**  
Qual volume você utilizaria para criar um volume persistente em um ambiente de armazenamento compartilhado na rede? Justifique.  

---

## **2. Primeiro PV**

**Exercício 2.1**  
Analise o YAML abaixo e identifique os erros:  
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: primeiroPV
spec:
  storageClassName: ""
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOne
  hostPath:
    patch: "/volume"
```

**Exercício 2.2**  
Reescreva o YAML acima corrigindo os erros identificados.  

---

## **3. Capacidade**

**Exercício 3.1**  
Explique o significado do seguinte bloco YAML:  
```yaml
capacity:
  storage: 1Gi
```

**Exercício 3.2**  
Converta a capacidade de 1Gi para Mi e reescreva o YAML.  

---

## **4. VolumeMode**

**Exercício 4.1**  
Qual a diferença entre os valores `Filesystem` e `Block` em `volumeMode`?  

**Exercício 4.2**  
Adicione o campo `volumeMode` ao YAML abaixo e configure-o para `Block`:  
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: volumeExemplo
spec:
  capacity:
    storage: 500Mi
  accessModes:
    - ReadWriteOnce
```

---

## **5. accessModes**

**Exercício 5.1**  
Diferencie os modos de acesso: **ReadWriteOnce**, **ReadOnlyMany** e **ReadWriteMany**.  

**Exercício 5.2**  
Dado o cenário de um cluster Kubernetes com 3 nós, escolha o modo de acesso mais adequado para:  
1. Um volume de leitura/escrita compartilhado por todos os nós.  
2. Um volume montado com leitura e escrita por apenas um nó.  

---

## **6. Reclaim Policy**

**Exercício 6.1**  
Explique o impacto de configurar a política de retenção como `Recycle`.  

**Exercício 6.2**  
Crie um exemplo YAML de PV configurado para deletar o volume quando o PVC for excluído.  

---

## **7. Class**

**Exercício 7.1**  
O que representa o campo `storageClassName` no YAML abaixo?  
```yaml
storageClassName: "Slow"
```

**Exercício 7.2**  
Altere o YAML abaixo para configurar a classe de armazenamento como `Fast`:  
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: meuPV
spec:
  storageClassName: "Slow"
  capacity:
    storage: 2Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/data"
```

---

## **8. hostPath**

**Exercício 8.1**  
Explique a diferença entre os valores **FileOrCreate** e **DirectoryOrCreate** no campo `type` do `hostPath`.  

**Exercício 8.2**  
Complete o YAML abaixo configurando o `hostPath` para criar um diretório vazio, caso não exista:  
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: hostPathPV
spec:
  capacity:
    storage: 500Mi
  accessModes:
    - ReadWriteOnce
  hostPath:
```

---

Boa prática e aprendizado! 🚀
