# Amazon Opensearch Service (Analytics)

<img height=100px; alt="amazon-opensearch" src="../../../../images/amazon-opensearch.png" />

O Amazon Opensearch Service, previamente chamado de *Amazon Elasticsearch Service*, é um serviço de *analytics*.

Ele provê um **serviço totalmente gerenciado** para trabalharmos com o **Elasticsearch** (*fully managed elasticsearch service*).

## O que é Elasticsearch?

Antes de entrarmos de fato nas peculiaridades do Opensearch, devemos primeiramente entender os conceitos do Elasticsearch.

O Elasticsearch inicialmente era um tecnologia *open source* porém, após o sucesso da tecnologia, os criadores fundaram a Elastic Company.

A partir deste momento, o Elasticsearch se tornou o principal produto da companhia sendo comercializado através de licenças.

O principais objetivos em utilizar-se desta tecnologia é o ganho em **Análise de dados** e **Observabilidade**.

## Características/Benefícios do Opensearch

Devido a complexidade para configuração e administração de um *cluster* do Elasticsearch, os principais benefícios são:

- Provisionamento do *hardware* e configuração do *cluster*.
- Instalação do *software*, controle de versão e *patching*.
- Recuperação contra falhas, *backups* automáticos e monitoramento.

Ou seja, a AWS se responsabiliza por prover toda a infraestrutura e resiliência necessária do nosso cluster.

## Funcionamento & Features

- [Arquitetura do Opensearch](./opensearch-architectural.md)

## Compatibilidade

Devido utilizar a mesma tecnologia elastic por baixo dos panos, ele é compatível com:

- API's nativas do Elasticsearch.
- Ferramentas de mercado como Logstash e Kibana.

## Integração Serviços AWS

Ele possui integração com os serviços abaixo:

- CloudWatch Logs
- Kinesis Data Firehose
- S3
- DynamoDB (Por meio do stream dos dados através de uma Lambda)

## Casos de Uso

- Analisar os dados de negócios possibilitando *insights* para tomadas de decisão.
- Análise de logs de aplicação e infraestrutura para *troubleshooting*.
- Análises de segurança dos dados.