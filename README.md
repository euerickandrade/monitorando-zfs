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

1 - Confira se o pacote zfsutils-linux esta instalado, caso nao esteja faca a instalacao pois ele e necessario para a execucao do monitoramento.

`# apt install zfsutils-linux`

2 - Acesse o diretorio do Zabbix Agent e baixe o arquivo de configuração dos parametros.

`# cd /etc/zabbix/zabbix_agentd.d`
