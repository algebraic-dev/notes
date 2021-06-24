# Scaling
- **Vertical Scaling** - é dar upgrade em uma maquina especifica. É bem ruim por que alguma hora os requerimentos vão chegar no estado-da-arte e vai ser impossivel escalar verticalmente o sistema.
- **Horizontal Scaling** - É mais facil você ter várias maquinas e isso não bate em um teto de recursos necessários.

### Load balancers
- DNS com round-robin as vezes pode dar errado se por má sorte um usuário ficar utilizando muito um servidor com TTL alto.
- Load balancers podem guardar um número que vê onde o usuário vai ir.
- Elastic Load Balancers for example.

### Shared State
- Não há como utilizar session se a arquitetura for somente serviços e o load balancer. Para isso temos que introduzir uma nova maquina, mas, caso ela fique offline... não há por que fazer a arquitetura vertical.
- **RAID** - Raids é uma junçaõ multiplos Hard Drives e voce consegue separar os dados entre os Hard drives. 
	- **RAID0** - Divide os dados entre os 2 Hard Drives por striping(botar um pouco de cada dado) assim fazendo com que fique um pouco mais rapida a escrita de dados.
	- **RAID1** - Faz espelhamento dos dados entre os 2 Hard drives fazendo com que caso um queime o outro fica intacto sem DownTime.
	- **RAID10** - Usa os 4 Hard drives com 2 Mirrors e 2 Stripes

###  Replications
- Voce pode replicar Master e Slave para dividir entre read e write ou só ter uma replicação simples pra evitar problemas.
- **Master-Master** Escrever em ambos e replica pra slaves.