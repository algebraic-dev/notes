# Agendamento de tarefas
- **crontab -u root -e** 
	- `-u` Qual usuário 
	- `-e` Edição
	
# Firewall
- **iptables -F** Flush em todas regras
- **iptables -X** Deleta regras 
- **iptables -P INPUT ACCEPT** Aceita input
- **iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT** -Aceita conexão somente na porta 80
- **iptables -L** mostra regras pré estabelecidas

## Port knocking
- **knockd** - Deamon pra knocking
	- utiliza o arquivo `/etc/knock.d` e o `/etc/default/knock.d`