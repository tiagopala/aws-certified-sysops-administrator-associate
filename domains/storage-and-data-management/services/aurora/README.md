# Aurora (Database)

<img height=100px; alt="aurora" src="../../../../images/aurora.png" />

Aurora é a base de dados relacional da amazon, sendo compatível com MySQL a PostgreSQL.

Um dos grandes benefícios de se utilizar o Aurora é a combinação dele ser um serviço gerenciado pela amazon, provendo maior rapidez, performance e escalabilidade.

Com a utilização de bases de dados *open source* já conhecidos no mercado.

Além dele possuir features como: *fault-tolerant* e *self-healing*, a qual diminuem o risco de perda de informações.

## Features and Characteristics

### Aurora DB Cluster Volume

Utilização de *cluster volumes* para distribuir virtualmente os dados armazenados em múltiplas AZ's.

### Storage Auto Scaling

As engines MySQL e PostgreSQL possuem customizações para beneficiarem-se de um rápido armazemaneto distruíbido podendo escalar até 128 TiB.

### Redundancy & Self-Repairing Storage 

Pelo fato do Aurora replicar os dados armazenados em 3 AZ's tendo cada AZ 2 cópias daqueles dados, podemos considerá-la altamente redundante, além dos discos e blocos de armzenamento serem continuamente *"scaneados"* para encontrar erros e realizar reparações automáticas caracterizando o *self-repairing*/*self-healing*.

> Ao todo temos sempre 6 cópias dos dados.

### Cache Warming

Para não impactar na performance enquanto novas bases estão sendo provisionadas, o Aurora pré-popula seu *buffer pool* com as *queries* mais comuns.

## Monitoring Aurora

Os dois cenários mais comuns de monitoramento são geralmente referentes a capacidade de leitura ou escrita.

Caso nosso aurora esteja sofrendo com a capacidade de escrita o aconselhável é escalarmos o banco através da melhoria do tipo da instância.

Por outro lado, caso o maior impacto seja na leitura e captura dos dados, devemos aumentar o número de *read-replicas*.

## Aurora Serverless

É outro tipo de engine que odemnos escolher no momento que estivermos criando nosso cluster do aurora, send o Aurora Serverless uma engine proprietária da amazon.

Diferente das outras engines, o Aurora Serverless se responsabiliza por toda a parte de escalabilidade por conta própria, não sendo necessário nenhuma configuração adicional ou se preocupar em monitorarmos estes recursos.

Todas as features já disponibilizadas pelo próprio Aurora também valem para o Aurora Serverless, exemplo: *Multi-AZ deployment*, *read-replicas*, *global database*, entre outros.

Ela é ideal para aplicações que não ainda não é possível prever o volume de tráfego e ainda assim é necessário alta disponibilidade.

## Aurora Underlying Architecture

TODO