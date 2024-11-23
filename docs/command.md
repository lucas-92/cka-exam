k run command --image=nginx --command --dry-run=client -o yaml -- /bin/sh -c env > command.yaml

k apply -f command.yaml

k get pods

k logs command

k run command --image=nginx --command --dry-run=client -o yaml -- /bin/sh -c "sleep 1d" > command.yaml

k replace -f command.yaml --force

k get pods

k exect -ti command -- bash

ps

apt update

apt install procps

psaux

k run command --image=nginx --dry-run=client -o yaml > command.yaml

k replace -f command.yaml --force

k get pods

k exect -ti command -- bash

apt update

apt install procps

psaux

