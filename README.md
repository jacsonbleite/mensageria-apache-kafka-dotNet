# Mensageria e Consumo com Apache Kafka e .Net

Essa issue simula, de forma simples, um serviço - Message Broker - de um aplicativo de entregas de pedidos

O intuito é entender a didática aplicada a esse tipo de serviço. O Swagger foi utilizado para facilitar o uso da _API_

## Instanciando os serviços.

Na pasta raiz do projeto, digite o seguinte comando:

`docker-compose up -d`



## Utilizando a dashboard do Kafdrop para gerenciar o serviço:

`localhost:9007`



## Subindo e testando a API com Swagger no navegador:

Ainda no terminal e dentro da pasta do projeto digite o seguinte comando:

`dotnet watch run --project Net.Delivery.Order.Api``

Isso inciciará um servidor local  que será mostrado no terminal como _localhost:5000_

para acessar as _APIs_ no navegaor acrescente o parêmtro _/swagger_ ao endereço do servidor local, ex:

`localhost:5000/swagger`



## Utilizando o serviço:

Acessando container (kafika) em modo de edição:

`docker exec -it kafka /bin/bash`



## Listando Tópicos

`./kafka-topics --list --bootstrap-server localhost:9092`



## Criando um Tópico

`./kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic tp-order`

Uma mensegem como esta, abaixo, deve aparecer:
`Created topic tp-order.`



## Criando um consumidor para o Tópico

`./kafka-console-consumer --bootstrap-server localhost:9092 --topic tp-order --from-beginning`



## Iniciando o serviço de notificação de mensagens:

No terminal, dentro da pasta do projeto, digite o seguinte comando:
`dotnet watch run --project Net.Delivery.Order.Notifier`

Assim é possível verificar todas as mensgens do sitema.
