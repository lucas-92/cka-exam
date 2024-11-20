k run command --image nginx --command --dry-run=client -o yaml -- /bin/sh -c env > command.yaml

k run command --image nginx --command --dry-run=client -o yaml -- /bin/sh -c "sleep 1d" > command.yaml
