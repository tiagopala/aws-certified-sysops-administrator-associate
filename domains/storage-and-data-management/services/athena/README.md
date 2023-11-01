# Athena (Analytics)

<img height=100px; alt="athena" src="../../../../images/athena.png" />

O Athena é um serviço *serverless* de *analytics*, ou seja, através dele podemos capturar e analisar dados.

A principal feature do Athena é a possibilidade de realizarmos *queries* usando **SQL**, nos dados presentes em *buckets s3*.

> Não é necessário, por exemplo, realizarmos a extração dos dados via de ETL's.

## Pontos chave

- SQL Queries
- Integração nativa S3
- Serverless

## Casos de Uso

- *Query*: Capturar dados.
- *Generate*: Gerar relatórios à partir dos dados recuperados.
- *Cost Analysis*: Gerar relatórios de usos de custos.
- *Analyze*: Analisar dados.

## Configurando uma tabela

Caso seja a primeira vez que você esteja utilizando o Athena, você deverá criar um *bucket s3* a qual irá armazenar os resultados das queries realizadas.

Após realizada a configuração do *bucket*, podemos iniciar o *setup* inicial de nossas tabelas.

Para isso, devemos apenas criar uma *database* (dentro do Athena) e o *table schema* (modelo da tabela) da futura tabela a ser consultada.

> As *queries* podem ser realizadas imediatamente após a criação das tabelas.