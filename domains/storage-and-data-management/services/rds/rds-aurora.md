# Aurora (Database - RDS)

<img height=100px; alt="aurora" src="../../../../images/aurora.png" />

É a engine proprietária da amazon e possui atualmente dois tipos: *[Aurora](#aurora)* and *[Aurora Serverless](#aurora-serverless)*.

## Aurora

### Aurora Auto Scaling

O *Aurora Auto Scaling* é uma feature que possibilita a adição de automática de *read Replicas* baseado nas métricas que escolhermos.

Essa configuração permite que o próprio *cluster* adicione ou remova *read replicas* para suportar picos, dessa forma, após o pico, replicas não utilizadas serão removidas.

Disponível apenas para as engines: Aurora MySQL e Aurora PostgreSQL. 

#### Aurora Auto Scaling Setup

Para criar um *RDS Auto Scaling*, devemos configurar:

1. Criar uma *Auto Scaling Policy* com as permissões necessárias para o RDS conseguir escalar os recursos.
2. Definir qual *CloudWatch Metric* será monitorado.
3. Definir um *Target Value*, representa o valor desejado de monitoramento da métrica escolhida.

Métricas disponíveis:

- Média do número de conexões.
- Média da utilização de CPU.

Os *target values* diferem para o tipo de métrica selecionado.

Para o número de conexões o *target value*, será o número de conexões permitidas para cada *read replica*.

Caso optarmos pela média de utilização de CPU, será a porcentagem aproximada.

> Podemos opcionalmente desabilitar a opção de *scaling-in actions*, responsáveis por remover as *read replicas* adicionais que não estão sendo mais utilizadas.

O padrão (default) para as *scaling actions* é de 300 segundos, porém pode ser ajustado conforme a necessidade.

APENAS para *scaling* de READ-REPLICAS.

**Aurora DB Cluster Volume:**

Utilização de *cluster volumes* para distribuir virtualmente os dados armazenados em múltiplas AZ's.

**Cache Warming**

Para não impactar na performance enquanto novas bases estão sendo provisionadas, o RDS pré-popula seu *buffer pool* com as *queries* mais comuns.

### Aurora Serverless

Diferente das outras engines, o *Aurora Serverless* se responsabiliza por toda a parte de escalabilidade por conta própria, não sendo necessário nenhuma configuração adicional ou se preocupar em monitorarmos estes recursos.

Todas as features já disponibilizadas pelo próprio Aurora também valem para o Aurora Serverless, exemplo: *Multi-AZ deployment*, *read-replicas*, *global database*, entre outros.

Ela é ideal para aplicações que não ainda não é possível prever o volume de tráfego e ainda assim é necessário alta disponibilidade.

### Aurora Resilience

Podemos considerá-la altamente **redundante**, pelo fato da replicação dos dados em 3 AZ's, com cada AZ possuindo 2 cópias, sempre teremos 6 cópias no total.

Outras duas features importantíssimas para garantir a resiliência do Aurora é o *self-repairing* e *self-healing*.

Em poucas palavras, o discos e blocos de armzenamento são continuamente *"scaneados"* para encontrar erros e realizar reparações automáticas caracterizando.