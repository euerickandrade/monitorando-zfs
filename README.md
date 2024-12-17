# Monitorando ZFS em ambiente Linux com Zabbix

Autor: Erick Andrade  
Instagram: @erickandrade_  
Telegram: @erickandrade  
Site: https://www.erickandrade.com.br/  
E-mail: erick@erickandrade.com.br  
Versão: 1.0  


O Template serve para monitorar o status do ZFS em ambientes que usam distribuições GNU/Linux, inclusive o ProxmoxVE que por baixo está utilizando o Debian.

Outro parâmetro utilizado no template é que ele irá reportar o uso de Memória RAM feito pelo processo do ZFS.

Para ajuda no monitoramento do ambiente será utilizado o pacote zfsutils-linux, para mais informações acesse a Documentação Oficial da ferramenta.

Documentação OpenZFS: (https://openzfs.github.io/)  
Documentação ZFS: (https://docs.oracle.com/cd/E24849_01/html/820-0447/zfsover-2.html)](https://docs.oracle.com/cd/E24849_01/html/820-0447/zfsover-2.html)  

**Versão do Zabbix**: 6.0 LTS e 7.0 LTS  
**Versão do Debian e ProxmoxVE**: Debian 11, Debian 12 e ProxmoxVE 8.2.2

# Nota
**Apesar de funcionar perfeitamente, o projeto ainda não está finalizado com todas as funcionalidades que quero.**  

# Configurando o Monitoramento

1 - Confira se o pacote zfsutils-linux esta instalado, caso nao esteja faca a instalacao pois ele e necessario para a execucao do monitoramento.

`# apt install zfsutils-linux`

2 - Acesse o diretorio do Zabbix Agent e baixe o arquivo de configuração dos parametros.

`# cd /etc/zabbix/zabbix_agentd.d`

`# wget https://raw.githubusercontent.com/euerickandrade/monitorando-zfs/refs/heads/main/monitoramento-zfs.conf`

**Para ver o total de Leitura/Escrita das Operações e Largura de Banda da Leitura/Escrita de cada Pool, substitua o nome da Pool no campo "minhapool" dentro do arquivo monitoramento-zfs.conf.**  

3 - Defina o proprietario, grupo e o modo do arquivo userparams.

`# chown root:zabbix monitoramento-zfs.conf`  

`# chmod 0440 monitoramento-zfs.conf`  

4 - Baixe e instale o Agent do Zabbix no Host que será monitorado.

Você precisa ter as informações da vesão do Linux/ProxmoxVE e Zabbix Server para instalar o agente correto. Em meu exemplo será o Debian 12 que roda no ProxmoxVE 8.2.2 e o Zabbix Server 7.0 LTS.

Acesse o site do Zabbix e baixe a versão correta. (https://www.zabbix.com/br/download)

Baixe o .deb  

`# wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.0+debian12_all.deb`

Instale o pacote  

`# dpkg -i zabbix-release_latest_7.0+debian12_all.deb`

Atualize o repositório do Linux  

`# apt update`

Instale o Zabbix Agent  

`# apt install zabbix-agent`

Edite o arquivo do Zabbix Agent para definir os parâmetros Server, ServerActive e Hostname  
Adicione o IP do seu Servidor Zabbix e o nome do seu Host.

`# nano /etc/zabbix/zabbix_agentd.conf` 

Reinicie o servico do Zabbix Agent no servidor   

`# systemctl restart zabbix-agent`  

5 - Configure os templates abaixo no Host para ter o monitoramento ZFS.

Nomes:

  Linux by Zabbix agent  
  Monitoramento ZFS por Erick Andrade  
