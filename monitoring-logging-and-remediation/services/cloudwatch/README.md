# CloudWatch (Management & Governance)

<img height=100px; alt="cloudwatch" src="../../../images/cloudwatch.png" />

CloudWatch é um serviço de **monitoramento** capaz de monitorar a **saúde** e **performance** dos recursos e aplicações que estão rodando na AWS e até mesmo em seu próprio data center.

## Features de Monitoramento

### CloudWatch Agent

Uma característica importante que o agente do CloudWatch oferece é o poder de criar suas próprias métricas.

### CloudWatch Logs

Através do CloudWatch Logs, podemos medir e monitorar sistema operacional assim como nossa aplicação.

### CloudWatch Metrics

#### Host-level Metrics

As *host-level metrics* são sempre enviadas por padrão, e referem-se a própria instância em si. Ela consiste nas seguintes métricas:

- CPU
- network (rede)
- disco
- status check

#### System-level Metrics

Por padrão, as *system-level metrics* NÃO são enviadas por padrão ao CloudWatch.

Para começarmos a coletar e enviar esses dados, devemos instalar o CloudWatch Agent nas instâncias EC2.

Consiste nas seguintes métricas:

- Uso de memória
- Processos/Serviços rodando na instância
- Quantidade espaço disponível em disco
- Tempo de CPU ocioso

#### Metric Frequency

Por **padrão** as métricas são enviadas ao CloudWatch em um intervalo de **5 minutos**.

Se quisermos um acompanhamento mais detalhado podemos habilitar o **detailed monitoring** e passar a enviar em um intervalo de 1 minuto por um **custo adicional**.

As **métricas customizadas** são enviadas em um intervalo de 1 minuto, porém podemos configurar **high-resolution metrics** e passar a enviar em um intervalo de **1 segundo**.

#### Armazenamento

Todas as métricas enviadas ao CloudWatch são armazenadas por tempo indefinido e podemos recuperá-las mesmo se a instância EC2 ou ELB já estiver sido terminada.

## Integrações

### Compute

- Instâncias EC2
- Auto scaling groups
- Elastic Load Balancers (ELB)
- Route 53 Health Checks
- Lambdas

### Databases & Analytics

- Tabelas DynamoDb
- Nós do ElastiCache
- Instâncias RDS
- Redshift
- Elastic Map Reduce

### Storage & Content Delivery

- Volumes EBS
- Storage Gateway
- CloudFront

### Others

- Tópicos SNS
- Filas SQS
- API Gateway
- Estimated AWS Charges (custos)