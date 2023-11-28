# SQS - Simple Queue Service (Aplication Integration)

<img height=100px; alt="sqs" src="../../../../images/sqs.png" />

O SQS (Simple Queue Service) é um serviço de mensageria totalmente gerenciado pela da aws (*serverless*).

Seu principal benefício é **desacoplarmos** os componentes de *software* de maneira a atingir maior resiliência à falhas e prover maior manutenabilidade dos recursos computacionais.

Como mencionado anteriorimente, é um serviço de mensageria, ou seja, as mensagens enviadas são armazenadas em suas respectivas filas até serem consumidas e processadas.

## Benefits

Entre alguns benefícios de utilizarmos o SQS, podemos destacar:

- Simplificar a atualização de pequenos componentes de software.
- Reduzir o número de dependências sistêmicas.
- Aumentar o número de componentes e aplicações autônomas.
- Criar aplicações não-bloqueantes, ou seja, permite técnicas de retentativas e reprocessamento.
- Decomposição lógica dos sistemas.

## How it works?

Quando incluímos o *sqs* em nossa arquitetura, temos basicamente 3 papéis a serem exercidos.

- **Produtor**: São as aplicações, microsserviços ou outros serviços da aws a qual enviarão as mensagens.
- **Fila**: A fila, aonde as mensagens ficarão armazenadas até serem consumidas, papel desempenhado pelo SQS.
- **Consumidor**: Podem ser aplicações, microsserviços, *lambdas*, instâncias ec2, entre muitos outros serviços AWS, a qual consumirão e processarão as mensagens.

## Archictecture

TODO: Criar uma arquitetura desacoplada através do uso do SQS.