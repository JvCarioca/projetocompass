## Projeto-Compass

# Configuração do NFS:

Instalação do servidor NFS:
sudo yum install nfs-utils
EFS configurado pela AWS para instância:
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-069a843885dc623cc.efs.us-east-1.amazonaws.com:/ /nfs-aws
Habilitação e inicialização do serviço NFS:
sudo systemctl enable nfs-server
sudo systemctl start nfs-server
Criação de um Diretório no NFS:
sudo mkdir /nfs-aws/joao-victor


# Instalação e Configuração do Apache HTTP Server:
Instalação do servidor Apache HTTP:
sudo yum install httpd
Inicialização do Apache:
sudo systemctl start httpd
Habilitar o serviço para iniciar automaticamente na inicialização:
sudo systemctl enable httpd
Testando:
sudo systemctl status httpd


# Criação do Script de Validação do Serviço:
Criação do script de validação (check_apache_status.sh) usando um editor de texto vim.
Apliquei no script para aparição de DATA e HORA na validação.
SCRIPT no README.


# Agendamento Automatizado do Script:
Edição do arquivo /etc/crontab usando o editor vim para adicionar a execução periódica do script:
sudo vim /etc/crontab
Na ultima linha livre anexei: */5 * * * * root /srv/nfs/shared/joao-victor/check_apache_status.sh
