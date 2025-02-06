1. Onde fica definido o método RBAC?

No kube-apiserver.yaml, no kind está dentro do node control-plane. O diretório padrão é /etc/kubernetes/manifests/kube-apiserver.yaml
```
cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep authorization-mode
    - --authorization-mode=Node,RBAC

```
&unit=65b4de45379f34ad950069eaUnit

&unit=66858a4fe5948d045f0cf31dUnit
