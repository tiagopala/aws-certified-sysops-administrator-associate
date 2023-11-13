# Elasticity & Scalability

Para um *sysops admin*, elasticidade e escalabilidade são dois conceitos que devem estar muito claro em seu dia a dia.

## Elasticity

O primeiro deles, elasticidade, refere-se a habilidade da sua infraestrutura em conseguir escalar de acordo com a demanda requerida pela aplicação.

Quando pensamos nela, devemos imaginar um curto período de tempo, visto que geralmente são picos de acessos temporários.

Ou seja, após este pico, a tendência é que a infraestrutura seja reduzida para comportar aquele novo número de acessos.

> Importante lembrar que o modelo *pay as you go*, aqui é de extrema importância, pois seremos cobrados apenas pelo tempo/recursos que realmente utilizarmos, sem excessos.

## Scalability

O segundo deles, escalabilidade, é a habilidade de conseguirmos evoluir forma definitiva a nossa infraestrutura.

Neste caso, devemos imaginar um longo período de tempo, pois já temos que ter a volumetria bem concreta e assim escolher a melhor forma de escalar nossa infraestrutura.

Aqui não pensamos mais em picos de acesso, mas sim de aplicações já consolidadas que possuem uma volumetria bem definida e já conhecida.

Com isso, podemos por exemplo re-avaliar a necessidade de escolher novas instâncias *ec2* mais potentes que suprem esta nova demanda.

### Serviços

Abaixo temos uma relação de alguns serviços e como eles realizam ambas funções de elasticidade e escalabilidade:

| Serviço       | Elasticidade                                                         | Escalabilidade                                                |
| ------------- | -------------------------------------------------------------------- | ------------------------------------------------------------- |
| EC2           | Uso Auto Scaling para aumentar quantidade de instâncias              | Aumentar o tamanho das instâncias / Usar *reserved instances* |
| DynamoDB      | Aumentar/diminuir IOPS baseado em picos de tráfego                   | DynamoDb já possui escalabilidade nativa para armazenamento   |
| RDS           | Não possui features para escalar sob-demanda                         | Aumentar o tamanho da instância / Adicionar mais instâncias   |
| Amazon Aurora | Escala automaticamente para cima ou para baixo para suprir a demanda | Modificar o tipo de instância                                 |
