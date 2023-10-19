# Amazon EventBridge (Application Integration)

<img height=100px; alt="amazon-eventbridge" src="../../../images/amazon-eventbridge.png" />

O EventBridge é um serviço *serverless* da AWS responsável por criarmos aplicações orientadas à eventos.

## Features

### Event-driven architectures

Permite a criação de arquiteturas orientadas a eventos, através do mapeamento dos eventos disparados pelos serviços e com ações a serem executadas por outros serviços.

### Schedule events

Adicionalmente, o EventBridge também permite a criação de eventos que serão executados em um horário agendado.

Exemplo: Todo dia às 10 da noite disparar um evento que irá *triggar* uma *lambda* para gerar um relatório do fechamento contábil do dia.

## EventBridge vs CloudWatch Events

Ambos os serviços utilizam por baixo dos panos as mesmas API's, porém atualmente o EventBridge é o serviço mais aconselhado para integrações de eventos.

## Terminologia

- **Events**: São alterações de estado gerados por recursos/serviços da AWS. Exemplo: Inserção de um novo item em uma tabela do dynamo.
- **Rules**: Mapeamento (de/para) entre os eventos disparados com os targets desejados.
- **Targets**: Serviço que irá receber aquele determinado evento para executar uma ação. Exemplos: Lambdas, SNS, EC2, entre outros.