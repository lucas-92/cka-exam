# Ativar o autocomplete do kubectl

- echo 'source <(kubectl completion bash)' >>~/.bashrc
*Ativa o autocomplete do kubectl*

- source .bashrc
*Carrega o bash config que acabamos de criar*

- kubectl 
*Verifica se o autocomplete está funcionando*

# Identações do vim

## vim .vimrc
*Cria o arquivo .vimrc dentro da home do usuário para configurar o vim* 

## set expandtab
*Usa o tab como espaço*

## set tabstop=2
*Define 2 espaços para cada tab*

## set shiftwidth=2
*Define como 2 o espaço mantidos para baixo a cada identação*

# Alias do kubectl

## vim .bashrc

## alias k=kubectl

## complete -F __start_kubectl k

## alias kgd='kubectl get pod'

## alias kd='kubectl describe'

# Variável de ambiente para dry run

## export drun="--dry-run=client -o yaml"
*Usar variável com $drun*
