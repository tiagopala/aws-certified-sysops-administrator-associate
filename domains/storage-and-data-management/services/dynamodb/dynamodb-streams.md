# DynamoDB Streams

É uma *feature* do DynamoDB responsável por disponibilizar a sequência ordenada de eventos que aconteceram com cada item presente na tabela.

Ou seja, todas as operações - *Inserts*, *Updates* e *Deletes* - serão capturadas e enviadas através de *stream events*.

Estes eventos por sua vez, poderão ser usados como gatilhos para acionar outros fluxos em resposta a estes eventos.

> Todos os eventos ficam armazenados por até 24 horas.

## Casos de Uso

**Global Table Replicas:** 

O uso do *DynamoDB Streams* em conjunto com *global table replicas* permite a replicação dos dados para outras regiões.

Dessa forma, estamos criando uma *multi-region redundancy* para recuperação à desastres e provendo um aumento da disponibilidade.

Além da capacidade de criar aplicações globalmente distribuidas, pelo fato de termos nossos dados em diversas regiões espalhadas pelo planeta.

> Os dados são replicados em menos de 1 segundo, sendo praticamente instantâneo.