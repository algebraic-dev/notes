# Manipulação de arquivos
## Diretórios do / 
- **/bin**: Arquivos/Comandos que podem ser executados por todos os usuários
- **/boot**: Diretório de arquivos de inicialização do SO
- **/dev**: Pseudo arquivos que representam varias coisas do hardware e sistema operacional.
- **/etc**: Arquivos de configuração do sistema
- **/home**: Diretórios de usuários comuns
- **/lib e /lib64**: Bibliotecas do sistema
- **/lost+found**: Arquivos corrompidos e verificações do sistema
- **/media e /mnt**: Diretórios de montagem do linux pra CD-ROM e pendrive 
- **/opt**: Diretório opcional de instalação
- **/proc**: Pseudo arquivos de coisas do processador e memória
- **/root**: Home do super usuário
- **/run**: Diretório de processos
- **/sbin**: Binários especificos para root
- **/srv**: Serviços de sistema
- **/sys**: Informações para serviços USB
- **/tmp**: Arquivos temporários
- **/usr**: Onde ficam instalados os programas do linux
- **/var**: Arquivos de tamanho variáveis (Logs, Arquivos de banco de dados e etc)
## Comandos
- **ls** Listar os arquivos e programas 
- **ls -lah** Lista todos os arquivos de forma longa com human-readable
	`d` = diretório
	`l` = syslink
	`-` = arquivo padrão
	`c` = formato caractere
	`b` = formato de bits
	`d rwx r-x r-- chiyo  docker` = 
		Diretório (`d`) de read write e execute para usuário (`rwx`),
		de read e execute para o grupo docker (`r-x`) e de read-only para todos os outros (`r--`)
- **pwd** Mostra o diretório atual
- **mkdir -p a/b/c**: cria pastas mesmo que não exista a pasta *a* (por causa do -p)
- **cp -Rvp a b** copia os arquivos de *a* para *b* recursivimente (-R), verbosamente (-v) e preservando as permissões (-p)
- **head -n 10 /proc/cpuinfo** le as primeiras 10 linhas de /proc/cpuinfo
- **tail -n 10 /proc/cpuinfo** pega as ultimas 10 linahs
- **less arquivo** é bom para navegar diferente do Cat
- **unzip -tv arquivo** Descompacta de forma verbosa (-v) e testar a integridade (-t)
- **tar -czvf pasta.tar.gz .** Cria o arquivo com nome pasta.tar.gz (-f), verbosamente (-v), comprimir com gzip (-z) e cria um novo arquivo (-c)
-  **ifconfig** estatisticas legais e coisas da internet
## Processos
- **ps -aux**: listar processos de todos usuários (-a) contendo uma explicação detalhada (-u) e com processos que não estão ligados ao terminal (-x)
- **kill pid**: Mata o processo
- **kill -SIGSTOP pid**: Pausa o processo
- **killall nome_do_processo**: Mata os processos com esse nome