# Amazon EventBridge (Application Integration)

<img height=100px; alt="amazon-eventbridge" src="../../../images/amazon-eventbridge.png" />

O EventBridge é um serviço *serverless* da AWS responsável por criarmos aplicações orientadas à eventos.

## Features

### Event-driven architectures

Permite a criação de arquiteturas orientadas a eventos, através do mapeamento dos eventos disparados pelos serviços e com ações a serem executadas por outros serviços.

### Schedule events

Adicionalmente, o EventBridge também permite a criação de eventos que serão executados em um horário agendado.

Exemplo: Todo dia às 10 da noite disparar um evento que irá *triggar* uma *lambda* para gerar um relatório do fechamento contábil do dia.

## AWS Config + Amazon EventBridge

Podemos adicionalmente *'triggar'* (desencadear) ações quando o AWS Config detectar que algum de nossos recursos não estão em conformidade.

Neste exemplo, iremos enviar um e-mail sempre que um recurso estiver em não conformidade, para isso devemos:

1. Criar uma *aws config rule*, a qual será responsável por verificar se o recurso está *compliance*.
2. Criar um *SNS topic* e uma *SNS subscription* sendo o *target* nosso e-mail. 
   > Essa é a ação a qual será desencadeada, podemos criar/configurar diferentes ações conforme a necessidade.
3. Criar uma *eventbridge rule* em que o *event pattern* será basicamente as alterações de *compliance* do *aws config* e o *target* será o tópico SNS criado acima.

Assim, toda vez que o aws config detectar um recurso que não esteja de acordo com as regras configuradas em nosso ambiente, ele irá enviar um evento ao *amazon eventbridge*, a qual irá enviar encaminhar este evento ao tópico SNS que por sua vez, através da subscription irá nos enviar um e-mail informando qual regra foi quebrada e qual recurso a quebrou.

## EventBridge vs CloudWatch Events

Ambos os serviços utilizam por baixo dos panos as mesmas API's, porém atualmente o EventBridge é o serviço mais aconselhado para integrações de eventos.

> O *CloudWatch Events* foi depreciado, portanto agora somente podemos criar a alterar nossas rules através do console do *EventBridge*. 

## Terminologia

- **Events**: São alterações de estado gerados por recursos/serviços da AWS. Exemplo: Inserção de um novo item em uma tabela do dynamo.
- **Rules**: Mapeamento (de/para) entre os eventos disparados com os targets desejados.
- **Targets**: Serviço que irá receber aquele determinado evento para executar uma ação. Exemplos: Lambdas, SNS, EC2, entre outros.