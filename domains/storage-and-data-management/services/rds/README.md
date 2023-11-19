# RDS (Database)

<img height=100px; alt="rds" src="../../../../images/rds.png" />

RDS é a base de dados relacional da amazon, sendo compatível com as principais engines *open source* do mercado como MySQL e PostgreSQL, entre outras.

Além destas, o RDS também possui o [Aurora](./rds-aurora.md#aurora), uma base de dados relacional *serverless* da própria amazon, compatível com as duas *engines open source* mencionadas acima.

Um dos grandes benefícios de se utilizar o RDS é a combinação dele ser um serviço gerenciado pela amazon, provendo maior rapidez, performance e escalabilidade.

Além dele possuir features como: *fault-tolerant* e *self-healing*, a qual diminuem o risco de perda de informações.

## Resilience

### Multi-AZ (Failover)

É um recurso do RDS focado em *disaster recovery*.

Por baixo dos panos, o RDS realiza a replicação de todos os dados da base primária para a base segundária.

Em um cenário de alguma eventualidade/anormalidade, não perderemos acesso nossos aos dados.

Pois a AWS se responsabiliza de realizar o *automatic failover* para nós, ou seja, eles mesmos atualizam o DNS da base principal para a base secundária.

Um ponto super importante de termos em mente é que o Multi-AZ NUNCA deve ser pensado/relacionado à performance/escalabilidade, sempre à prevenção à falhas.

> Podemos provocar um *failover* através do *reboot* da base principal, através do console ou através da chamada da *API RebootDBInstance*.

Entre as principais vantagens de utilizarmos o Multi-AZ, podemos destacar:

- Alta disponibiidade dos dados.
- Geração de *backups* e *restores* à partir da base secundária, sem impactar o desempenho da base principal.

**Replication**

**MySQL, Oracle e PostgreSQL** possuem uma **replicação física** dos dados na base secundária, enquanto para o **SQL Server** ocorre uma **replicação lógica**. 

As replicações provenientes do Multi-AZ sempre são realizadas de forma **síncrona**.

> Todas *engines* asseguram contra perda de seus dados de *DB instance failure* ou a perda de uma AZ.

### Performance

#### Read Replicas

É um recurso com foco no aumento na performance do RDS.

Elas são basicamente cópias *read only* da base de dados primária, para auxiliar em pesadas cargas de trabalho de leitura (*read-heavy workloads*).

Devemos utilizá-las quando for necessário capacidade de leitura adicional, ou seja, as leituras serão realizadas na *read replica* em vez da base de dados primária.

**Read Replicas Replication Data**

As *read replicas* se beneficiam de funcionalidades de replicação nativas das próprias *engines*.

Importante ressaltar que nem todas as *engines* possuem essa capacidade nativa.

As que possuem suporte, permitindo assim, escalar além das limitações de capacidade da própria instância para *read-heavy worloads*.

Nas seguintes engines: MySQL, PostgreSQL, MariaDB, SQL Server, é utilizado o modelo de replicação nativo de cada uma delas.

Já no caso do Aurora, é utilizado uma camada de armazenamento virtual suportados por SSS's.

**Scheduled Maintenance e *Backups***

Uma boa prática é utilizar-se de *read replicas* em conjunto com manutenções programadas e *backups*.

Dessa forma, poderemos continuar consumindo os dados à partir das *read replicas* mesmo que a base de dados primária não estiver disponível para I/O (estiver momentaneamente suspensa devido a manutenções programadas ou estiver realizando um *backup*).

**Business Reporting e Data Warehousing**

Outro caso de uso é a extração de relatórios de negócios através de grandes, extensas e complexas *queries* à partir das *read replicas*.

**Creating and Connecting**

Para criação de uma nova *read replica*, é necessário a realização de um *snapshot*.

Se o *Multi-AZ* estiver habilitado, este *snapshot* ocorrerá à partir da base de dados secundária, sem impactos na base primária.

Caso não, ele será tirado à partir da base primária, tendo uma suspensão de I/O de aproximadamente 1 minuto.

Após criado a *read replica*, será gerado um novo *endpoint* (*endereço de DNS*).

**Read Replicas Tips**

- Podemos ter até 5 *read replicas* para MySQL, PostgreSQL, SQL Server e MariaDB.
- *Read replicas* podem ser *same AZ*, *cross-AZ* (*multi-AZ*) ou até *cross-region*.
- A replicação dos dados para as *read replicas* sempre ocorre de forma **assíncrona**.
- É possível ter *read replicas* à partir de outra *read replicas*, porém cuidado com a latência.
- *DB Snapshots & Automated Backups* podem ou não serem possíveis dependendo do tipo de engine escolhida.

**Read Replicas Additional Content**

- [Página oficial da aws referente às read replicas](https://aws.amazon.com/pt/rds/features/read-replicas/)
- [FAQ oficial sobre read replicas](https://aws.amazon.com/pt/rds/faqs/#Read_Replicas)
- [Documentação oficial das read replicas](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html)

## Monitoring

Os dois cenários mais comuns de monitoramento são geralmente referentes a capacidade de leitura ou escrita.

Caso nossa base RDS esteja sofrendo com a capacidade de escrita o aconselhável é escalarmos o banco através da melhoria do tipo da instância.

Por outro lado, caso o maior impacto seja na leitura e captura dos dados, devemos aumentar o número de *read-replicas*.

Uma métrica importante para termos em mente é a *REPLICA LAG*, quando estivermos monitoramento *read replicas*.

## Encryption

Para criptografarmos um banco de dados RDS que não possui criptografia, devemos realizar os seguintes passos:

1. Criar um *snapshot* do banco a ser criptografada.
2. Criar uma cópia do *snapshot* para outra região ou para a mesma.
3. Habilitar a opção de criptografia.
4. Restaurar um novo banco à partir do *snapshot* criptografado.

### Snapshots

*Snaphots* são basicamente cópias do banco naquele exato momento em que o snapshot foi tirado.

Eles podem ser gerados manualmente ou através da *feature: automated backups* (backups automáticos).

**Sharing Snapshots**

Eles podem ser compartilhados com outras contas através do *AWS Console*, *AWS CLI* ou *Api do RDS*.

Caso nosso *snapshot* compartilhado esteja criptografado, devemos compartilhar juntamente a chave de criptografia do KMS.

**Encryption Tips**

- Criar um *snapshot* à partir de um banco sem criptografia resultará também em um *snapshot* sem criptografia.
- *Snapshots* criados à partir de bancos criptografados também serão criptografados.
- A criptografia pode ser habilitada no momento da criação do banco.
- Não há forma "simples" de criptografar uma base de dados.

## RDS Underlying Architecture

![rds-db-cluster-underlying-architecture](../../../../diagrams/rds-db-cluster-underlying-architecture.drawio.png)

