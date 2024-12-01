Criar um PV, PVC e Montá-lo dentro do pod

Criar PV

Criar PVC

Monstar no POD


hostPath - HostPath volume plugin
vim meupv.yaml

apiVersion: v1
kind: PersistentVolume
metadata:
  name: meu-pv
spec:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 1Gi
  hostPath:
    path: /volume

k apply -f meupv.yaml

k get pv

k describe pv meu-pv

accessmod

hostpath

capacity
