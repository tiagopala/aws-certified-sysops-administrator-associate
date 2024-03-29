# CloudWatch (Management & Governance)

<img height=100px; alt="cloudwatch" src="../../../../images/cloudwatch.png" />

CloudWatch é um serviço de **monitoramento** capaz de monitorar a **saúde** e **performance** dos recursos e aplicações que estão rodando na AWS e até mesmo em seu próprio data center.

## Features

### CloudWatch Logs

O objetivo dos logs no cloudwatch é conseguirmos monitorar e realizar o *troubleshooting* de nossas aplicações através de *logs files* (arquivos de log).

#### Características

- **Acesso centralizado**: Logs de aplicação (.NET logs), sistemas operacionais (Linux/EC2 logs) e serviços/recursos AWS (CloudTrail/Route 53) tudo no mesmo lugar.
- **View, Search & Filter**: Permite visualizarmos, procurar e até filtrar por logs específicos: Exemplo: "Status Code 404 lambda XYZ"
- **Notifications**: Permite integração com o SNS, dessa forma é possível criar alertas através de notificações. Exemplo: "Status Code 500 microsserviço XYZ acima de 15% nos últimos 15 minutos."
- **Near real-time**: Logs são próximos ao tempo real.
- **CloudWatch Agent**: Necessária instalação do *Agent* para envio dos *logs*. Exemplo: Instâncias EC2 e aplicações on-premises.

#### Terminologia

- **Log Events**: O evento de *log* é sempre composto por uma **mensagem** e o **timestamp** que ocorreu.
- **Log Stream**: É uma sequência de *log events*, deve permanecer há um grupo.
- **Log Group**: Agrupamento de *log streams*, possui **controle de retenção, monitoramento e controle de acessos centralizado**. Não possui limite de log streams em um único log group.

#### Configurações de Retenção

Por padrão todos os logs enviados ao CloudWatch Logs são **armazenados indefinitivamente**.

É possível definir um período de retenção entre **1 dia - 10 anos**.

Logs de eventos expirados são deletados automaticamente.

O controle de retenção pode ser aplicado em **nível de log group**.

#### CloudWatch Metrics Filter

É uma feature que permite criarmos métricas à partir de palavras ou frases presentes nos *logs*.

Após criadas, podemos adicionalmente criar alertas baseados nesta métrica para nos notificar em caso de comportamentos adversos em nossa aplicação.

Filtros comuns: *'warnings'*, *'errors'* ou *'http status codes'* específicos, exemplo: 500 ou 400.

##### Como criar um metric filter?

1. Escolher o *log group* a qual será criado o metric filter.
2. Definir o padrão de busca (*filter pattern*), exemplo: 'warning'.
3. Opcionalmente, podemos testar o padrão mencionado acima em logs reais.
4. Criar um *metric namespace*, *metric name* e *metric value*
5. Opcionalmente, podemos também definir um valor *default* e a unidade de medida.

#### CloudWatch Log Insights

É uma feature para *troubleshooting*, através dele podemos rodar *queries* em vários *log groups* de uma só vez e assim conseguir identificar, rapidamente, eventuais problemas ou simplesmente analisar a saúde da sua aplicação. 

Essas *queries* realizadas, por sua vez, podem ser salvas para futuras consultas, além do próprio cloudwatch insights já fornecer algumas queries de exemplos. Exemplo: 'Exiba os 25 últimos eventos de logs adicionados'.

Podemos adicionalmente, criar visualizações à partir dos dados retornados nas queries. Exemplo: Gráficos de barras, gráficos em linhas, gráfico de pizza, entre outros.

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

### CloudWatch Dashboards

Permite a criação de dashboards de monitoramento customizados com base nas métricas disponíveis no CloudWatch Metrics.

Esses dashboards podem criados com métricas padrão já disponibilizados pelo CloudWatch, como também métricas customizadas.

#### Características 

- Dashboards são *multi-region*, ou seja, em um único *dashboard* podemos criar visualizações para uma ou mais regiões.
- Devemos sempre salvar nossos *dashboards* visto que o CloudWatch não salva automaticamente.

### CloudWatch Alarms

É uma feature do CloudWatch, a qual permite criarmos **alarmes de monitoramento** à partir de qualquer *CloudWatch Metric* presente em sua conta e alertar assim que algum *threshold* for atingido, e devido possuir integração nativa com o SNS, podemos enviar notificações à partir destes alertas.

O CloudWatch Alarms possui integração nativa com o SNS dessa forma podemos, por exemplo, enviar notificações (incluindo e-mails) informando que um alarme foi acionado.

Exemplo: Acionar este alarme caso o uso de CPU de uma instância EC2 exceda 90% (threshold) nos últimos 5 minutos (período) e envie um e-mail ao time de suporte de TI (integração via SNS).

#### Alarmes + Service Quotas 

Através do console do *Service Quotas* podemos também, criar alarmes para notificar quando estivermos prestes a atingir o limite de algum serviço da aws.

Exemplo: Atingimos 90% da quota/limite para instâncias EC2 do tipo On-Demand.

#### Alarmes + Health Events

Através da *AWS Health API* podemos verificar a saúde dos nossos recursos e em conjunto com o EventBridge podemos capturar e usar estes eventos de erro para *'triggar'* um CloudWatch Alarm que por sua vez irá *'triggar'* uma função lambda ou enviar uma mensagem à uma fila SQS.

### CloudWatch Agent

Através do CloudWatch Agent, podemos:

- Criar métricas customizadas e enviá-las ao *CloudWatch Metrics*.
- Criar e enviar logs ao *CloudWatch Logs*.

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